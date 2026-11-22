# Verified MARS configuration meanings

## Sources and method
- XML: plugin.gz.mars.config_modified(1).xml, local copy. XML parsing succeeded.
- Language text: 7046-L007.xml, language ID 7, local copy.
- Cross-checks: menu text IDs, comments, handlers that write values, and numeric clamps/cycles.
- Findings describe this script build only; do not assume the indexes remain stable across MARS versions.

## Mappings confirmed in code/text

| Config | Meaning supported by source | Values / bounds visible in code | Evidence |
|---:|---|---|---|
| 93 | Defender collection of contraband | Toggle; text IDs 2405/2408 for on/off | Lines 807–812; language ID 2653 |
| 188 | Defender collection of cargo incompatible with ship | Toggle | Lines 814–819; ID 2654 |
| 189 | Stop collection when enemy detected within range | Numeric 0–200; label specifies km | Lines 821–826, 1824–1834; ID 2655 |
| 94 | Collect only compatible ammunition/missiles | Toggle | Lines 832–838; ID 2656 |
| 95 | Collect unguided missiles | Toggle | Lines 840–845; ID 2657 |
| 96 | Goblins on M-class ships: collection only according to Supply settings | Toggle; enabling also clears Config[94] and sets Config[95] TRUE | Lines 848–857 |
| 107 | Cargo auto-collection when ship moves | Toggle | Lines 859–865; ID 2658 |
| 106 | Defender repair feature | Toggle | Lines 882–887; ID 2659 |
| 173 | Cargo Collect task cargo/free-space display mode | null → 1 → 2 → null; comment: 1 on, 2 on without colors | Lines 867–880, 1963–1971 |
| 116 | Do not use flak weapons | Toggle | Lines 934–939; ID 2666 |
| 108 | Detect hidden mines | Toggle | Lines 941–946; ID 2667 |
| 88 | Monitor marine vital signs | null/off, 1 and 2 display different states; exact distinction requires missing language texts 2506/2507 | Lines 948–965; ID 2668 |
| 115 | Detect laser-defined damage zone | Toggle | Lines 981–987; ID 2669 |
| 179 | Manual turret control | Toggle | Lines 989–994; ID 2670 |
| 86 | MARS availability for enemy capital ships | States 1, 2, or null. Menu comments/text refer to one enemy ship and all AI cap ships; complete mapping needs missing menu texts | Lines 1013–1038, 1874–1899 |
| 87 | MARS logo mode | null → 1 → 2 → null; exact meanings depend on missing texts 2462/2463/2465 | Lines 1050–1065, 1853–1868 |
| 18 | Neutral-station avoidance setting | Cycle 0–3; exact labels not available in provided language file | Lines 996–1009, 1981–1986 |
| 44 | Area-laser exclusion threshold in defense mode, based on shield percentage | Numeric clamp -10 to 110 | Lines 892–898, 2046–2049; ID 2660/2662 |
| 45 | Area-laser exclusion threshold in attack mode, based on shield percentage | Numeric clamp -10 to 110 | Lines 892–901, 2051–2054; ID 2661/2662 |
| 178 | Energy management: normal percentage setting | Input clamp -1000 to 1000 | Lines 908–911, 1990–2001 |
| 184 | Energy management: low-energy activation percentage | Clamp 0–100 | Lines 913–916, 2003–2014; ID 2663 |
| 185 | Energy management: low-energy setting value | Clamp -1000 to 1000 | Lines 918–923, 2016–2027; ID 2664 |
| 190 | Observe assigned target sizes below energy percentage | Clamp 0–95 | Lines 925–932, 2029–2040; ID 2665 |
| 97 | Performance menu setting described in code as target-acquisition wait after X targets | Cycle 0 → 5 → 10 → 25 → 0 | Lines 1161–1172, 2084–2095 |
| 98 | Performance setting comment: target changing / salvo length; exact semantic meaning remains ambiguous | Cycle 0 → 1 → 2 → 4 → 0 | Lines 1174–1185, 2097–2108 |
| 99 | Goblin control setting (exact effect not established) | Cycle 0 → 800 → 1600 → 3000 → 0 | Lines 1187–1198, 2110–2121 |
| 100 | Goblin control setting (exact effect not established) | Cycle 0 → 400 → 800 → 1500 → 0 | Lines 1200–1211, 2123–2137 |
| 101 | Auxiliary flag used together with Config[100] | Set to 0/1 in the Config[100] cycle; independent meaning unknown | Lines 2123–2137 |
| 181 | Numeric performance setting; label is not present in supplied language XML | Input clamp 10–100; menu display uses value / 6, minimum display result 2 | Lines 1213–1217, 2139–2150 |
| 175 | Goblin swarm menu parameter (exact meaning not established) | Numeric input clamp 0–2000; display calculation 1000/value | Lines 786–805, 1805–1814 |

## Aliases confirmed at the top of the script

| Config index | Variable alias |
|---:|---|
| 129 | VarName.Attack.Shields |
| 130 | VarName.Ignore |
| 131 | VarName.Neutral.Station |
| 127 | VarName.Is.Goblin |
| 132 | VarName.Gob.Missile.Def |
| 118 | VarName.MARS.Mode |
| 159 | VarName.Recover.Ships |

## Other array/context uses observed

| Config | Context visible in source | Meaning status |
|---:|---|---|
| 4 | Lasers.Main.Arr | Variable purpose confirmed |
| 117 | Statistics.Laser.Use.Arr | Variable purpose confirmed |
| 182 | Laser.Ban.Shiptype.Arr | Alias name provides context |
| 183 | Laser.Ban.Laser.Arr | Alias name provides context |
| 58 | Array used to count Goblin Mk1/Mk2 cargo | Exact config meaning unknown |
| 60 | Value used as ware to count Advanced Satellites in cargo | Usage known; config purpose unknown |
| 192 | Displayed in menu as TFile/config-file information | Full meaning unknown |

## Still unknown / require additional sources
The exact purpose or valid values for several indexes are not established by this XML and language excerpt. Missing referenced menu texts include IDs 2404–2408, 2462–2465, 2490–2492, 2506–2508, and 2570–2576. Obtain the matching full MARS text file or other script sources before assigning names based on guesswork.

## Conclusion
Changing a setting safely requires its index, the code that handles its menu result, allowed values/range, and the effect. This file provides evidence for several settings but is not a universal MARS configuration specification.
