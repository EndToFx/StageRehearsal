# AI Digital Rehearsal

Browser-based rehearsal demo for motion, camera, lighting, and Unreal Engine bridge tests.

## Local demo

```powershell
node serve.js
```

Open:

```text
http://localhost:8000/demo/
```

For Unreal bridge streaming, start the Python WebSocket bridge first:

```powershell
python bridge/ue_bridge.py --port 9090
```

Then open the demo, generate data, and click `Connect` in the Unreal Bridge panel.

## Public GitHub Pages demo

1. Push this repository to GitHub.
2. In GitHub, open `Settings` -> `Pages`.
3. Set `Source` to `Deploy from a branch`.
4. Choose branch `main` and folder `/ (root)`.
5. Save and wait for the Pages deployment to finish.

Your public demo URL will look like:

```text
https://endtofx.github.io/StageRehearsal/demo/
```

If you use a custom domain, keep `.nojekyll` in the repository root so the `_shared` folder is served correctly.

## Notes

- The public GitHub Pages site can host the browser demo, but it cannot expose your local Unreal Editor.
- Unreal live streaming still requires the Python bridge and Unreal Editor to run on the same machine or on a reachable server.
- The frontend caps bridge streaming FPS and disconnects when WebSocket buffering grows too large, which helps prevent browser and editor freezes.

## Detailed docs

- [GitHub Pages 外网 Demo 发布教程](docs/github-pages-demo.md)
- [Demo 前端使用文档](docs/demo-user-guide.md)
- [Unreal 实时联动文档](docs/unreal-realtime-bridge.md)
- [数据资产导出与第三方软件导入文档](docs/data-export-import.md)
