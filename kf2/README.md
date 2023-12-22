# Killing Floor 2

For the official docs, refer to the [Killing Floor 2 Wiki's Dedicated Server Guide](https://wiki.killingfloor2.com/index.php?title=Dedicated_Server_(Killing_Floor_2)).
Most of the notes here are retranscribed here for brevity and easier referral. There are additional notes in here that are specific to my implementation.

## Running the Server

Simply run:

```bash
~/kf2/start-server
```

Which runs the KF2 Linux executable at `~/Steam/steamapps/common/kf2server/Binaries/Win64/KFGameSteamServer.bin.x86_64`.

Use `start-server --help` for usage info.

### `start-server` CLI

<!-- Long description here, shorter descriptions in the help menu. -->
<!-- Remember to update both... -->

| Flag | Description | Value(s) |
|------|-------------|----------|
| `-h,--help` | Show help menu. | - |
| `-m,--map` `<map>` | Choose the map to set on server start. Default is `kf-bioticslab`. | Look at maps in `[KFGame.KFGameInfo].GameMapCycles` in `KFGame.ini` |
| `--game-mode` `<mode>` | Choose the game mode on server start. Default is `survival`. | `survival`, `versus`, `weekly`, `endless` |

## Configuration

In `~/Steam/steamapps/common/kf2server/KFGame/Config/` exists multiple `*.ini` config files:

- `KFGame.ini`
  - General game config for the server. (stuff like, server info, name, password, game mode, game maps, etc.)
- `KFEngine.ini`
  - Server port management, server tick rate
- `KFWeb.ini`
  - Web admin config options

### Custom Maps

Add the workshop ID into `KFEngine.ini`:

```ini
; This section will exist already if there are custom maps already set up...
[OnlineSubsystemSteamworks.KFWorkshopSteamworks]
ServerSubscribedWorkshopItems=2998243647 ; <-- Add a new item with the workshop ID
```

## Updating

Simply run:

```bash
~/kf2/run-update
```
