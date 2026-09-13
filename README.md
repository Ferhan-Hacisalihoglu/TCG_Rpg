# TCG_Rpg — Trading Card Game (Unreal Engine 5.8)

A Blueprint-only trading card game prototype built in Unreal Engine 5.8. Features a 5v5 card board, data-driven card definitions, AI opponents, and a multiplayer-ready lobby.

<img width="1919" height="1079" alt="Screenshot 2026-09-13 114127" src="https://github.com/user-attachments/assets/a7d0eacc-7710-4ae7-93b0-ea36dc9d3030" />


## Features

- **Card battler core** — player vs. enemy card spawns on a symmetric 5v5 board (`Lvl_Test`)
- **Data-driven cards** — `DT_Card` / `DT_PlayerAttributes` DataTables + `ST_Card`, `ST_PlayerInfo`, `ST_TCGSettings` structs
- **Custom card rules** — extensible `BP_BaseCardCustomRule` (e.g. `BP_CustomRule_Fireball`)
- **AI opponent** — `BP_AI` + `BP_AIController_TCG`
- **Full UMG UI** — main HUD, dice (`WBP_Dice`), notifications, enemy HUD, player vitality widgets, legacy + current card frames
- **Lobby** — `GM_Lobby`, lobby player/controller, server-name widgets (`TCGLobby`)
- **Dice & icon set** — 6 dice faces, 12+ ability icons (sword, shield, fireball, frost, arcane…)

## Requirements

- Unreal Engine **5.8**
- Windows 64-bit (developed / tested on Windows)
- No C++ toolchain required — **Blueprint-only** (no `Source/` folder)

## Getting Started

1. Clone the repo:
   ```bash
   git clone <repo-url> TCG_Rpg
   ```
2. Open `TCG_Rpg.uproject` with Unreal Engine 5.8.
3. Default startup map: `/Game/_Main/GameMode/TCGGame/Level/Lvl_Test`.
4. Press **Play (PIE)** — default GameMode `GM_TcgGame`, GameInstance `GI_TCGGameInstance`.

## Project Structure

```text
Content/
  _Main/
    GameMode/
      GI_TCGGameInstance          # GameInstance
      TCGGame/
        Actor/                    # BP_Card, BP_CardInstance, BP_CardSpawn*, BP_AI, BP_AIController_TCG
        Actor/CardCustomRules/    # BP_BaseCardCustomRule, BP_CustomRule_Fireball
        GameMode/                 # GM_TcgGame, GS_TCGGame_State, PC_TCG, BP_BaseTcgPawn, BPC_TCG_Component, BPI_TCG_Controller
        Level/                    # Lvl_Test
        Materials/ Mesh/ Texture/ # card art, dice, icons, UI
        Varaibles/                # E_* enums, DT_* tables, ST_* structs
        Widget/                   # WBP_MainTcg, WBP_Dice, WBP_Card, Enemy, PlayerVitality
      TCGLobby/
        TCGLobby (level), GM_Lobby, PC_TCGLobby, PlayerLobby
        Widgets/                  # WBP_MainLobby, WBP_ServerName
```

## Gameplay Notes

- `Lvl_Test` outliner: `CardLocations/` (5x `BP_PlayerCardSpawn` + 5x `BP_EnemyCardSpawn`), `Lighting/` (directional, sky, fog, clouds).
- Card data lives in `DT_Card`; player stats in `DT_PlayerAttributes`.
- New card effects: subclass `BP_BaseCardCustomRule` and add the rule action attribute (`E_RuleActionAttribute`).

## Contributing

Pull requests welcome. Keep Blueprint diffs small and test in PIE before submitting.
"# TCG_Rpg" 
