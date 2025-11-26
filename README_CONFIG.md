# 配置文件使用说明

## 概述

`config.json` 是3D卡通人智能聊天助手的配置文件，您可以通过修改此文件来调整应用的默认参数，而无需修改HTML代码。

## 配置文件位置

配置文件应与HTML文件放在同一目录下，文件名为 `config.json`。

## 配置项说明

### 1. API配置 (`api`)

```json
{
  "api": {
    "url": "",
    "key": "",
    "appId": ""
  }
}
```

- `url`: API接口地址
- `key`: API密钥
- `appId`: 应用ID

**注意**：建议不要在此文件中存储敏感信息。可以在界面中配置API信息，配置会保存在浏览器的localStorage中。

### 2. 模型配置 (`model`)

```json
{
  "model": {
    "defaultModelUrl": "模型URL地址",
    "defaultPosition": { "x": 0, "y": 0, "z": 0 },
    "defaultRotation": { "x": 0, "y": 0, "z": 0 },
    "autoScale": true,
    "scaleMultiplier": 2,
    "localModelRotationY": -90
  }
}
```

- `defaultModelUrl`: 默认加载的3D模型URL
  - **支持相对路径**：如 `"model/little_kid_stand.glb"`（相对于HTML文件位置）
  - **支持绝对URL**：如 `"https://example.com/model.glb"`
  - **注意**：相对路径需要在Web服务器环境下运行才能正常加载，直接用file://协议打开可能无法加载
- `defaultPosition`: 模型的默认位置坐标（x, y, z）
- `defaultRotation`: 模型的默认旋转角度（度）
- `autoScale`: 是否自动缩放模型（true/false）
- `scaleMultiplier`: 自动缩放时的缩放倍数
- `localModelRotationY`: 本地模型加载时的Y轴旋转角度（度）

### 3. 相机配置 (`camera`)

```json
{
  "camera": {
    "fov": 75,
    "near": 0.1,
    "far": 1000,
    "position": { "x": 0, "y": 1.5, "z": 5 },
    "target": { "x": 0, "y": 1, "z": 0 }
  }
}
```

- `fov`: 视野角度
- `near`: 近裁剪面距离
- `far`: 远裁剪面距离
- `position`: 相机初始位置
- `target`: 相机目标点

### 4. 灯光配置 (`light`)

```json
{
  "light": {
    "ambient": {
      "color": "#ffffff",
      "intensity": 0.6
    },
    "directional": {
      "color": "#ffffff",
      "intensity": 0.8,
      "position": { "x": 5, "y": 10, "z": 7 },
      "castShadow": true,
      "shadowMapSize": { "width": 2048, "height": 2048 }
    }
  }
}
```

- `ambient`: 环境光配置
  - `color`: 颜色（十六进制）
  - `intensity`: 强度（0-1）
- `directional`: 定向光配置
  - `color`: 颜色
  - `intensity`: 强度
  - `position`: 位置
  - `castShadow`: 是否投射阴影
  - `shadowMapSize`: 阴影贴图尺寸

### 5. 轨道控制器配置 (`controls`)

```json
{
  "controls": {
    "enableDamping": true,
    "dampingFactor": 0.05,
    "minDistance": 1,
    "maxDistance": 20
  }
}
```

- `enableDamping`: 是否启用阻尼
- `dampingFactor`: 阻尼系数
- `minDistance`: 最小缩放距离
- `maxDistance`: 最大缩放距离

### 6. 场景配置 (`scene`)

```json
{
  "scene": {
    "backgroundColor": "#0f172a",
    "shadowMap": {
      "enabled": true,
      "type": "PCFSoftShadowMap"
    },
    "renderer": {
      "antialias": true,
      "alpha": true,
      "powerPreference": "high-performance",
      "pixelRatio": "auto"
    }
  }
}
```

- `backgroundColor`: 背景颜色
- `shadowMap`: 阴影贴图配置
  - `enabled`: 是否启用
  - `type`: 阴影类型（"PCFSoftShadowMap" 或 "BasicShadowMap"）
- `renderer`: 渲染器配置
  - `antialias`: 抗锯齿
  - `alpha`: 透明通道
  - `powerPreference`: 性能偏好
  - `pixelRatio`: 像素比（"auto" 或数字）

### 7. 文字显示配置 (`textDisplay`)

