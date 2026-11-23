# X3TC Custom Menu — Two-column formatting research

## Scope
Research target: X3: Terran Conflict (TC), custom-script menus. This document records verified information relevant to implementing two-column menu rows in MARS without modifying the working configuration yet.

## Verified command

MSCI command:

`<RetVar> = create text for custom menu, left=<Var/String1>, right=<Var/String2>`

The command formats two text values into one menu row:
- `left`: text positioned toward the left edge.
- `right`: text positioned toward the right edge.
- result: formatted string returned into a variable, which can then be added to a menu as a regular menu item or information line.

This is not merely manual spacing: the command explicitly formats left/right fields in a single row.

## Menu construction context
Custom menus are built into an array using commands such as:
- `create custom menu array`
- `add custom menu heading to array`
- `add custom menu info line to array`
- `add custom menu item to array`
- `add section to custom menu`
- `open custom menu`

## Sources
1. Russian MSCI reference page, “Прочее / X3 Terran Conflict”: https://x3tc.net/prochee_125.html — describes the command and its left/right alignment behavior.
2. Elite Games forum discussion of External Script Editor custom command definitions, including command ID 1523 and type layout: https://www.elite-games.ru/conference/viewtopic.php?sid=91114acdca46991619f8f2ce941f3f11&start=80&t=47152 — corroborates the command signature in external editor configuration. The ID is editor metadata, not a new in-game script identifier.

## What is not verified yet
- Whether the formatting command is available in the user's exact X-Studio setup without importing command definitions.
- Maximum text length and behavior when either side is long.
- Whether the formatted output should be used as an info line, selectable item text, or both for the desired layout.
- Exact spacing/column widths, font-width behavior, and color formatting interactions.
- In-game rendering in TC 3.4 has not yet been tested.

## Next practical test
Create a small isolated test script using the verified command to generate a row with short left text and a short right value (e.g. label/value), place the result in a custom menu array, and open the menu. Test short, long, empty-right, and empty-left cases in-game. Only after this is validated should this formatting be applied to MARS menus.


## Additional verified mechanism: formatted-text arrays (patch 2.5+)

The Egosoft Community Wiki menu tutorial indexed as “Creating beautiful menus in X3: Terran Conflict” reports that, from patch 2.5, any menu command expecting text can also accept an array structured as:

`ARRAY('PosCol1', 'text1', 'PosCol2', 'text2', ...)`

The tutorial describes each `PosColN` as an integer column position: `1` places a column at the left side and `-1` at the right side. This permits multi-column text formatting in a menu text field. This is a flexible route beyond the dedicated left/right formatting command.

**Caution:** The wiki search-index excerpt provides this format and positional explanation, but the full tutorial page could not be opened in this session. The format is source-supported but not yet independently validated in a TC 3.4 in-game test.

## Test matrix (not yet executed in game)

| Case | Left column | Right column | Purpose |
|---|---|---|---|
| A | Short label | ON | Basic two-column alignment |
| B | Long label | ON | Check left-side width/overlap |
| C | Short label | Long value | Check right-side width/overlap |
| D | Short label | Empty string | Empty right column behavior |
| E | Empty string | ON | Empty left column behavior |
| F | Two rows with different values | Compare alignment stability |

## Research conclusions

- **Source-confirmed:** Dedicated command 1523 formats left and right strings into one menu text row; command definition lists three string-type slots (return string, left string, right string).
- **Wiki indexed text:** Since patch 2.5, text-consuming menu commands accept positional formatted-text arrays; `1` means left and `-1` means right.
- **Not tested in game:** Exact display in TC 3.4/X-Studio, column widths, long-text behavior, color markup interaction, and compatibility of each menu text slot.
- **Next step:** Test the array formatting mechanism in a separate minimal menu, then compare with command 1523. Do not alter MARS menu code until rendering is confirmed.

## Additional source
3. Egosoft Community Wiki tutorial, “Creating beautiful menus in X3: Terran Conflict” (indexed text and attachment content): https://wiki.egosoft.com/X3%20Wiki/02.%20X3%3A%20Terran%20Conflict/Scripts%20and%20Modding/Tutorials/Creating%20beautiful%20menus%20in%20X3%3A%20Terran%20Conflict/
