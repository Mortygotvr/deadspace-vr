# Dead Space VR for the Theater Control Panel

`deadspace.tcp` is a module for the [Theater Control Panel](https://github.com/Mortygotvr/Theater-Control-Panel).
Load it in the panel the same way as its other modules.

With it you can:

- **Spawn the game's own monsters in front of Isaac** from any trigger, for
  example channel point redeems or chat commands. Use the command
  **Dead Space: Spawn Monster** and pick a monster and how many (1 to 5).
  The count accepts the panel's variables and math, such as `{1}`.
- **React to the game** with the trigger **Dead Space Event**: monster
  spawned, spawn failed, Isaac hurt, grabbed, died, and more. For example,
  post a chat message when a redeemed slasher arrives.
- **See the connection and Isaac's health** on the module's card.

It talks to the mod's game feed on `ws://127.0.0.1:47601`. You can change
this address in the module's settings.

## Before you start

- You need a version of the mod newer than 0.1.0-alpha (the first one with
  the `spawn` command).
- A monster can only be spawned after you have met one in the game. The
  mod remembers it from then on. Until then, the spawn fails with "not
  learned yet".
