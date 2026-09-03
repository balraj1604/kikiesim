# Banana Coder — INBOUND (city → Dubai) Illustration Spec

Crew flying HOME to Dubai. Same engine as the outbound spec but reversed, with a story layer.
Generate ONE image per route in Gemini ("Create image" / Nano Banana 2), account
**balrajsinghkalra@gmail.com** (/u/1/ tab — verify active first), image-to-image. Then crop + save.

## Frozen coming-home lady (HARD GATE)
Always upload this exact reference every time (never a derivative):
`/Users/a44/Pictures/screenshot/2026-06-22_23-28-57.png`
Keep her EXACT identity, outfit, NATURAL proportions, the calm coming-home standing pose (back view,
both feet planted, body turned toward the Dubai side on the RIGHT through the glass, one hand resting
on the upright black suitcase, white scarf streaming to the LEFT), red pillbox hat, camel/tan belted
coat, deep-red skirt, red heels. Crisp clean FLAT-VECTOR taste (flat fills, soft cel-shading, clean
linework, light paper texture — NOT soft/3D/volumetric, NOT elongated). Repaint only the two city
backgrounds and add the per-city story element. **After each gen, compare to the reference; if she is
softened/3D/restyled/re-proportioned, REJECT and regenerate (up to 2 tries). Save only a PASS.**
EXCEPTION: when the per-city element specifies an accessory swap (e.g. cowboy hat replacing the
pillbox), that swap is intended — keep everything else identical.

## Composition (every inbound image)
- LEFT = the ORIGIN city at its DEPARTURE time-of-day (characterful cultural vignette, not a skyline).
- RIGHT, THROUGH the glass terminal window = DUBAI at the ARRIVAL-INTO-DUBAI time-of-day.
- Small plane + faint contrail in the RIGHT side of the sky (flying toward Dubai / toward the right).
- Portrait 3:4, flat-vector, light paper texture, no heavy grain. NO text/letters/labels anywhere
  (the suitcase sticker is a tiny GRAPHIC, never a word-label — unless a logo naturally has letters,
  keep it tiny/subtle).

## Day-part vocabulary (same buckets as outbound)
DUBAI side by ARR bucket: early-morning = pre-dawn indigo→rose, still; morning = soft warm light;
afternoon = golden hot desert, palms, bright; evening = warm dusk orange→violet, lights starting;
night = deep navy, crescent moon, warm city lights + one subtle slim tower.
ORIGIN side by DEP bucket: same lighting logic applied to that city's scene.

## Story element (per city) — from `_INBOUND_ELEMENTS.md`
Each route has: a SUBTLE small sticker/charm on the black suitcase, and OPTIONALLY an accessory
(e.g. Thai anklet, Texas cowboy hat). Read the element line for the city from `_INBOUND_ELEMENTS.md`
and apply it subtly and tastefully.

## Per-route Gemini prompt template (fill [...] then send)
"Edit this illustration. Keep the woman EXACTLY as in the reference — same identity, outfit, the calm
standing coming-home pose (back view, both feet planted, body turned right toward the glass, hand on
the upright black suitcase, white scarf streaming left), and the crisp clean FLAT-VECTOR art style.
[IF accessory swap: apply this change to her and nothing else: <accessory>.]
Repaint ONLY the two backgrounds: (1) LEFT = [ORIGIN CITY] at [DEP bucket] — [characterful scene].
(2) RIGHT through the glass window = DUBAI at [ARR bucket] — [Dubai scene]. Put the small plane +
contrail in the RIGHT side of the sky. Add a subtle small [sticker/charm] on her black suitcase.
Keep the plane(s) PLAIN/unbranded — do NOT add Emirates wordmark or livery (Gemini's filter refuses
trademarks and stalls). No text or labels anywhere. Portrait 3:4, premium clean flat-vector design."

NOTE (filter-safe phrasing): frame as "use the uploaded image as a STYLE/COMPOSITION reference, keep
the same stylized illustrated traveler, repaint only the scenery" — NOT "do not change the person /
pixel-for-pixel", which Gemini refuses.

## Save + de-watermark (per route)
1. Extract the result (canvas-draw the live <img> if blob revoked) to a temp raw PNG.
2. Crop the bottom-right Gemini watermark PROPORTIONALLY to output height, save FINAL to
   `/Users/a44/Documents/dojo/dojo/Emirates Illustrations/Inbound/<REGION>/IN_<FLIGHT>_<City>-<IATA>.png`
   (sanitize City: spaces→hyphens, drop parentheses/periods/accents). Python:
   `python3 -c "from PIL import Image;im=Image.open('SRC');w,h=im.size;c=round(h*56/1024);im.crop((0,0,w,h-c)).save('DST')"`
3. Idempotent: if `IN_*_<IATA>.png` already exists in the Inbound region folder, SKIP that route.

## Image model (MUST be PRO)
In the Gemini image tool, select the **PRO image model — "Nano Banana Pro" (Gemini 3 Pro Image)**, NOT
the standard "Nano Banana 2". Pick the Pro option in the "Create image" model/quality selector. The
account must be Gemini Pro-tier. If only standard is available with no Pro option, STOP and report.

## Browser handling
`mcp__playwright__browser_tabs list` first. If locked by an orphaned Playwright Chrome, gracefully
`pkill -TERM` ONLY that orphaned process (never touch Kiki on donguri or ~/.telegram-web-profile).
Work ALONE, single reused session. If an image daily-limit message appears, STOP and report how many
completed (we resume next reset).

## Report
Per route: ✅ saved path / ⏭️ skipped / ❌ failed (reason) + crew-gate tries. End with done/skipped/failed.
