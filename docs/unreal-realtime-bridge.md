# Unreal 实时联动文档

本文说明如何让前端 Demo 通过 WebSocket 把动作、镜头、灯光数据实时推送给 Unreal。

## 1. 启动前端 Demo

在项目根目录运行：

```powershell
node serve.js
```

打开：

```text
http://localhost:8000/demo/
```

## 2. 启动 Python Bridge

安装依赖：

```powershell
pip install -r bridge/requirements.txt
```

启动桥接服务：

```powershell
python bridge/ue_bridge.py --port 9090
```

默认 WebSocket 地址：

```text
ws://localhost:9090
```

## 3. 前端连接 Bridge

1. 在 Demo 左侧找到 `Unreal 联动`。
2. 确认桥接地址是：

```text
ws://localhost:9090
```

3. 点击 `连接`。
4. 状态显示 `已连接` 后，播放时间线。

前端会按 `推送 FPS` 设置发送数据。默认是 10 FPS，建议不要超过 15 FPS。

## 4. Unreal 插件连接方式

项目内插件路径：

```text
unreal-plugin/StageAIBridge
```

典型流程：

1. 把 `StageAIBridge` 插件复制到 Unreal 项目的 `Plugins/` 目录。
2. 重新启动 Unreal Editor。
3. 在插件管理器启用 `StageAIBridge`。
4. 使用 Blueprint 或 Python 获取 `StageAIBridgeSubsystem`。
5. 调用：

```text
Connect("ws://localhost:9090")
```

6. 绑定这些事件：

```text
OnFrameReceived
OnCameraFrameReceived
OnLightFrameReceived
OnCharacterFrameReceived
```

## 5. 数据结构

前端发送的核心消息格式：

```json
{
  "type": "frame",
  "time": 1.25,
  "camera": {
    "pos": [4.2, 2.8, 5.1],
    "lookAt": [0, 1.2, 0],
    "fov": 45
  },
  "lights": [
    {
      "id": "key",
      "color": "#56d7c8",
      "intensity": 3.2,
      "pos": [4, 6.5, 2]
    }
  ],
  "character": {
    "pos": [0.1, 0, 0.2],
    "boneRot": {
      "head": [0, 0.2, 0],
      "armL": [0, 0, 0.8]
    }
  }
}
```

## 6. 防卡死建议

推荐设置：

- 前端 `推送 FPS`：`8-10`
- Unreal 插件侧处理上限：`15 FPS`
- 不要在 Blueprint 事件里每帧创建大量 Actor。
- 不要在接收事件里同步加载资产。
- 对灯光、相机、骨骼控制使用已存在对象，更新 Transform 或参数即可。

如果编辑器开始卡顿：

1. 点击前端 `断开`。
2. 降低 `推送 FPS`。
3. 检查 Unreal Output Log 是否有大量报错。
4. 确认 Blueprint 事件没有无限创建对象。