```json
{
  "textDisplay": {
    "speed": 50
  }
}
```

- `speed`: 文字显示速度，单位：毫秒/字

### 8. 模型跳转配置 (`modelJump`)

```json
{
  "modelJump": {
    "clickJumpEnabled": true,
    "currentModelIndex": 0
  }
}
```

- `clickJumpEnabled`: 是否启用点击跳转功能
- `currentModelIndex`: 当前模型索引（从0开始）

### 9. 模型库 (`modelLibrary`)

```json
{
  "modelLibrary": [
    {
      "name": "模型名称",
      "url": "模型URL或相对路径",
      "description": "模型描述",
      "jumpTo": 1
    }
  ]
}
```

- `name`: 模型显示名称
- `url`: 模型文件URL或相对路径
  - **相对路径示例**：`"model/little_kid_stand.glb"`（相对于HTML文件位置）
  - **绝对URL示例**：`"https://example.com/model.glb"`
  - **注意**：支持GLB/GLTF格式，相对路径需要在Web服务器环境下运行
- `description`: 模型描述
- `jumpTo`: 点击后跳转到的模型索引（-1表示不跳转）

### 10. UI文本配置 (`ui`)

```json
{
  "ui": {
    "title": "3D卡通人智能助手",
    "subtitle": "与可爱的3D卡通角色进行智能对话",
    "welcomeMessage": "欢迎消息",
    "inputPlaceholder": "输入您的问题...",
    "statusText": "请配置API信息"
  }
}
```

用于自定义界面显示的文本内容。

### 11. 动画配置 (`animation`)

```json
{
  "animation": {
    "defaultEnabled": true
  }
}
```

- `defaultEnabled`: 动画默认是否启用

### 12. 文件上传配置 (`file`)

```json
{
  "file": {
    "maxFileSize": 52428800,
    "allowedExtensions": [".glb", ".gltf"]
  }
}
```

- `maxFileSize`: 最大文件大小（字节），52428800 = 50MB
- `allowedExtensions`: 允许的文件扩展名

## 使用方法

1. **修改配置文件**：
   - 打开 `config.json` 文件
   - 根据需要修改相应的配置项
   - 保存文件

2. **应用配置**：
   - 刷新浏览器页面，配置会自动加载
   - 如果配置文件不存在或加载失败，将使用内置的默认配置

3. **配置优先级**：
   - 浏览器localStorage中的配置 > 配置文件中的配置 > 默认配置
   - 在界面中保存的配置会优先于配置文件中的配置

## 注意事项

1. **JSON格式**：修改配置文件时请确保JSON格式正确，否则可能导致加载失败
2. **敏感信息**：不建议在配置文件中存储API密钥等敏感信息
3. **路径问题**：
   - **相对路径**：如 `"model/little_kid_stand.glb"`，路径相对于HTML文件所在目录
   - **绝对URL**：如 `"https://example.com/model.glb"`
   - **重要**：使用相对路径时，必须在Web服务器环境下运行（如使用 `http://localhost`），不能直接用 `file://` 协议打开，否则会因CORS限制无法加载
4. **文件大小**：模型文件不宜过大，建议小于10MB以获得更好的加载性能

## 示例

以下是一个完整的配置示例：

```json
{
  "api": {
    "url": "",
    "key": "",
    "appId": ""
  },
  "model": {
    "defaultModelUrl": "model/little_kid_stand.glb",
    "defaultPosition": { "x": 0, "y": 0, "z": 0 },
    "defaultRotation": { "x": 0, "y": 0, "z": 0 }
  },
  "modelLibrary": [
    {
      "name": "本地模型",
      "url": "model/little_kid_stand.glb",
      "description": "使用相对路径的本地模型",
      "jumpTo": -1
    },
    {
      "name": "在线模型",
      "url": "https://example.com/model.glb",
      "description": "使用绝对URL的在线模型",
      "jumpTo": 0
    }
  ],
  "textDisplay": {
    "speed": 30
  },
  "ui": {
    "title": "我的3D助手",
    "subtitle": "自定义副标题"
  }
}
```

## 故障排除

如果配置没有生效：

1. 检查浏览器控制台是否有错误信息
2. 确认 `config.json` 文件与HTML文件在同一目录
3. 检查JSON格式是否正确（可以使用JSON验证工具）
4. 清除浏览器缓存后重新加载页面

