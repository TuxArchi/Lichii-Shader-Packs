# Lichii shader packs

Code-free shader packs for Lichii. A pack contains pipeline keys and captured translation
metadata, never shader instructions, game files, saves or driver cache blobs. Lichii rebuilds the
shader code from the user's own game copy and verifies the pack's SHA-256.

## Download

Right-click a title in Lichii → **Download Available Shaders**. The client reads `index.json` from
the latest release.

## Publishing a pack

Export it with:

```sh
eden-cli --export-shader-pack <title id> <output.json> [game version]
```

Then upload the JSON as a release asset and regenerate the index:

```sh
python3 tools/nx2/shader_pack_index.py \
  --base-url https://github.com/TuxArchi/Lichii-Shader-Packs/releases/download/<tag> \
  --output index.json *.shaderpack.json
```

Packs are game-derived metadata. Only publish a pack when you have the rights to do so.
