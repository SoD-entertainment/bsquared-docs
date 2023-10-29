# 🛑 **obs-websocket** [events](https://github.com/obsproject/obs-websocket/blob/master/docs/generated/protocol.md#enumerations-table-of-contents), [requests](https://github.com/obsproject/obs-websocket/blob/master/docs/generated/protocol.md#requests-table-of-contents) 🛑

## Scene Items

```bash
GetSceneItemEnabled
Gets the enable state of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
Response Fields:
sceneItemEnabled 	Boolean
```

```bash
SetSceneItemEnabled
Sets the enable state of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
sceneItemEnabled 	Boolean
```

```bash
GetSceneItemTransform
Gets the transform and crop info of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
Response Fields:
sceneItemTransform 	Object
```

```bash
SetSceneItemTransform
Sets the transform and crop info of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
sceneItemTransform 	Object
```

```bash
GetSceneItemBlendMode
Gets the blend mode of a scene item.
Blend modes:
    OBS_BLEND_NORMAL
    OBS_BLEND_ADDITIVE
    OBS_BLEND_SUBTRACT
    OBS_BLEND_SCREEN
    OBS_BLEND_MULTIPLY
    OBS_BLEND_LIGHTEN
    OBS_BLEND_DARKEN
Request Fields:
sceneName 	String
sceneItemId 	Number
Response Fields:
sceneItemBlendMode 	String
```

```bash
SetSceneItemBlendMode
Sets the blend mode of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
sceneItemBlendMode 	String
```

```bash
GetSceneItemLocked
Gets the lock state of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
Response Fields:
sceneItemLocked 	Boolean
```

```bash
SetSceneItemLocked
Sets the lock state of a scene item.
Request Fields:
sceneName 	String
sceneItemId 	Number
sceneItemLocked 	Boolean
```

---

## Input Requests

```bash
GetInputList
Gets an array of all inputs in OBS.
Request Fields:
?inputKind 	String
Response Fields:
inputs 	Array<Object>
```

```bash
GetInputSettings
Gets the settings of an input.
Request Fields:
inputName 	String
Response Fields:
inputSettings 	Object
inputKind 	String
```

```bash
SetInputSettings
Sets the settings of an input.
Request Fields:
inputName 	String
inputSettings 	Object
?overlay 	Boolean
	True == apply the settings on top of existing ones,
	False == reset the input to its defaults, then apply settings.
```

```bash
ToggleInputMute 👈👈👈
Toggles the audio mute state of an input.
Request Fields:
inputName 	String
Response Fields:
inputMuted 	Boolean
```

```bash
GetInputMute
Gets the audio mute state of an input.
Request Fields:
inputName 	String
Response Fields:
inputMuted 	Boolean
```

```bash
SetInputMute
Sets the audio mute state of an input.
Request Fields:
inputName 	String
inputMuted 	Boolean
```

```bash
GetInputVolume 👈👈👈
Gets the current volume setting of an input.
Request Fields:
inputName 	String
Response Fields:
inputVolumeMul 	Number
inputVolumeDb 	Number 👈👈👈
```

```bash
SetInputVolume 👈👈👈
Gets the current volume setting of an input.
Request Fields:
inputName 	String
?inputVolumeMul 	Number
?inputVolumeDb 	Number 👈👈👈
```
