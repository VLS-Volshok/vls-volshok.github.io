# Player & Team Colors
Player and teams colors are automatically assigned, dependent on the game mode. This is done intentionally to provide a clear visual distinction. 

In multiplayer games, colors are assigned by descending Openskill value. A player cannot pick a specific color to play as, it's dictated by team number.

## Color Palettes
-   There are different predefined palettes (`ffaColors`, `survivalColors`, `teamColors`) for all game modes.
 -   Special colors are assigned for AI factions like _Scavenger_ and _Raptor_, as well as neutral factions

### Automatic Color Generation
Teams in BAR will have a main color, or a "theme" color. BAR generates slight variations to a team's main color to make them visually distinct and avoid repetitive colors while not having drastic changes that would make colors unrecognizable. This variation is achieved by randomly modifying the RGB values of each "main" color, then converting it back to Hex.

Process is
-   `hex2RGB(hex)` converts a color's hex code into an RGB triplet (Red, Green, Blue) that ranges from 0 to 255.
-   A random value is added to each RGB component (Red, Green, Blue), defined as: `math.random(-variation, variation).`variation` is the delta value.
- Level of variation is controlled by `colorVariationDelta` (default is 128). It increases over each cycle to maintain uniqueness incase the color palette gets weird.
-   If all available colors are exhausted it resets to the first color and the variation amplitude increases, making new colors more distinct.
-   
### AI Faction Defined Colors
| Hex Code  | Special Color  |
|-----------|-------------|
| #004DFF   | Armada Blue |
| #FF1005   | Cortex Red |
| #6809A1   | Scav Purple |
| #CC8914   | Raptor Orange |
| #7F7F7F   | Gaia Grey    |
| #0CE818   | Legion Green |
 
### Alternative Modes
These are alternate modes where player/team colors are randomized, obscured, or standardized to alter identify/visibility.
- **Disco Mode** `disco`: Randomizes team colors periodically (every 2 minutes), using`shuffleAllColors`
- **All Red** `allred`: Yeah everyone is red. 
- **Anonymous** `local`:  Each player is given local random colors for all other players so there isn't uniform coloring. For example, Player 1 will see Player 2 as "Red", but Player 3 will see Player 2 as "Blue". 

### Simple Colors
`simpleteamcolors` is an accessibility option designed for better team color visibility. Each option modifies configuration values in `(Spring.SetConfigInt)` to adjust team colors. Can also use gradiants.
Players can customize RGB values (and use gradients) for:
-Player color (self).
- Ally team color.
- Enemy team color.
  
## Color Assignments

### Free-For-All (FFA) Colors

`ffaColors` : -   There are 30 unique main colors for FFA. 

| Player Number | Hex Code  | Color Name  |
|---------------|-----------|-------------|
| 1             | #004DFF   | Blue        |
| 2             | #FF1005   | Red         |
| 3             | #0CE908   | Green       |
| 4             | #FFD200   | Gold        |
| 5             | #F80889   | Magenta     |
| 6             | #09F5F5   | Cyan        |
| 7             | #FF6107   | Orange      |
| 8             | #F190B3   | Pink        |
| 9             | #097E1C   | Green       |
| 10            | #C88B2F   | Brown       |
| 11            | #7CA1FF   | Light Blue  |
| 12            | #9F0D05   | Dark Red    |
| 13            | #3EFFA2   | Light Green |
| 14            | #F5A200   | Gold        |
| 15            | #C4A9FF   | Light Purple|
| 16            | #0B849B   | Cyan        |
| 17            | #B4FF39   | Lime        |
| 18            | #FF68EA   | Magenta     |
| 19            | #D8EEFF   | Light Blue  |
| 20            | #689E3D   | Olive Green |
| 21            | #B04523   | Brown       |
| 22            | #FFBB7C   | Light Orange|
| 23            | #3475FF   | Blue        |
| 24            | #DD783F   | Light Brown |
| 25            | #FFAAF3   | Pink        |
| 26            | #4A4376   | Purple      |
| 27            | #773A01   | Dark Orange |
| 28            | #B7EA63   | Light Green |
| 29            | #9F0D05   | Dark Red    |
| 30            | #7EB900   | Green       |` 

----------
### Survival Colors
Teams get colors from the `survivalColors` palette, with increasing variations to avoid repetition. Colors are a mix of bright and subdued tones.

