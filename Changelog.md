# Changelog  

Here you can discover the latest changes to the API.
## 10th September 2026
 * Added the interactable entity setting. Set it on a mesh entity or a mob (e.g. `api.setTargetedPlayerSettingForEveryone(eId, "interactable", true)`) to make alt actioning it count as an interaction: the alt action is consumed, so a held block isn't placed through the entity and a held throwable isn't used, and `onPlayerAltAction` fires with the entity as the target. Leave it off for decorative entities, or they will swallow player input. It also makes the entity pickable, so an entity can be `interactable` with `canAttack` off: the player's aim lands on it and interacting works, but swinging or shooting at it does nothing. On a mob it applies alongside the usual mounting and taming behaviour rather than replacing it, though there a held throwable or consumable is still used in preference to interacting.
 * Entities marked `interactable` now show an interaction prompt by the crosshair while a player is looking at them, showing the key bound to the interact action (`E` by default) so players can tell which input to use. Set the new `interactionPrompt` entity setting to replace the label beside that key, e.g. `api.setTargetedPlayerSettingForEveryone(eId, "interactionPrompt", "Open Shop")`, and leave it off for the default "Interact". It takes plain text or `CustomTextStyling`, and describes what interacting does rather than which button to press, since the engine draws the key itself. Not shown on touchscreens, where a tap needs no prompt.
## 8th September 2026
 * Added first-party plugins!
   * You can import helper scripts to help you from `@plugins`
     * E.g. `import { setTimeout } from "@plugins/helpers"`
   * See the plugins how-to for more information.
 * The biggest example of this is **Session-Based Game**, a helper to help you create a game with mini-matches, like Bedwars/Skywars etc.
   * `import { createGame } from "@plugins/sessionBasedGame"` to check it out
   * See the SessionBasedGame how-to for more information.
## 28th August 2026
 * Added vehicle spawn callbacks:
   * `onPlayerAttemptSpawnVehicle`
   * `onWorldAttemptSpawnVehicle`
   * `onPlayerSpawnVehicle`
   * `onWorldSpawnVehicle`
   * `onVehicleDespawned`
 * Added `onEntityDeleted`, called whenever any non-player entity is deleted.
## 27th August 2026
(haven’t done yet)
Added api.attemptSpawnVehicle to spawn rideable vehicles (boats, karts, cars) which players can mount with an alt action.
18th August 2026
Added TypeScript support to World Code!
Rename your file from index.js to index.ts to use TypeScript files!
Import some of our types from @bloxd
E.g. import type { PlayerId } from "@bloxd"
Use your own types!
Type Checking is supported and errors will show if you use incorrect types.
Multiple files are supported! Split your code across multiple files for better readability!
Create .js and .ts files
Use import / export syntax to be able to import files across between versions
index.js or index.ts MUST be where your callbacks are stored and cannot be imported anywhere else.
require() syntax technically works although isn't type-safe.
Increased total code size from 64k characters to 512k characters.
Added variations to custom games!
Each custom game can now have multiple variations, with default being the default variation.
api.getVariation
api.matchmakeToVariation
See the variations doc for more information.
11th August 2026
Added currency API:
api.setCurrency
api.getCurrency
api.deleteCurrency
api.getCurrencyAmount
api.setCurrencyAmount
api.giveCurrencyAmount
These currencies can be used in the currency field in the Shop to automatically deduct currency on purchase.
These can also be persisted across sessions.
10th August 2026
Added to the UI Request System:
api.addUiRequestPopup
7th August 2026
Added UI Request System:
api.addUiRequest
api.deleteUiRequest
onUiRequestResponded
20th July 2026
New mob settings:
runningJumpInfo
runningRandomFacingInfo
runningSlideInfo
walkingJumpInfo
walkingRandomFacingInfo
walkingSlideInfo
13th July 2026
Added new bridgeInfo mob setting to make mobs build bridges or leave trails, e.g.:
bridgeInfo: {
    blockToPlace: "Bricks",
    mustBeGrounded: false,
    yOffset: -1,
},

26th June 2026
Added new client options for custom game UI:
middleTextTop
headerChips
Added ProgressBar support to options that accept a CustomTextStyling
e.g. ["Loading", { type: "ProgressBar", progress: 0.5 }]
15th June 2026
Added new client options for adjusting the third person camera:
cameraRotationOffset
cameraPositionOffset
11th June 2026
Added the ability to get and set scale for lifeforms (players, mobs)
api.getLifeformScale
api.setLifeformScale
Added new block standing callbacks:
This is to prevent having to use onBlockStand, which eats into your runtime limit significantly due to its high frequency of being called
onBlockStandStart
onBlockStandStop
Added isReceiveDamageCooldownGlobal client option and mob setting
10th June 2026
Added showChatBubbles client option
Added useRespawnButton client option
Added multilineTextBox entity setting
Added lobbyLeaderboardTags entity setting
18th May 2026
Added the ability to change the gamemode of a player
api.setPlayerGamemode
api.getPlayerGamemode
Added the ability to queue text to be displayed in different places on the screen
api.queueMiddleTextLower
api.queueMiddleTextUpper
api.queueCrosshairText
api.getQueuedStatus
api.removeFromQueue
15th May 2026
Significantly increased runtime limit - interrupts should be less frequent
Added api.isNearInterrupt
12th May 2026
Added new client option groundArrowPath
11th May 2026
Added Changelog
Added a bunch of new API Methods:
api.addCustomKillfeedMessage
api.deleteAllItems
api.findItem
api.findStandardChestItem
api.getEffectLevel
api.getItemDropName
api.getItemIDsOverlappingWithPlayer
api.getMobDbId
api.hasEffect
api.preventFallDamageNextGrounding
api.removeItemNameFromStandardChest
api.resetCanChangeBlock
api.resetCanPickUpItem
api.setOtherEntitySettingToDefault
api.updateMeshParticleSystems
7th May 2026
Added api.copyChunk
Added onPlayerToggledShopMenu
28th April 2026
Doubled code block size (16000 -> 32000)
'Hide World Code' option renamed to 'Hide Code' and also hides code of Code Blocks
New docs page!
23rd April 2026
Added api.matchmakePlayer
Added per-item gun stats in customAttributes.gunStats
21st April 2026
Added database methods to write persisted data to be saved between sessions.
There are two sections of database values:
Lobby
api.getLobbyDBValue
api.setLobbyDBValue
api.deleteLobbyDBValue
api.deleteAllLobbyDBValues
Writes data that is persisted to the *lobby*, whether it's a worlds lobby or a lobby within a custom game
Player
api.getDBValue
api.setDBValue
api.deletePlayerDBValue
api.deleteAllPlayerDBValues
Writes data that is persisted to the player. For custom games, this data persists *between* lobbies
16th April 2026
Added api.setItemStat
11th April 2026
The Code Editor now supports collaborative editing
You can now simultaneously code with your other fellow coders at the same time! Hop into a code block or World Code together to simultaneously create the best World or the best Custom Game ever!!
7th April 2026
New Code Editor UI! Syntax Highlighting, Autocomplete, Error Checking, and more!
25th March 2026
Increased world code size from 16000 to 64000 characters
24th March 2026
Added mesh entities!
api.attemptCreateMeshEntity
api.updateMeshEntity
api.deleteMeshEntity
Added throwables!
api.attemptCreateThrowable
api.deleteThrowable
23rd March 2026
Added the ability to open and close chests for players, going beyond reach distance to open chests from far away
api.openChestForPlayer
api.closeChestForPlayer
Previous Changes
For previous changes, see the code-api repository or #dev-log in the Bloxd Discord server
