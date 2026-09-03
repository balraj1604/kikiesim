# Emirates Wallpaper Runner — Ledger

> Source-of-truth note for the autonomous wallpaper-generation system. ANY SESSION: read this first whenever Balraj asks about the Emirates wallpaper runner / illustration generation / "the download". Always verify live numbers with the status command below before asserting.

---

## 🟢 HOW BALRAJ ASKS (copy-paste prompts)

**To check status (and pull new files into the vault):**
> "Status of the Emirates wallpaper download. Read `Emirates Illustrations/_WALLPAPER_RUNNER_LEDGER.md`, run the donguri status command, tell me done/pending, then pull any new full-res files into my vault."

**To get full context on this system:**
> "Give me context on the Emirates wallpaper runner — read its ledger note and the memory `reference-donguri-wallpaper-runner`."

**To add more wallpapers to the queue:**
> "Add more tasks to the Emirates wallpaper download: [describe what — new base illustrations, or a new ratio]."

(See "ADD MORE TASKS" section below for what the session then does.)

---

## WHAT IT IS
Autonomous job generating **wallpaper-ratio (9:16 phone, 16:9 desktop, 1:1 square) copies of the 248 frozen Emirates flight-attendant base illustrations** = **744 targets**. Bases stay untouched. "Banana Coder" = headless Gemini (Pro) driven via Playwright MCP, one reused browser session.

## WHERE IT RUNS
Entirely on **donguri** (the always-on Mac mini), independent of any Claude chat. **Closing a session does NOT stop it.** m16 can be off.
- launchd service: `com.balraj.emirates-wallpapers` (RunAtLoad + KeepAlive; survives reboot)
- Working dir: `donguri:~/emirates-wp/`
- Outputs: `~/emirates-wp/illustrations/Wallpaper/<ratio>/<Outbound|Inbound>/<region>/WP_<origname>.png`
- Auth: `chrome-profile/` signed into **balrajsinghkalra@gmail.com (Pro)**, default `gemini.google.com/app`

## CHECK STATUS (run this, don't guess)
```
ssh donguri 'cd ~/emirates-wp && ./gen-worklist.sh >/dev/null 2>&1; echo "done: $((744-$(wc -l < worklist.tsv)))/744"; ls CAP DONE 2>/dev/null; pgrep -fl "emirates-wp/chrome-profile" >/dev/null && echo running || echo idle; tail -n 4 run.log'
```

## SYNC TO VAULT — IMPORTANT (how files reach the Mac)
Files are generated on **donguri** and must be pulled to the vault at:
```
/Users/a44/Documents/dojo/dojo/Emirates Illustrations/Wallpaper/
```
- Mechanism: **one-way rsync, donguri → m16, NO `--delete`, additive, Wallpaper-folder ONLY.** This is NOT Syncthing (the thing that caused past duplicate-folder messes) — it can only ADD/UPDATE wallpaper PNGs, never delete or touch anything else. Script: `m16:/Users/a44/code/emirates-wp/pull-wallpapers.sh`.
- **⚠️ macOS TCC gotcha:** the launchd timer (`com.balraj.emirates-wp-pull`, every 900s) is **blocked from writing into `~/Documents`** ("Operation not permitted") — same limitation hits kiki-pull. So the timer alone does NOT reliably sync.
- **RELIABLE path: a SESSION runs the pull.** When Balraj asks status/completion, the session runs the script directly (session context is allowed into Documents):
  ```
  /Users/a44/code/emirates-wp/pull-wallpapers.sh
  ```
  That's why the status prompt above says "then pull new files into my vault" — checking status and syncing are the same action.
- To make the timer work hands-off later: grant **Full Disk Access** to `/usr/bin/rsync` (or `/bin/bash`) in System Settings → Privacy & Security → Full Disk Access (one-time GUI click — only Balraj can do it).

## ADD MORE TASKS
The queue (`gen-worklist.sh`) = every base PNG in `donguri:~/emirates-wp/illustrations/{Outbound,Inbound}/**` × the 3 ratios, skipping any output that already exists (idempotent).
- **Add new illustrations:** copy the new base PNG(s) into `donguri:~/emirates-wp/illustrations/Outbound/<region>/` (or `Inbound/`). They auto-appear as 3 new jobs (one per ratio) on the next loop — no code change.
- **Add a new ratio:** edit the `for ratio in 9x16 16x9 1x1` line in `donguri:~/emirates-wp/gen-worklist.sh` and add the ratio + a matching `<RECOMPOSE>` line in `worker_prompt.md`.
- After adding, the running loop picks them up automatically; nothing to restart.

## QUALITY GUARD (low-res)
Early batches saved full **1536×2602**; the worker sometimes fell back to a downscaled **968px** preview. Two guards now:
1. `worker_prompt.md` requires the full-size download and rejects anything <1400px.
2. **Deterministic sweep in `run-loop.sh`** — every loop it hard-deletes any wallpaper with longest side <1400px, which re-queues it for a full-size regen. (The prompt alone wasn't reliable; the sweep is the real fix.)

## BEHAVIOR
- Queue order: all 9:16, then 16:9, then 1:1.
- Cap: on quota/limit/base-echo the worker writes `CAP`; loop sleeps ~2h45m, auto-resumes. Kiki WhatsApps Balraj on cap windows + completion.
- Per-batch timeout 1800s (perl SIGALRM). Killed batches keep saved images (idempotent).
- **Safety:** chromium cleanup SCOPED to `pkill -f "emirates-wp/chrome-profile"` ONLY. NEVER broad `pkill`, NEVER touch Kiki or KAMAJI.

## MANAGE
- stop generation: `ssh donguri 'launchctl unload ~/Library/LaunchAgents/com.balraj.emirates-wallpapers.plist'`
- start generation: `ssh donguri 'launchctl load ~/Library/LaunchAgents/com.balraj.emirates-wallpapers.plist'`
- auth recovery recipe: memory `reference-donguri-wallpaper-runner`

## PROGRESS LOG
- 2026-06-25 — runner re-authed, generating; resolution-guard issues found.
- 2026-06-28 13:00 — **570/744 done** (9:16 ✅ 248, 16:9 ✅ 248, 1:1 = 74). CAP hit 10:07 (quota), auto-sleeping. Deployed: deterministic low-res sweep in run-loop + 1400px guard in worker. Cleared 43 low-res (re-queued → pending 217). Built m16 Wallpaper puller + seeded vault (session-run, since launchd is TCC-blocked).

## RELATED
- Base series 248/248 complete: memory `project-emirates-illustrations`.
- Runner internals + auth recovery: memory `reference-donguri-wallpaper-runner`.
