# Spidie Avatar Studio

Two modes: set up Spidie as-is (Mode 1), or generate a custom character in the same chibi style and proportions (Mode 2).

Converse in the user's language throughout.

## Mode 1 — Set up Spidie

- Give this Muse the Spidie identity: the name Spidie and a chibi Spider-Man avatar matching `image.png` in this skill folder.

- Call `avatar.create` with the user's request verbatim as `user_request` and the absolute path of `image.png` as `reference_image`. Never restate or enrich the user's words.

- Present the returned candidates in your own words and invite the user to pick the one they like best. After they choose, call `avatar.set` with that candidate's id. Never call `avatar.set` in the same turn as `avatar.create`.

- After the avatar is active, set the name to Spidie in `~/IDENTITY.md` and keep the existing vibe and emoji lines unless the user asks otherwise. Do not edit `~/IDENTITY.md` while the avatar calls are still running.

- Tell the user the animated variants generate automatically once the avatar is set, so nothing else is needed.

## Mode 2 — Custom character in Spidie style

When the user wants their own character design (any species, any outfit) as an avatar, generated to match Spidie's body proportions and art style:

1. Ask them to describe the character in their own words — species, colors, outfit, vibe, pose. One or two sentences is enough. If they only name a known character (e.g. "LinaBell"), confirm which version/outfit before generating.

2. Call `media.generate_image` with:
   - First entry: `kind: "image"`, value = the absolute path of `image.png` in this skill folder (the style reference — always pass it).
   - Second entry: `kind: "text"`, value = the user's character description, followed by a blank line and the style-constraint block below, copied verbatim.

3. Read the returned image before presenting it. Show it to the user and describe what was made.

4. Offer tweaks in their words ("換個pose", "唔要耳機", …). Each tweak reuses the previous result via `resume_from_snapshot_id` and describes only what changes — the style constraints carry over automatically, do not re-paste the block on refinements.

5. Do not rename the user's Muse to Spidie in this mode — the character is theirs, the name stays theirs (unless they ask).

### Style-constraint block (append verbatim after the user's description)

> Style constraints — always apply; the character description must not override these: chibi collectible-figure style matching the reference image. Oversized round head taking up roughly half of the total figure height (about 2 heads tall overall), short stubby limbs, soft matte 3D vinyl-figure rendering, large expressive eyes, clean plain white background, full-body centered composition. Keep the same body proportions, figure size, and art style as the reference image; only the character's identity, outfit, colors, and pose follow the user's description.
