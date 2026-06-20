# Demo 前端使用文档

默认入口：

```text
http://localhost:8000/demo/
```

外网发布后入口：

```text
https://endtofx.github.io/StageRehearsal/demo/
```

## 1. 界面布局

Demo 是三栏工作台：

- 左侧：创意描述、风格选择、生成模块、Unreal 联动设置。
- 中间：3D 舞台视口，默认加载 `RobotExpressive.glb` 机器人测试模型。
- 右侧：关键帧数据、GitHub Demo 提示、联动保护说明。
- 底部：时间线、播放按钮、速度选择。

## 2. 语言切换

页面默认是中文。

右上角语言菜单可以切换：

```text
中文 / English
```

## 3. 生成数据

左侧 `生成模块` 有三个按钮：

- `动作`：生成角色动作关键帧。
- `运镜`：生成摄像机环绕和推进轨迹。
- `灯光`：生成舞台灯光 Cue。
- `生成全部`：一次性生成动作、运镜和灯光，并自动播放。

可调参数：

- `时长`：控制预演总时长。
- `能量`：控制动作节奏幅度。
- `镜头`：控制运镜范围。

## 4. 视口操作

中间舞台视口支持鼠标操作：

- 左键拖动：旋转视角。
- 滚轮：缩放。
- 右上角 `#`：显示/隐藏网格。
- 右上角 `C`：切换轨道视角和生成的摄像机视角。

## 5. 导出 JSON

点击右上角 `导出 JSON` 会下载一份数据文件，包含：

- `meta`：项目元信息。
- `animation`：动作关键帧。
- `camera`：摄像机关键帧。
- `lighting`：灯光 Cue。

这份 JSON 可用于后续导入 Unreal、Blender、TouchDesigner 或自定义工具。

## 6. 默认测试模型

当前默认模型：

```text
assets/models/RobotExpressive.glb
```

如果你想替换模型：

1. 把新的 `.glb` 或 `.gltf` 放到 `assets/models/`。
2. 修改 `demo/index.html` 中的模型路径。
3. 保证模型授权允许公开展示，尤其是发布到 GitHub Pages 时。

注意：不要直接使用商业游戏资源，除非你确认有授权。
