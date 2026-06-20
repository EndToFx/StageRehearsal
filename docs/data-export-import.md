# 数据资产导出与第三方软件导入文档

Demo 当前支持导出 JSON 数据。它是中间交换格式，可被 Unreal、Blender、TouchDesigner、After Effects 或自定义脚本读取。

## 1. 导出数据

在前端 Demo 中：

1. 点击 `生成全部`。
2. 确认右侧关键帧数量不为 0。
3. 点击右上角 `导出 JSON`。

文件名类似：

```text
stage-rehearsal-1780000000000.json
```

## 2. JSON 内容

导出的 JSON 包含：

```json
{
  "meta": {
    "product": "AI Digital Rehearsal",
    "duration": 12,
    "style": "studio"
  },
  "animation": [],
  "camera": [],
  "lighting": []
}
```

字段说明：

- `animation`：角色位移、头部、手臂、腿部等关键帧。
- `camera`：摄像机位置、FOV、时间点。
- `lighting`：灯光颜色、强度、角度、时间点。

## 3. 导入 Unreal 的推荐方式

### 方法 A：实时联动

适合预览和调试。

1. 运行 Python bridge。
2. 前端点击 `连接`。
3. Unreal 插件订阅实时帧数据。
4. 在 Blueprint 或 C++ 中把数据映射到 Camera、Light、Character。

### 方法 B：离线 JSON 导入

适合生成 Sequencer 或固定资产。

1. 在前端导出 JSON。
2. 把 JSON 放到 Unreal 项目目录，例如：

```text
Content/StageAI/Data/
```

3. 使用 Unreal Python 或 C++ 读取 JSON。
4. 创建 Level Sequence。
5. 把 `camera` 写入 CineCameraActor Transform/FOV 关键帧。
6. 把 `lighting` 写入 Light Actor 的颜色和强度关键帧。
7. 把 `animation` 映射到 Control Rig 或角色骨骼控制器。

## 4. 导入 Blender

推荐流程：

1. 打开 Blender。
2. 使用 Python 脚本读取 JSON。
3. 创建或选择 Camera。
4. 遍历 `camera` 数组，为 Camera 插入位置和 FOV 关键帧。
5. 创建 Area Light 或 Point Light。
6. 遍历 `lighting` 数组，插入颜色和强度关键帧。
7. 将 `animation` 映射到骨骼或空物体。

## 5. 导入 TouchDesigner

推荐流程：

1. 使用 `File In DAT` 读取 JSON。
2. 使用 Python DAT 解析 `camera`、`lighting`、`animation`。
3. 把数值输出到 CHOP。
4. 使用 CHOP Export 控制 Camera、Light、Geometry。

## 6. 后续可扩展格式

后续可从 JSON 转出：

- `FBX`：角色动画或摄像机动画。
- `USD`：场景、灯光、相机交换。
- `CSV`：灯光控台 Cue 表。
- `GLTF/GLB`：Web 和 Blender 资产交换。

当前建议先以 JSON 作为稳定中间格式，再根据目标软件写转换脚本。
