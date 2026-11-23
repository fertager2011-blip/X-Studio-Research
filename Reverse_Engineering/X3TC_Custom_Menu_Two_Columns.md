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