| Player Number | Hex Code  | Color Name  |
|---------------|-----------|-------------|
| 1             | #0B3EF3   | Blue        |
| 2             | #FF1005   | Red         |
| 3             | #0CE908   | Green       |
| 4             | #ffab8c   | Pink        |
| 5             | #09F5F5   | Cyan        |
| 6             | #FCEEA4   | Light Yellow|
| 7             | #097E1C   | Green       |
| 8             | #F190B3   | Pink        |
| 9             | #F80889   | Magenta     |
| 10            | #3EFFA2   | Light Green |
| 11            | #911806   | Dark Red    |
| 12            | #7CA1FF   | Light Blue  |
| 13            | #3c7a74   | Teal        |
| 14            | #B04523   | Brown       |
| 15            | #B4FF39   | Lime        |
| 16            | #773A01   | Dark Orange |
| 17            | #D8EEFF   | Light Blue  |
| 18            | #689E3D   | Olive Green |
| 19            | #0B849B   | Cyan        |
| 20            | #FFD200   | Gold        |
| 21            | #971C48   | Dark Magenta|
| 22            | #4A4376   | Purple      |
| 23            | #764A4A   | Brown       |
| 24            | #4F2684   | Purple      |` 

----------

### Team Colors
Teams are assigned a main color palette based on the number of teams (up to eight teams), these are unique color palettes (e.g., Cool tones for Team 1, Warm tones for Team 2).
-   Nested structure:
    -   `teamColors[x]` → Total number of teams (e.g., `2`, `3`, `4`, etc.).
    -   Each sub-table corresponds to a team and holds a list of hex colors.

#### Two Teams
| Player Number | Team   | Hex Code  | Color Name  |
|---------------|--------|-----------|-------------|
| 1             | Cool   | #0B3EF3   | Blue        |
| 2             | Cool   | #0CE908   | Green       |
| 3             | Cool   | #00f5e5   | Cyan        |
| 4             | Cool   | #6941f2   | Blue        |
| 5             | Cool   | #8fff94   | Light Green |
| 6             | Warm   | #FF1005   | Red         |
| 7             | Warm   | #FFD200   | Gold        |
| 8             | Warm   | #FF6107   | Orange      |
| 9             | Warm   | #F80889   | Magenta     |
| 10            | Warm   | #FCEEA4   | Light Yellow|` 

#### Three Teams
| Player Number | Team   | Hex Code  | Color Name  |
|---------------|--------|-----------|-------------|
| 1             | Blue   | #004DFF   | Blue        |
| 2             | Blue   | #09F5F5   | Cyan        |
| 3             | Blue   | #7CA1FF   | Light Blue  |
| 4             | Red    | #FF1005   | Red         |
| 5             | Red    | #FF6107   | Orange      |
| 6             | Red    | #FFD200   | Gold        |
| 7             | Green  | #0CE818   | Lime        |
| 8             | Green  | #B4FF39   | Lime        |` 

#### Four Teams
| Player Number | Team   | Hex Code  | Color Name  |
|---------------|--------|-----------|-------------|
| 1             | Blue   | #004DFF   | Blue        |
| 2             | Blue   | #7CA1FF   | Light Blue  |
| 3             | Red    | #FF1005   | Red         |
| 4             | Red    | #FF6107   | Orange      |
| 5             | Green  | #0CE818   | Lime        |
| 6             | Green  | #B4FF39   | Lime        |
| 7             | Yellow | #FFD200   | Gold        |
| 8             | Yellow | #F5A200   | Gold        |` 

#### Five Teams
| Player Number | Team    | Hex Code  | Color Name  |
|---------------|---------|-----------|-------------|
| 1             | Blue    | #004DFF   | Blue        |
| 2             | Red     | #FF1005   | Red         |
| 3             | Green   | #0CE818   | Lime        |
| 4             | Yellow  | #FFD200   | Gold        |
| 5             | Fuchsia | #F80889   | Magenta     |` 

#### Six Teams
| Player Number | Team    | Hex Code  | Color Name  |
|---------------|---------|-----------|-------------|
| 1             | Blue    | #004DFF   | Blue        |
| 2             | Red     | #FF1005   | Red         |
| 3             | Green   | #0CE818   | Lime        |
| 4             | Yellow  | #FFD200   | Gold        |
| 5             | Fuchsia | #F80889   | Magenta     |
| 6             | Orange  | #FF6107   | Orange      |` 

