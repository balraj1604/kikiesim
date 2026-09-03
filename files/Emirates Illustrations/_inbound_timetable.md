# Emirates Passenger Network Timetable — INBOUND to Dubai (DXB)

Source: emirates.com Flight Schedules service (POST /service/flight-schedules, origin=<city>, destination=DXB, date 20260623, non-stop EK-operated services only). Captured via authenticated browser session, same-origin JSON service. Representative service = earliest daytime departure where available, else first non-stop. Times: CITY_DEP = origin city local, DXB_ARR = Dubai local (+1 = next-day arrival). Day-part buckets: early-morning 04:00-06:59 | morning 07:00-11:59 | afternoon 12:00-16:59 | evening 17:00-20:59 | night 21:00-03:59.

Total destinations: 124

## Machine-readable (pipe-delimited)
`REGION | INBOUND_FLIGHT | ORIGIN_CITY | IATA | CITY_DEP | DXB_ARR | DEP_BUCKET | ARR_BUCKET`

```
Europe | EK146 | Amsterdam | AMS | 11:25 | 20:45 | afternoon | evening
Europe | EK210 | Athens | ATH | 18:05 | 23:59 | evening | night
Europe | EK256 | Barcelona | BCN | 15:40 | 00:30 (+1) | afternoon | night
Europe | EK40 | Birmingham | BHX | 14:35 | 01:20 (+1) | afternoon | night
Europe | EK94 | Bologna | BLQ | 15:35 | 23:35 | afternoon | night
Europe | EK184 | Brussels | BRU | 15:20 | 00:35 (+1) | afternoon | night
Europe | EK112 | Budapest | BUD | 16:05 | 00:15 (+1) | afternoon | night
Europe | EK152 | Copenhagen | CPH | 15:15 | 00:30 (+1) | afternoon | night
Europe | EK162 | Dublin | DUB | 14:20 | 01:20 (+1) | afternoon | night
Europe | EK56 | Düsseldorf | DUS | 15:25 | 00:35 (+1) | afternoon | night
Europe | EK24 | Edinburgh | EDI | 22:00 | 08:55 (+1) | night | morning
Europe | EK44 | Frankfurt am Main | FRA | 11:00 | 19:55 | morning | evening
Europe | EK90 | Geneva | GVA | 15:15 | 23:55 | afternoon | night
Europe | EK28 | Glasgow | GLA | 14:40 | 01:45 (+1) | afternoon | night
Europe | EK60 | Hamburg | HAM | 15:30 | 00:40 (+1) | afternoon | night
Europe | EK124 | Istanbul | IST | 16:25 | 22:25 | afternoon | night
Europe | EK110 | Larnaca | LCA | 20:25 | 01:40 (+1) | evening | night
Europe | EK192 | Lisbon | LIS | 14:20 | 01:15 (+1) | afternoon | night
Europe | EK12 | London | LGW | 10:05 | 20:40 | morning | evening
Europe | EK8 | London | LHR | 09:05 | 19:40 | morning | evening
Europe | EK66 | London | STN | 14:55 | 01:30 (+1) | afternoon | night
Europe | EK82 | Lyon | LYS | 15:40 | 23:59 | afternoon | night
Europe | EK142 | Madrid | MAD | 15:25 | 00:45 (+1) | afternoon | night
Europe | EK22 | Manchester | MAN | 09:50 | 20:40 | morning | evening
Europe | EK206 | Milan | MXP | 14:15 | 22:45 | afternoon | night
Europe | EK134 | Moscow | DME | 16:50 | 01:05 (+1) | afternoon | night
Europe | EK50 | Munich | MUC | 15:40 | 00:15 (+1) | afternoon | night
Europe | EK36 | Newcastle | NCL | 14:15 | 01:05 (+1) | afternoon | night
Europe | EK78 | Nice | NCE | 15:50 | 00:20 (+1) | afternoon | night
Europe | EK160 | Oslo | OSL | 15:20 | 01:05 (+1) | afternoon | night
Europe | EK72 | Paris | CDG | 11:20 | 20:35 | morning | evening
Europe | EK140 | Prague | PRG | 16:10 | 00:45 (+1) | afternoon | night
Europe | EK98 | Rome | FCO | 15:45 | 23:45 | afternoon | night
Europe | EK176 | St. Petersburg | LED | 23:05 | 08:10 (+1) | night | morning
Europe | EK158 | Stockholm | ARN | 15:35 | 01:10 (+1) | afternoon | night
Europe | EK136 | Venice | VCE | 15:35 | 23:55 | afternoon | night
Europe | EK128 | Vienna | VIE | 15:35 | 23:50 | afternoon | night
Europe | EK180 | Warsaw | WAW | 15:10 | 23:45 | afternoon | night
Europe | EK88 | Zürich | ZRH | 15:30 | 00:15 (+1) | afternoon | night
Americas | EK238 | Boston | BOS | 23:05 | 20:00 (+1) | night | evening
Americas | EK236 | Chicago | ORD | 20:35 | 19:45 (+1) | evening | evening
Americas | EK222 | Dallas | DFW | 12:15 | 12:55 (+1) | afternoon | afternoon
Americas | EK212 | Houston | IAH | 19:35 | 20:10 (+1) | evening | evening
Americas | EK216 | Los Angeles | LAX | 16:40 | 20:25 (+1) | afternoon | evening
Americas | EK214 | Miami | MIA | 23:55 | 22:40 (+1) | night | night
Americas | EK244 | Montréal | YUL | 10:15 | 07:00 (+1) | morning | morning
Americas | EK204 | New York | JFK | 11:20 | 08:30 (+1) | morning | morning
Americas | EK220 | Orlando | MCO | 20:50 | 19:35 (+1) | evening | evening
Americas | EK248 | Rio de Janeiro | GIG | 03:05 | 00:35 (+1) | night | night
Americas | EK226 | San Francisco | SFO | 17:05 | 20:30 (+1) | evening | evening
Americas | EK230 | Seattle | SEA | 17:15 | 19:40 (+1) | evening | evening
Americas | EK262 | São Paulo | GRU | 01:05 | 23:05 | night | night
Americas | EK242 | Toronto | YYZ | 14:55 | 12:30 (+1) | afternoon | afternoon
Americas | EK232 | Washington, D.C. | IAD | 10:55 | 08:30 (+1) | morning | morning
Far East & Australasia | EK441 | Adelaide | ADL | 22:00 | 05:40 (+1) | night | early-morning
Far East & Australasia | EK449 | Auckland | AKL | 20:30 | 05:35 (+1) | evening | early-morning
Far East & Australasia | EK399 | Bali | DPS | 00:35 | 05:35 | night | early-morning
Far East & Australasia | EK371 | Bangkok | BKK | 03:40 | 06:50 | night | early-morning
Far East & Australasia | EK307 | Beijing | PEK | 00:40 | 05:00 | night | early-morning
Far East & Australasia | EK435 | Brisbane | BNE | 21:00 | 05:20 (+1) | evening | early-morning
Far East & Australasia | EK338 | Cebu | CEB | 17:55 | 01:15 (+1) | evening | night | UNCERTAIN
Far East & Australasia | EK363 | Guangzhou | CAN | 00:20 | 04:00 | night | early-morning
Far East & Australasia | EK311 | Hangzhou | HGH | 00:10 | 04:30 | night | early-morning
Far East & Australasia | EK395 | Hanoi | HAN | 01:30 | 05:05 | night | early-morning
Far East & Australasia | EK393 | Ho Chi Minh City | SGN | 23:50 | 03:45 (+1) | night | night
Far East & Australasia | EK383 | Hong Kong | HKG | 19:10 | 23:00 | evening | night
Far East & Australasia | EK357 | Jakarta | CGK | 17:40 | 22:30 | evening | night
Far East & Australasia | EK345 | Kuala Lumpur | KUL | 09:20 | 12:10 | morning | afternoon
Far East & Australasia | EK337 | Manila | MNL | 07:45 | 12:15 | morning | afternoon
Far East & Australasia | EK409 | Melbourne | MEL | 05:15 | 13:05 | early-morning | afternoon
Far East & Australasia | EK317 | Osaka | KIX | 23:45 | 04:35 (+1) | night | early-morning
Far East & Australasia | EK421 | Perth | PER | 22:20 | 05:15 (+1) | night | early-morning
Far East & Australasia | EK379 | Phuket | HKT | 19:55 | 23:00 | evening | night
Far East & Australasia | EK323 | Seoul | ICN | 23:55 | 04:25 (+1) | night | early-morning
Far East & Australasia | EK305 | Shanghai | PVG | 07:20 | 12:00 | morning | afternoon
Far East & Australasia | EK329 | Shenzhen | SZX | 00:45 | 04:20 | night | early-morning
Far East & Australasia | EK315 | Singapore | SIN | 10:35 | 13:45 | morning | afternoon
Far East & Australasia | EK415 | Sydney | SYD | 06:00 | 14:10 | early-morning | afternoon
Far East & Australasia | EK387 | Taipei | TPE | 00:30 | 05:15 | night | early-morning
Far East & Australasia | EK313 | Tokyo | HND | 00:05 | 05:40 | night | early-morning
Far East & Australasia | EK319 | Tokyo | NRT | 22:30 | 04:05 (+1) | night | early-morning
West Asia & Indian Ocean | EK539 | Ahmedabad | AMD | 04:40 | 06:10 | early-morning | early-morning
West Asia & Indian Ocean | EK565 | Bengaluru (Bangalore) | BLR | 10:30 | 12:45 | morning | afternoon
West Asia & Indian Ocean | EK545 | Chennai (Madras) | MAA | 09:50 | 12:20 | morning | afternoon
West Asia & Indian Ocean | EK651 | Colombo | CMB | 10:05 | 12:55 | morning | afternoon
West Asia & Indian Ocean | EK583 | Dhaka | DAC | 10:10 | 13:00 | morning | afternoon
West Asia & Indian Ocean | EK527 | Hyderabad | HYD | 10:15 | 12:25 | morning | afternoon
West Asia & Indian Ocean | EK613 | Islamabad | ISB | 09:25 | 11:35 | morning | morning
West Asia & Indian Ocean | EK601 | Karachi | KHI | 12:15 | 13:20 | afternoon | afternoon
West Asia & Indian Ocean | EK603 | Karachi | KHI | 22:55 | 00:05 (+1) | night | night
West Asia & Indian Ocean | EK531 | Kochi (Cochin) | COK | 10:35 | 12:55 | morning | afternoon
West Asia & Indian Ocean | EK571 | Kolkata (Calcutta) | CCU | 09:50 | 13:00 | morning | afternoon
West Asia & Indian Ocean | EK625 | Lahore | LHE | 09:10 | 11:25 | morning | morning
West Asia & Indian Ocean | EK706 | Mahe | SEZ | 08:25 | 12:55 | morning | afternoon
West Asia & Indian Ocean | EK657 | Malé | MLE | 09:15 | 12:15 | morning | afternoon
West Asia & Indian Ocean | EK505 | Mumbai (Bombay) | BOM | 10:15 | 11:45 | morning | morning
West Asia & Indian Ocean | EK511 | New Delhi | DEL | 11:00 | 13:00 | morning | afternoon
West Asia & Indian Ocean | EK619 | Sialkot | SKT | 02:40 | 04:55 | night | early-morning
West Asia & Indian Ocean | EK523 | Thiruvananthapuram (Trivandrum) | TRV | 04:45 | 07:15 | early-morning | morning
Gulf & Middle East | EK904 | Amman | AMM | 18:15 | 23:00 | evening | night
Gulf & Middle East | EK838 | Bahrain | BAH | 10:20 | 12:35 | morning | afternoon
Gulf & Middle East | EK958 | Beirut | BEY | 13:30 | 18:30 | afternoon | evening
Gulf & Middle East | EK828 | Dammam | DMM | 09:30 | 11:55 | morning | morning
Gulf & Middle East | EK806 | Jeddah | JED | 10:45 | 14:40 | morning | afternoon
Gulf & Middle East | EK858 | Kuwait City | KWI | 17:40 | 20:25 | evening | evening
Gulf & Middle East | EK810 | Medina (Madinah) | MED | 17:35 | 21:15 | evening | night
Gulf & Middle East | EK867 | Muscat | MCT | 04:40 | 05:55 | early-morning | early-morning
Gulf & Middle East | EK820 | Riyadh | RUH | 09:40 | 12:50 | morning | afternoon
Africa | EK788 | Accra | ACC | 18:00 | 06:15 (+1) | evening | early-morning
Africa | EK724 | Addis Ababa | ADD | 16:00 | 21:15 | afternoon | night
Africa | EK928 | Cairo | CAI | 13:10 | 17:30 | afternoon | evening
Africa | EK773 | Cape Town | CPT | 13:15 | 00:35 (+1) | afternoon | night
Africa | EK752 | Casablanca | CMN | 14:40 | 01:30 (+1) | afternoon | night
Africa | EK795 | Conakry | CKY | 14:45 | 07:40 (+1) | afternoon | morning | UNCERTAIN
Africa | EK726 | Dar Es Salaam | DAR | 15:25 | 21:50 | afternoon | night
Africa | EK776 | Durban | DUR | 18:40 | 05:00 (+1) | evening | early-morning
Africa | EK730 | Entebbe | EBB | 16:35 | 23:00 | afternoon | night
Africa | EK762 | Johannesburg | JNB | 13:30 | 23:40 | afternoon | night
Africa | EK784 | Lagos | LOS | 17:40 | 04:45 (+1) | evening | early-morning
Africa | EK794 | Luanda | NBJ | 18:25 | 05:15 (+1) | evening | early-morning
Africa | EK714 | Lusaka | LUN | 21:35 | 06:30 (+1) | night | early-morning
Africa | EK702 | Mauritius | MRU | 16:15 | 22:50 | afternoon | night
Africa | EK720 | Nairobi | NBO | 16:35 | 22:40 | afternoon | night
Africa | EK748 | Tunis | TUN | 13:55 | 22:55 | afternoon | night
```
