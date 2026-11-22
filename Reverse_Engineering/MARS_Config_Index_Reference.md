# MARS Config index reference

## Corrected extraction counts
- Source: local XML plugin.gz.mars.config_modified(1).xml.
- sourcetext contains 2246 line elements.
- Exact XML itertext extraction found 56 unique numeric Config indexes.
- Total 171 numeric references including 3 comment-only references; 168 code references.
- The earlier table had line-number/classification mistakes; use the updated verified mapping in [Verified MARS Config meanings](MARS_Config_Verified_Meanings.md).

## Numeric indexes found (56)
0, 1, 2, 4, 18, 29, 37, 44, 45, 54, 55, 57, 58, 60, 84, 85, 86, 87, 88, 90, 93, 94, 95, 96, 97, 98, 99, 100, 101, 106, 107, 108, 115, 116, 117, 118, 127, 129, 130, 131, 132, 159, 170, 173, 175, 178, 179, 181, 182, 183, 184, 185, 188, 189, 190, 192.

## Verified aliases at lines 21–27
| Config index | Alias |
|---:|---|
| 129 | VarName.Attack.Shields |
| 130 | VarName.Ignore |
| 131 | VarName.Neutral.Station |
| 127 | VarName.Is.Goblin |
| 132 | VarName.Gob.Missile.Def |
| 118 | VarName.MARS.Mode |
| 159 | VarName.Recover.Ships |

## Reading rules
Config[n] identifies an array slot; it is not the stored value. Don't change indexes until the index is understood. Some slots contain arrays rather than scalar settings. Verify a setting by examining reads, writes, menu-return handling, comments, and localized menu text. See the verified mapping document for the findings from this sample.