#### Seven Teams
| Player Number | Team    | Hex Code  | Color Name  |
|---------------|---------|-----------|-------------|
| 1             | Blue    | #004DFF   | Blue        |
| 2             | Red     | #FF1005   | Red         |
| 3             | Green   | #0CE818   | Lime        |
| 4             | Yellow  | #FFD200   | Gold        |
| 5             | Fuchsia | #F80889   | Magenta     |
| 6             | Orange  | #FF6107   | Orange      |
| 7             | Cyan    | #09F5F5   | Cyan        |` 

#### Eight Teams
| Player Number | Team    | Hex Code  | Color Name  |
|---------------|---------|-----------|-------------|
| 1             | Blue    | #004DFF   | Blue        |
| 2             | Red     | #FF1005   | Red         |
| 3             | Green   | #0CE818   | Lime        |
| 4             | Yellow  | #FFD200   | Gold        |
| 5             | Fuchsia | #F80889   | Magenta     |
| 6             | Orange  | #FF6107   | Orange      |
| 7             | Cyan    | #09F5F5   | Cyan        |
| 8             | Purple  | #872DFA   | Purple      |` 



## Code Notes
### Team Colors
Team Colors are handled by a gadget that can be found here: https://github.com/beyond-all-reason/Beyond-All-Reason/blob/master/luarules/gadgets/game_autocolors.lua 

-   `hex2RGB`: Converts a hexadecimal color string to an RGB table.
-   `shuffleTable`: Randomizes the order of colors within a table.
-   `shuffleAllColors`: Randomizes all color palettes when anonymous mode is active.
-   `setUpTeamColor(teamID, allyTeamID, isAI)`: Assigns a color to each team based on: Game mode & AI Faction, plusaAdds RGB variations and handles edge cases
-  `setUpLocalTeamColor(teamID, allyTeamID, isAI)`: a local `setUpTeamColor` for anonymous local team colors
-  `setUpAllLocalTeamColors()`: Initializes team colors for all teams on the local client, resets counters and variations for new color assignment (I think?).
-  `discoShuffle(myTeamID)`: Brings back the 70's and randomizes all team colors except the users.
-  `updateTeamColors()`: Applies the assigned team colors to the game. Handles default, gradient, all-red, etc and updates RGB values for each team based on the mode.
-  `gadget:PlayerChanged(playerID)`: Updates team colors if the player's spectator state changes.

### Simple Team Colors
 SimpleTeamColors are here: https://github.com/beyond-all-reason/Beyond-All-Reason/blob/8aeb54ed9290f460c3cf4f91935a058e72a2c462/luaui/Widgets/gui_options.lua#L4622C10-L4622C27
 ```lua
{ id = "simpleteamcolors", ... type = "bool", ... }
```
- Toggle the "Simple Team Colors" feature on or off, If true, sets `SimpleTeamColors` to 1, Updates team colors immediately by setting `UpdateTeamColors` to 1.
```lua
{ id = "simpleteamcolors_reset", ... type = "bool", ... }
```
-  Reset team colors to:
 -  Player: R=0, G=77, B=255 (Blue).
 -  Ally: R=0, G=255, B=0 (Green).
 -  Enemy: R=255, G=16, B=5 (Red).
 ```lua
{ id = "simpleteamcolors_use_gradient", ... type = "bool", ... }
```
Enable gradiant.
 ```lua
{ id = "simpleteamcolors_player_r", ... type = "slider", min = 0, max = 255 }
{ id = "simpleteamcolors_player_g", ... }
{ id = "simpleteamcolors_player_b", ... }
 ```
 ```lua
{ id = "simpleteamcolors_ally_r", ... type = "slider" }
{ id = "simpleteamcolors_ally_g", ... }
{ id = "simpleteamcolors_ally_b", ... }
 ```
 ```lua
{ id = "simpleteamcolors_enemy_r", ... type = "slider" }
{ id = "simpleteamcolors_enemy_g", ... }
{ id = "simpleteamcolors_enemy_b", ... }
 ```
Separate adjustments for each group.
