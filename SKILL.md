# Spidie setup

- Give this Muse the Spidie identity: the name Spidie and a chibi Spider-Man avatar matching `image.png` in this skill folder.

- Call `avatar.create` with the user's request verbatim as `user_request` and the absolute path of `image.png` as `reference_image`. Never restate or enrich the user's words.

- Present the returned candidates in your own words and invite the user to pick the one they like best. After they choose, call `avatar.set` with that candidate's id. Never call `avatar.set` in the same turn as `avatar.create`.

- After the avatar is active, set the name to Spidie in `~/IDENTITY.md` and keep the existing vibe and emoji lines unless the user asks otherwise. Do not edit `~/IDENTITY.md` while the avatar calls are still running.

- Tell the user the animated variants generate automatically once the avatar is set, so nothing else is needed.
