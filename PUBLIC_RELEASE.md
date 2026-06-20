# Public Release Checklist

This repository is prepared as a static GitHub Pages demo.

## Files intended for the public repository

- `index.html`
- `demo/index.html`
- `README.md`
- `docs/*.md`
- `_shared/fonts/*.ttf`
- `assets/models/RobotExpressive.glb`
- `assets/models/debug_native_glb.glb`
- `assets/models/IozsL7ZmHiVHopD-D3_ay.usdz`
- `assets/refs/REPO.png`
- `.nojekyll`
- `.gitignore`

## Files intentionally excluded

- Local Python bridge services: `bridge/`
- Unreal Engine plugin source: `unreal-plugin/`
- Local diagnostic scripts: `_*.py`, `test_subsystem*.py`, `ws_relay_server.py`
- Legacy/private product deck files
- Generated JPG marketing images under `assets/*.jpg`

## Asset note

`assets/models/debug_native_glb.glb` is the default Kimodo-compatible rig preview. `assets/models/IozsL7ZmHiVHopD-D3_ay.usdz` is the Hunyuan-compatible prototype asset. `assets/refs/REPO.png` is the visual reference. Do not add commercial game assets unless their license clearly allows redistribution in a public GitHub repository.

## GitHub Pages target

Repository:

```text
https://github.com/EndToFx/StageRehearsal.git
```

Pages URL after enabling Pages from the `main` branch root:

```text
https://endtofx.github.io/StageRehearsal/
```

Interactive demo:

```text
https://endtofx.github.io/StageRehearsal/demo/
```
