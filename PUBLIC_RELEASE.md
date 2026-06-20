# Public Release Checklist

This repository is prepared as a static GitHub Pages demo.

## Files intended for the public repository

- `index.html`
- `demo/index.html`
- `README.md`
- `docs/*.md`
- `_shared/fonts/*.ttf`
- `assets/models/RobotExpressive.glb`
- `.nojekyll`
- `.gitignore`

## Files intentionally excluded

- Local Python bridge services: `bridge/`
- Unreal Engine plugin source: `unreal-plugin/`
- Local diagnostic scripts: `_*.py`, `test_subsystem*.py`, `ws_relay_server.py`
- Legacy/private product deck files
- Generated JPG marketing images under `assets/*.jpg`

## Asset note

`assets/models/RobotExpressive.glb` is used only as a public demo test model. Do not add commercial game assets unless their license clearly allows redistribution in a public GitHub repository.

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
