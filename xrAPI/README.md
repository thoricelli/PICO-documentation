# PICO OpenXR API <!-- omit in toc -->

Content dumped from libpxrruntime.so, used by com.pico.xr.openxr_runtime

PICO's OpenXR runtime is documented [here](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/index.html).

OpenXR uses a function called xrGetInstanceProcAdrr, documented [here](https://registry.khronos.org/OpenXR/specs/1.0/man/html/xrGetInstanceProcAddr.html). <br>
Original source code from OpenXR for the xrGetInstanceProcAddr function is [here](https://github.com/KhronosGroup/OpenXR-SDK-Source/blob/d0bbcabc2a2e6565035ef3a68ec1f789a2dc9562/src/loader/loader_core.cpp#L715).

# Table of contents <!-- omit in toc -->

- [PICO Extensions](#pico-extensions)
- [PICO Specific XR functions](#pico-specific-xr-functions)
  - [Misc](#misc)
    - [xrLogSdkApiPICO](#xrlogsdkapipico)
    - [xrPerfSettingsSetPerformanceLevelEXT](#xrperfsettingssetperformancelevelext)
    - [xrPerfSettingsGetPerformanceLevelEXT](#xrperfsettingsgetperformancelevelext)
  - [Controller functionality (XR_PICO_android_controller_function_ext_enable)](#controller-functionality-xr_pico_android_controller_function_ext_enable)
    - [xrGetControllerSensorDataPredictPico](#xrgetcontrollersensordatapredictpico)
    - [xrSetEngineVersionPico](#xrsetengineversionpico)
    - [xrSetMainControllerHandlePico](#xrsetmaincontrollerhandlepico)
    - [xrGetMainControllerHandlePico](#xrgetmaincontrollerhandlepico)
    - [xrGetControllerConnectionStatePico](#xrgetcontrollerconnectionstatepico)
    - [xrGetPhyControllerInfoPico](#xrgetphycontrollerinfopico)
    - [xrGetPhyControllerTypePico](#xrgetphycontrollertypepico)
    - [xrVibrateControllerPico](#xrvibratecontrollerpico)
    - [xrVibrateControllerPico](#xrvibratecontrollerpico-1)
    - [xrSetPhyControllerEnterPairingPico](#xrsetphycontrollerenterpairingpico)
    - [xrSetPhyControllerStopPairingPico](#xrsetphycontrollerstoppairingpico)
    - [xrSetPhyControllerUpgradePico](#xrsetphycontrollerupgradepico)
    - [xrSetPhyControllerUnbindPico](#xrsetphycontrollerunbindpico)
    - [xrSetPhyControllerEnableKeyPico](#xrsetphycontrollerenablekeypico)
    - [xrSetVirtualKeyPico](#xrsetvirtualkeypico)
    - [xrStartPhyControllerVCMotorPico](#xrstartphycontrollervcmotorpico)
    - [xrStopPhyControllerVCMotorPico](#xrstopphycontrollervcmotorpico)
    - [xrSetControllerAmpPico](#xrsetcontrolleramppico)
    - [xrSetMotorDelayPico](#xrsetmotordelaypico)
    - [xrGetVibrateDelayTimePico](#xrgetvibratedelaytimepico)
    - [xrStartVibrateBySharemPico](#xrstartvibratebysharempico)
    - [xrGetVibrateSharemPico](#xrgetvibratesharempico)
    - [xrStartVibrateByPHFPico](#xrstartvibratebyphfpico)
    - [xrGetPHFSharedMemPico](#xrgetphfsharedmempico)
    - [xrPauseVibratePico](#xrpausevibratepico)
    - [xrResumeVibratePico](#xrresumevibratepico)
    - [xrReleaseControllerBufferPico](#xrreleasecontrollerbufferpico)
    - [xrStartVibrateByCachePico](#xrstartvibratebycachepico)
    - [xrClearVibrateByCachePico](#xrclearvibratebycachepico)
    - [xrSetAppHandTrackingEnabledPico](#xrsetapphandtrackingenabledpico)
    - [xrGetActiveInputDeviceTypePico](#xrgetactiveinputdevicetypepico)
    - [xrGetHandTrackingEnabledPico](#xrgethandtrackingenabledpico)
    - [xrGetHandTrackingHandStatePico](#xrgethandtrackinghandstatepico)
    - [xrGetHandTrackingSkeletonPico](#xrgethandtrackingskeletonpico)
  - [Controller interaction (XR_PICO_controller_interaction)](#controller-interaction-xr_pico_controller_interaction)
    - [xrGetHandTrackingMeshPico](#xrgethandtrackingmeshpico)
    - [xrGetControllerSensorDataPredictPICO](#xrgetcontrollersensordatapredictpico-1)
    - [xrSetControllerMainHandlePICO](#xrsetcontrollermainhandlepico)
    - [xrGetControllerMainHandlePICO](#xrgetcontrollermainhandlepico)
    - [xrGetControllerConnectionStatePICO](#xrgetcontrollerconnectionstatepico-1)
    - [xrGetControllerInfoPICO](#xrgetcontrollerinfopico)
    - [xrResetControllerPICO](#xrresetcontrollerpico)
    - [xrSetArmModelParametersPICO](#xrsetarmmodelparameterspico)
    - [xrGetControllerHandnessPICO](#xrgetcontrollerhandnesspico)
    - [xrGetControllerTypePICO](#xrgetcontrollertypepico)
    - [xrSetControllerVibratePICO](#xrsetcontrollervibratepico)
    - [xrSetControllerVibrateEventPICO](#xrsetcontrollervibrateeventpico)
    - [xrSetControllerEnterPairingPICO](#xrsetcontrollerenterpairingpico)
    - [xrSetControllerStopPairingPICO](#xrsetcontrollerstoppairingpico)
    - [xrSetControllerUpgradePICO](#xrsetcontrollerupgradepico)
    - [xrSetControllerUnbindPICO](#xrsetcontrollerunbindpico)
    - [xrSetControllerEnableKeyPICO](#xrsetcontrollerenablekeypico)
    - [xrCreateControllerClientPICO](#xrcreatecontrollerclientpico)
    - [xrUpdateVibrateParamsPICO](#xrupdatevibrateparamspico)
    - [xrCreateHapticStreamPICO](#xrcreatehapticstreampico)
    - [xrWriteHapticStreamPICO](#xrwritehapticstreampico)
    - [xrSetPHFHapticSpeedPICO](#xrsetphfhapticspeedpico)
    - [xrGetPHFHapticSpeedPICO](#xrgetphfhapticspeedpico)
    - [xrGetCurrentFrameSequencePICO](#xrgetcurrentframesequencepico)
    - [xrStartPHFHapticPICO](#xrstartphfhapticpico)
    - [xrStopPHFHapticPICO](#xrstopphfhapticpico)
    - [xrRemovePHFHapticPICO](#xrremovephfhapticpico)
    - [xrGetPHFStreamMemPICO](#xrgetphfstreammempico)
  - [Hand tracking (XR_PICO_hand_tracking)](#hand-tracking-xr_pico_hand_tracking)
    - [xrGetHandTrackerSettingStatePICO](#xrgethandtrackersettingstatepico)
    - [xrGetHandTrackerActiveInputTypePICO](#xrgethandtrackeractiveinputtypepico)
  - [Eye tracking (No extension)](#eye-tracking-no-extension)
    - [xrSetEyeTrackerModePICO](#xrseteyetrackermodepico)
    - [xrGetEyeTrackerModePICO](#xrgeteyetrackermodepico)
    - [xrGetEyeTrackerDataPICO](#xrgeteyetrackerdatapico)
  - [Body tracking (XR_PICO_body_tracking)](#body-tracking-xr_pico_body_tracking)
    - [xrSetBodyTrackerStaticCalibStatePICO](#xrsetbodytrackerstaticcalibstatepico)
    - [xrSetBodyTrackerModePICO](#xrsetbodytrackermodepico)
    - [xrGetBodyTrackerPosePICO](#xrgetbodytrackerposepico)
    - [xrGetBodyTrackerImuDataPICO](#xrgetbodytrackerimudatapico)
    - [xrGetBodyTrackerConnectStatePICO](#xrgetbodytrackerconnectstatepico)
    - [xrGetBodyTrackerBatteryPICO](#xrgetbodytrackerbatterypico)
    - [xrGetBodyTrackerCalibStatePICO](#xrgetbodytrackercalibstatepico)
    - [xrSetBodyTrackingAlgParamPICO](#xrsetbodytrackingalgparampico)
    - [xrCreateBodyTrackerBD](#xrcreatebodytrackerbd)
    - [xrDestroyBodyTrackerBD](#xrdestroybodytrackerbd)
    - [xrLocateBodyJointsBD](#xrlocatebodyjointsbd)
    - [xrStartBodyTrackingCalibAppBD](#xrstartbodytrackingcalibappbd)
    - [xrGetBodyTrackingStateBD](#xrgetbodytrackingstatebd)

# PICO Extensions

> Extensions are a method for runtimes or API layers to expose groups of functionality upon opt-in by the application. To help understand how OpenXR extensions are created and supported, this document describes the various processes for creating, supporting, promoting, and retiring extensions. <br> [Documentation](https://registry.khronos.org/OpenXR/specs/1.0/extprocess.html)

Extensions are to be passed when calling [`XrCreateInstance`](https://registry.khronos.org/OpenXR/specs/1.1/man/html/xrCreateInstance.html).

```
XR_BD_anchor_entity
XR_BD_anchor_entity_persistence
XR_BD_async_task
XR_BD_body_tracking
XR_BD_composition_layer_color_matrix
XR_BD_composition_layer_eac
XR_BD_composition_layer_settigs
XR_BD_controller_interaction
XR_BD_external_camera
XR_BD_human_occlusion_ext
XR_BD_motion_tracking
XR_BD_mr_management
XR_BD_room_scene
XR_BD_semi_auto_room_capture
XR_BD_spatial_anchor
XR_BD_spatial_anchor_persistence
XR_BD_spatial_localization_and_tracking
XR_BD_spatial_scene
XR_BD_spatial_tracking_state
XR_PICO_MetricsTool_ext
XR_PICO_android_controller_function_ext_enable
XR_PICO_body_tracking
XR_PICO_boundary
XR_PICO_configs_ext
XR_PICO_configuration
XR_PICO_controller_interaction
XR_PICO_eye_tracking
XR_PICO_frame_end
XR_PICO_frame_end_info_ext
XR_PICO_hand_tracking
XR_PICO_ipd
XR_PICO_mrc_pose
XR_PICO_mrc_pose_ext_enable
XR_PICO_passthrough
XR_PICO_performance_metrics
XR_PICO_reset_sensor
XR_PICO_view_frustum
XR_PICO_view_frustum_ext
XR_PICO_view_ipd
XR_PICO_view_state
XR_PICO_view_state_ext_enable
```

# PICO Specific XR functions

Written here are all the PICO specific XR extensions that I could find. <br>
For the original OpenXR header used by PICO see [here](./include_openXR/openxr_pico.h).

Note: External type refers to the name given to the function in libpxrplugin.so <br>
(PICO's library used by Unreal and Unity.)

## Misc

### xrLogSdkApiPICO

```c
xrLogSdkApiPICO
```

External name: Pxr_LogPluginApi <br>
Status: **To be RE'd.** <br>
Note: No source code available anywhere.

---

### xrPerfSettingsSetPerformanceLevelEXT

_Sets GPU or CPU performance level._

```c
XrResult xrPerfSettingsSetPerformanceLevelEXT(
    XrInstance instance,
    XrPerfSettingsDomainEXT domain,
    XrPerfSettingsLevelEXT level
);
```

| Parameter               | Description                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------ |
| XrPerfSettingsDomainEXT | CPU = 1 <br> GPU = 2                                                                                   |
| XrPerfSettingsLevelEXT  | The performance level<br />Saving = 0<br />Sustained low = 25<br />Sustained high = 50<br />Boost = 75 |

External name: Pxr_SetPerformanceLevels <br>
Status: [Documented by Khronos](https://registry.khronos.org/OpenXR/specs/1.0/man/html/xrPerfSettingsSetPerformanceLevelEXT.html) <br>

---

### xrPerfSettingsGetPerformanceLevelEXT

_Gets GPU or CPU performance level_

```c
XrResult xrPerfSettingsGetPerformanceLevelEXT(
    XrInstance instance,
    XrPerfSettingsDomainEXT domain,
    XrPerfSettingsLevelEXT level
);
```

| Parameter               | Description                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------ |
| XrPerfSettingsDomainEXT | CPU = 1 <br> GPU = 2                                                                                   |
| XrPerfSettingsLevelEXT  | The performance level<br />Saving = 0<br />Sustained low = 25<br />Sustained high = 50<br />Boost = 75 |

External name: Pxr_GetPerformanceLevels <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/de/d7f/_pxr_api_8h.html#a68478ea6f8a8e353e123ccc1e93822bf) <br>

---

## Controller functionality (XR_PICO_android_controller_function_ext_enable)

### xrGetControllerSensorDataPredictPico

_Not tested._

```c
XrResult xrGetControllerSensorDataPredictPico(
    XrInstance instance,
    int controllerHandle,
    float headSensorData[],
    float predictTime,
    float* data
):
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: getControllerSensorDataPredict <br>
Status: [Only available in header source code](./include_openXR/openxr_pico.h?plain=1#L847)

---

### xrSetEngineVersionPico

_Not tested_

```c
XrResult xrSetEngineVersionPico(
    XrInstance instance,
    const char* version
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetEngineVersionPico <br>
Status: [Only available in header source code](./include_openXR/openxr_pico.h?plain=1#L836) <br>
Note: Not made public through libpxrplugin.so.

---

### xrSetMainControllerHandlePico

_Sets the main controller_

```c
XrResult xrSetMainControllerHandlePico(
    XrInstance instance,
    int controllerHandle
);
```

| Parameter        | Description                                   |
| ---------------- | --------------------------------------------- |
| controllerHandle | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerMainInputHandle <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrsetmaincontrollerhandlepico)

---

### xrGetMainControllerHandlePico

_Gets the main controller_

```c
XrResult xrGetMainControllerHandlePico(
    XrInstance instance,
    int* controllerHandle
);
```

| Parameter        | Description                                   |
| ---------------- | --------------------------------------------- |
| controllerHandle | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetControllerMainInputHandle <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrgetmaincontrollerhandlepico-new)

---

### xrGetControllerConnectionStatePico

_Gets the connection status of the specified controller_

```c
XrResult xrGetControllerConnectionStatePico(
    XrInstance instance,
    uint8_t controllerhandle,
    uint8_t* status
);
```

| Parameter        | Description                                   |
| ---------------- | --------------------------------------------- |
| controllerHandle | Left controller = 0 <br> Right controller = 1 |
| status           | Disconnected = 0 <br> Connected = 1           |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetControllerConnectStatus <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrgetcontrollerconnectionstatepico)

---

### xrGetPhyControllerInfoPico

_Gets physical controller information_

```c
XrResult xrGetPhyControllerInfoPico(
    XrInstance instance,
    int device,
    XrControllerInfo* controllerinfo
);
```

| Parameter      | Description                                                   |
| -------------- | ------------------------------------------------------------- |
| device         | Left controller = 0 <br> Right controller = 1                 |
| controllerinfo | See [struct](./include_openXR/openxr_pico.h?plain=1#L11) here |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetControllerinfo <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrgetphycontrollerinfopico-new)

---

### xrGetPhyControllerTypePico

_Not tested_

```c
XrResult xrGetPhyControllerTypePico(
    XrInstance instance,
    int device,
    unkown_data_struct* controllerType
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: getControllerType <br>
Status: **To be RE'd**

---

### xrVibrateControllerPico

_Vibrates the specified controller for a specified strength and time_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrVibrateControllerPico(
    XrInstance instance,
    float strength,
    int time,
    int controllerHandle
);
```

| Parameter        | Description                                   |
| ---------------- | --------------------------------------------- |
| strength         | vibrate strength: 0 - 1                       |
| time             | time of vibration in MS                       |
| controllerHandle | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerVibration <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrvibratecontrollerpico)

---

### xrVibrateControllerPico

_Vibrates the specified controller for a specified frequency, strength and time._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrVibrateControllerPico(
    XrInstance instance,
    int device,
    int frequency,
    float strength,
    int time
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |
| frequency | vibration frequency: 50 - 500 Hz              |
| strength  | vibrate strength: 0 - 1                       |
| time      | time of vibration in MS                       |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerVibrationEvent <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_SetControllerVibrationEvent)

---

### xrSetPhyControllerEnterPairingPico

_Not tested_

```c
XrResult xrSetPhyControllerEnterPairingPico(
    XrInstance instance,
    int device
)
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerEnterPairing <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L488)

---

### xrSetPhyControllerStopPairingPico

_Not tested_

```c
XrResult xrSetPhyControllerStopPairingPico(
    XrInstance instance,
    int device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerStopPairing <br>
Status: [Only available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L861)

---

### xrSetPhyControllerUpgradePico

> [!CAUTION]
> Use with caution. <br> I am not responsible for bricked controllers.

_Not tested_

```c
XrResult xrSetPhyControllerUpgradePico(
    XrInstance instance,
    int devicetype,
    int rule,
    char* station_path_by_char,
    char* controller_path_by_char
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

**Parameters not documented**

External name: Pxr_SetControllerUpgrade <br>
Status: [Only available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L861)

---

### xrSetPhyControllerUnbindPico

_Not tested_

```c
XrResult xrSetPhyControllerUnbindPico(
    XrInstance instance,
    int device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerUnbind <br>
Status: [Only available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L863)

---

### xrSetPhyControllerEnableKeyPico

_Disables or enables a key on the specified controller_

```c
XrResult xrSetPhyControllerEnableKeyPico(
    XrInstance instance,
    bool isEnable,
    XrControllerKeyMap Key
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

| Parameter | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| isEnabled | Key blocked                                                           |
| Key       | [XrControllerKeyMap](./include_OpenXR/openxr_pico.h?plain=1#L19) enum |

External name: Pxr_SetControllerEnableKey <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrsetphycontrollerenablekeypico-new)

---

### xrSetVirtualKeyPico

```c
XrResult xrSetVirtualKeyPico(
    XrInstance instance,
    int param_2,
    int param_3,
    int param_4
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

Status: **To be RE'd**

---

### xrStartPhyControllerVCMotorPico

_Enables audio-based vibration through audio file path._

```c
XrResult xrStartPhyControllerVCMotorPico(
    XrInstance instance,
    char* file,
    EPICOXRVibrateController slot
);
```

| Parameter | Description                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------------- |
| file      | Audio file path                                                                                           |
| slot      | Which controller to vibrate with the audio <br> No = 0 <br> Left = 1 <br> Right = 2 <br> LeftAndRight = 3 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StartControllerVCMotor <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StartControllerVCMotor)

---

### xrStopPhyControllerVCMotorPico

```c
XrResult xrStopPhyControllerVCMotorPico(
    XrInstance instance,
    int clientId
);
```

| Parameter | Description                                                                                                                                                        |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| clientId  | a reserved parameter, set it to the sourceId returned by another vibration control API to stop the corresponding vibration, or set it to 0 to stop all vibrations. |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StopControllerVCMotor <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StopControllerVCMotor)

---

### xrSetControllerAmpPico

_Sets the amplitude of audio-based vibration. You can change the vibration amplitude during audio playback._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrSetControllerAmpPico(
    XrInstance instance,
    float mode
);
```

| Parameter | Description                                        |
| --------- | -------------------------------------------------- |
| device    | Vibration amplitude level. The range is 0.0 to 2.0 |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerAmp <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_SetControllerAmp)

---

### xrSetMotorDelayPico

_Not tested_

```c
XrResult xrSetMotorDelayPico(
    XrInstance instance,
    int delay
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerDelay <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L508)

---

### xrGetVibrateDelayTimePico

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetVibrateDelayTimePico(
    XrInstance instance,
    int* length
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetVibrateDelayTime <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L509)

---

### xrStartVibrateBySharemPico

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrStartVibrateBySharemPico(
    XrInstance instance,
    float* data,
    PxrVibrate_config* parameter,
    int* sourceId
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StartVibrateBySharemF and Pxr_StartVibrateBySharemU <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L510)

---

### xrGetVibrateSharemPico

```c
XrResult xrGetVibrateSharemPico(
    XrInstance instance,
    long param_2,
    int param3
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetVibrateSharem <br>
Status: **To be RE'd**

---

### xrStartVibrateByPHFPico

_Plays PHF vibration data._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrStartVibrateByPHFPico(
    XrInstance instance,
    char* data,
    int buffersize,
    int* sourceId,
    VibrateInfo vibrateInfo
);
```

**Conflicting documentation for parameters** <br>
Refer to [VibrateInfo](./include/PxrTypes.h?plain=1#L506) for the struct.

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StartVibrateByPHF <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StartVibrateByPHF)

---

### xrGetPHFSharedMemPico

```c
XrResult xrGetPHFSharedMemPico(
    XrInstance instance,
    long param_2,
    long param_3
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetPHFSharedMem <br>
Status: **To be RE'd**

---

### xrPauseVibratePico

_Pauses the PHF vibration data._

```c
XrResult xrPauseVibratePico(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_PauseVibrate <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_PauseVibrate)

---

### xrResumeVibratePico

_Resumes PHF vibration data._

```c
XrResult xrResumeVibratePico(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_ResumeVibrate <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_ResumeVibrate)

---

### xrReleaseControllerBufferPico

```c
XrResult xrReleaseControllerBufferPico(
    XrInstance instance
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_ReleaseControllerBuffer <br>
Status: **To be RE'd**

---

### xrStartVibrateByCachePico

_Plays the cached audio vibration data._

```c
XrResult xrStartVibrateByCachePico(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StartVibrateByCache <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StartVibrateByCache)

---

### xrClearVibrateByCachePico

_Clears the cached audio vibration data._

```c
XrResult xrClearVibrateByCachePico(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_ClearVibrateByCache <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_ClearVibrateByCache)

---

### xrSetAppHandTrackingEnabledPico

_Not tested_

```c
XrResult xrSetAppHandTrackingEnabledPico(
    XrInstance instance,
    bool handTrackingEnabled
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetAppHandTrackingEnabled <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L519)

---

### xrGetActiveInputDeviceTypePico

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetActiveInputDeviceTypePico(
    XrInstance instance,
    PxrHandType handId,
    int coordinateFlag,
    PxrHandState* handtrackHandState
);
```

**Parameters not documented** <br>
See [PxrHandType](./include/PxrInput.h?plain=1#L199) and [PxrHandState](./include/PxrInput.h?plain=1#L300)

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetActiveInputDeviceType <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L520)

---

### xrGetHandTrackingEnabledPico

_Not tested_

```c
XrResult xrGetHandTrackingEnabledPico(
    XrInstance instance,
    bool* handTrackingEnabled
);
```

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetHandTrackingEnabled <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L521)

---

### xrGetHandTrackingHandStatePico

_Not tested_

```c
XrResult xrGetHandTrackingHandStatePico(
    XrInstance instance,
    PxrHandType handId,
    int coordinateflag,
    PxrHandState* handtrackinghandState
);
```

**Parameters not documented** <br>
See [PxrHandType](./include/PxrInput.h?plain=1#L199) and [PxrHandState](./include/PxrInput.h?plain=1#L300)

> [!NOTE]
> Requires XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetHandTrackingHandState <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L522)

---

### xrGetHandTrackingSkeletonPico

_Not tested_

```c
XrResult xrGetHandTrackingSkeletonPico(
    XrInstance instance,
    PxrSkeletonType handtrackingSkeletonType,
    PxrSkeleton* handtrackSkeleton
);
```

**Parameters not documented** <br>
See [PxrSkeletonType](./include/PxrInput.h?plain=1#L204) and [PxrSkeleton](./include/PxrInput.h?plain=1#L328)

External name: Pxr_GetHandTrackingSkeleton <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L523)

---

## Controller interaction (XR_PICO_controller_interaction)

### xrGetHandTrackingMeshPico

_Not tested_

```c
XrResult xrGetHandTrackingMeshPico(
    XrInstance instance,
    PxrMeshType handtrackMeshType,
    PxrHandMesh* handtrackHandMesh
)
```

**Parameters not documented** <br>
See [PxrMeshType](./include/PxrInput.h?plain=1#L209) and [PxrHandMesh](./include/PxrInput.h?plain=1#L340)

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetHandTrackingMesh <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L524)

---

### xrGetControllerSensorDataPredictPICO

_Not tested_

```c
XrResult xrGetControllerSensorDataPredictPICO(
    XrInstance instance,
    int controllerHandle,
    float headSensorData[],
    float predictTime,
    float* data
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: getControllerSensorDataPredict <br>
Status: [Only available in header source code](./include_openXR/openxr_pico.h?plain=1#L847)

---

### xrSetControllerMainHandlePICO

_Sets the main controller._

```c
XrResult xrSetControllerMainHandlePICO(
    XrInstance instance,
    uint32_t device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerMainInputHandle <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a95cd83871aeee5ccb75f62dc7dea3b24)

---

### xrGetControllerMainHandlePICO

_Gets the main controller_

```c
XrResult xrGetControllerMainHandlePICO(
    XrInstance instance,
    uint32_t* device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetControllerMainInputHandle <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a12d599740d6397af7bd62a8927b4adb0)

---

### xrGetControllerConnectionStatePICO

_Gets the connection status of a controller_

```c
XrResult xrGetControllerConnectionStatePICO(
    XrInstance instance,
    uint8_t controllerHandle,
    uint8_t* status
);
```

| Parameter        | Description                                   |
| ---------------- | --------------------------------------------- |
| controllerHandle | Left controller = 0 <br> Right controller = 1 |
| status           | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetControllerConnectStatus <br>
Status: [Documented by PICO](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/chapter_six.html#xrgetcontrollerconnectionstatepico)

---

### xrGetControllerInfoPICO

_Gets the information about a specified controller._

```c
XrResult xrGetControllerInfoPICO(
    XrInstance instance,
    uint32_t device,
    PxrControllerInfo* info
);
```

| Parameter | Description                                                     |
| --------- | --------------------------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1                   |
| info      | Refer to [PxrControllerInfo](./include/PxrInput.h?plain=1#L186) |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetControllerinfo <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a9d51f251f137aefde686c5489765b2b7)

---

### xrResetControllerPICO

_Not tested_

```c
XrResult xrResetControllerPICO(
    XrInstance instance,
    uint32_t device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_ResetController <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2601)

---

### xrSetArmModelParametersPICO

_Not tested_

```c
XrResult xrSetArmModelParametersPICO(
    XrInstance instance,
    PxrGazeType gazeType,
    PxrArmModelType armmodelType,
    float elbowHeight,
    float elbowDepth,
    float pointerTiltAngle
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetArmModelParameters <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2604)

---

### xrGetControllerHandnessPICO

_Not tested_

```c
XrResult xrGetControllerHandnessPICO(
    XrInstance instance,
    int* handness
);
```

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetControllerHandness <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2604)

---

### xrGetControllerTypePICO

```c
XrResult xrGetControllerTypePICO(
    XrInstance instance,
    long param_2,
    int* param_3
);
```

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: getControllerType <br>
Status: **To be RE'd**

---

### xrSetControllerVibratePICO

_Sets vibration for a specified controller._

```c
XrResult xrSetControllerVibratePICO(
    XrInstance instance,
    uint32_t device,
    float strength,
    int time
);
```

| Parameter | Description                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1                                                                               |
| strength  | Vibration amplitude. The valid value ranges from 0.0f to 1.0f. The greater the value, the stronger the vibration amplitude. |
| time      | Vibration duration. The valid value ranges from 0 to 65535 (in milliseconds).                                               |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerVibration <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a29b92a99751ab8830d1b266ae5135fde)

---

### xrSetControllerVibrateEventPICO

_Vibrates the specified controller for a specified frequency, strength and time._

```c
XrResult xrSetControllerVibrateEventPICO(
    XrInstance instance,
    int device,
    int frequency,
    float strength,
    int time
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |
| frequency | vibration frequency: 50 - 500 Hz              |
| strength  | vibrate strength: 0 - 1                       |
| time      | time of vibration in MS                       |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerVibrationEvent <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_SetControllerVibrationEvent)

---

### xrSetControllerEnterPairingPICO

_Not tested_

```c
XrResult xrSetControllerEnterPairingPICO(
    XrInstance instance,
    uint32_t device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerEnterPairing <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a501fc44a5990f5b45f7bd0d3758cd61d)

---

### xrSetControllerStopPairingPICO

_Not tested_

```c
XrResult xrSetControllerStopPairingPICO(
    XrInstance instance,
    uint32_t device
);
```

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

External name: Pxr_SetControllerStopPairing <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#aaa8d98fa1a7b91589a31fcf2a7a671b7)

---

### xrSetControllerUpgradePICO

> [!CAUTION]
> Use with caution. <br> I am not responsible for bricked controllers.

_Not tested_

```c
XrResult xrSetControllerUpgradePICO(
    XrInstance instance,
    uint32_t device,
    int rule,
    char* station_path_by_char,
    char* controller_path_by_char
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerUpgrade <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#ad4405376f56f06ac2a73b18760efe84f)

---

### xrSetControllerUnbindPICO

_Not tested_

```c
XrResult xrSetControllerUnbindPICO(
    XrInstance instance,
    uint32_t device
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| device    | Left controller = 0 <br> Right controller = 1 |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerUnbind <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#ad0a4668857cf365ab008ba6b96a6a587)

---

### xrSetControllerEnableKeyPICO

_Enables/disables the specified controller key._

```c
XrResult xrSetControllerEnableKeyPICO(
    XrInstance instance,
    bool isEnable,
    PxrControllerKeyMap key
);
```

| Parameter | Description                                                      |
| --------- | ---------------------------------------------------------------- |
| isEnable  | Whether to enable/disable the specified key                      |
| key       | Refer to [PxrControllerKeyMap](./include/PxrInput.h?plain=1#L19) |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerEnableKey <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a75859deb3d1097a444ae985c926a218a)

---

### xrCreateControllerClientPICO

```c
XrResult xrCreateControllerClientPICO(
    XrInstance instance
);
```

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

Status: **To be RE'd**

---

### xrUpdateVibrateParamsPICO

_Dynamically modifies PHF and AudioClip vibration data._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
xrUpdateVibrateParamsPICO(
    XrInstance instance,
    int sourceId,
    EPICOXRVibrateController slot,
    EPICOXRChannelFlip slotConfig,
    float ampValue
);
```

| Parameter  | Description                                                                                               |
| ---------- | --------------------------------------------------------------------------------------------------------- |
| sourceId   | ID returned by another vibration control API.                                                             |
| slot       | Which controller to vibrate with the audio <br> No = 0 <br> Left = 1 <br> Right = 2 <br> LeftAndRight = 3 |
| slotconfig | Specifies whether to enable audio channel inversion. <br> No = 0 <br> Yes = 1                             |
| ampValue   | Vibration amplitude level. The range is 0.0 to 2.0.                                                       |

> [!NOTE]
> When slotConfig = 1, the left controller vibrates with the audio source from right soundtrack, and vice versa.

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_UpdateVibrateParams <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_UpdateVibrateParams)

---

### xrCreateHapticStreamPICO

_Creates a haptic stream._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrCreateHapticStreamPICO(
    XrInstance instance,
    char* PHFVersion,
    int frameDurationMS,
    int slot,
    int reversal,
    float amp,
    float speed,
    int* sourceId
);
```

| Parameter       | Description                                                                                               |
| --------------- | --------------------------------------------------------------------------------------------------------- |
| PHFVersion      | String, the version of the PHF ( PICO Haptic File).                                                       |
| frameDurationMS | Interval of each frame.                                                                                   |
| slot            | Which controller to vibrate with the audio <br> No = 0 <br> Left = 1 <br> Right = 2 <br> LeftAndRight = 3 |
| reversal        | Not used currently. Set to 0 by default.                                                                  |
| amp             | Vibration amplitude level. The range is 0.0 to 2.0                                                        |
| speed           | Speed of the haptic stream.                                                                               |
| sourceId        | returns a unique control ID for the corresponding vibration.                                              |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_CreateHapticStream <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_CreateHapticStream)

---

### xrWriteHapticStreamPICO

_Writes vibration data in the corresponding stream._

```c
XrResult xrWriteHapticStreamPICO(
    XrInstance instance,
    int sourceId,
    FPHFJsonData frames,
    int from,
    int numFrames
);
```

| Parameter | Description                                                      |
| --------- | ---------------------------------------------------------------- |
| sourceId  | ID returned by another vibration control API.                    |
| frames    | PHF data.                                                        |
| from      | Specifies from which element of the array to start sending from. |
| numFrames | Specifies how many elements to send.                             |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_WriteHapticStream <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_WriteHapticStream)

---

### xrSetPHFHapticSpeedPICO

_Sets the PHF haptic speed._

```c
XrResult xrSetPHFHapticSpeedPICO(
    XrInstance instance,
    int sourceId,
    float speed
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |
| speed     | Speed of the haptic stream.                   |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetPHFHapticSpeed <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_SetPHFHapticSpeed)

---

### xrGetPHFHapticSpeedPICO

```c
XrResult xrGetPHFHapticSpeedPICO(
    XrInstance instance,
    int sourceId,
    float* speed
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |
| speed     | Speed of the haptic stream.                   |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetPHFHapticSpeed <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_SetPHFHapticSpeed)

---

### xrGetCurrentFrameSequencePICO

_Removes PHF haptic._

```c
XrResult xrGetCurrentFrameSequencePICO(
    XrInstance instance,
    int sourceId,
    uint64_t* frameSequence
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetCurrentFrameSequence <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2666)

---

### xrStartPHFHapticPICO

_Starts PHF haptic._

```c
XrResult xrStartPHFHapticPICO(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_StartPHFHaptic <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StartPHFHaptic)

---

### xrStopPHFHapticPICO

_Stops PHF haptic._

```c
XrResult xrStopPHFHapticPICO(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_StopPHFHaptic <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_StopPHFHaptic)

---

### xrRemovePHFHapticPICO

_Removes PHF haptic._

```c
XrResult xrRemovePHFHapticPICO(
    XrInstance instance,
    int sourceId
);
```

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| sourceId  | ID returned by another vibration control API. |

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_RemovePHFHaptic <br>
Status: **To be RE'd**

---

### xrGetPHFStreamMemPICO

```c
xrGetPHFStreamMemPICO
```

> [!NOTE]
> Requires XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetPHFStreamMem <br>
Status: **To be RE'd**

---

## Hand tracking (XR_PICO_hand_tracking)

### xrGetHandTrackerSettingStatePICO

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetHandTrackerSettingStatePICO(
    XrInstance instance,
    bool* enable
);
```

> [!NOTE]
> Requires XR_PICO_hand_tracking extension to be enabled

External name: Pxr_GetHandTrackerSettingState <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L528)

---

### xrGetHandTrackerActiveInputTypePICO

_Not tested_

```c
XrResult xrGetHandTrackerActiveInputTypePICO(
    XrInstance instance,
    PxrActiveInputDeviceType* activeInputType
);
```

**Parameters not documented**

See [PxrActiveInputDeviceType](./include/PxrInput.h?plain=1#L529).

> [!NOTE]
> Requires XR_PICO_hand_tracking extension to be enabled

External name: Pxr_GetHandTrackerActiveInputType <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L529)

---

## Eye tracking (No extension)

### xrSetEyeTrackerModePICO

```c
XrResult xrSetEyeTrackerModePICO(
    XrInstance instance,
    int param_2 //Probably PxrTrackingModeFlags.
);
```

Status: **To be RE'd**

---

### xrGetEyeTrackerModePICO

```c
XrResult xrGetEyeTrackerModePICO(
    XrInstance instance,
    int param_2 //Probably PxrTrackingModeFlags.
);
```

Status: **To be RE'd**

---

### xrGetEyeTrackerDataPICO

```c
XrResult xrGetEyeTrackerDataPICO(
    XrInstance instance,
    long param_2,
    long param_3
);
```

Status: **To be RE'd**

---

## Body tracking (XR_PICO_body_tracking)

### xrSetBodyTrackerStaticCalibStatePICO

_Not tested_

```c
XrResult xrSetBodyTrackerStaticCalibStatePICO(
    XrInstance instance,
    int calibstate
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingStaticCalibState <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L550)

---

### xrSetBodyTrackerModePICO

_Not tested_

```c
XrResults xrSetBodyTrackerModePICO(
    XrInstance instance,
    int mode
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingMode <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2766C1-L2766C68)

---

### xrGetBodyTrackerPosePICO

_Gets data for all user joints._

```c
XrResult xrGetBodyTrackerPosePICO(
    XrInstance instance,
    PxrBodyTrackingResult* res
);
```

**Parameters not documented**

See [PxrBodyTrackingResult](./include/PxrInput.h?plain=1#L426).

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingPose <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L550)

---

### xrGetBodyTrackerImuDataPICO

_Not tested_

```c
XrResult xrGetBodyTrackerImuDataPICO(
    XrInstance instance,
    int deviceId,
    PxrBodyTrackingImu res
);
```

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingImuData <br>
Status: [Only available in header source code](./include/PxrInput.h?plain=1#L552)

---

### xrGetBodyTrackerConnectStatePICO

```c
XrResult xrGetBodyTrackerConnectStatePICO(
    XrInstance instance,
    bool trackerId,
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

Status: **To be RE'd**

---

### xrGetBodyTrackerBatteryPICO

_Not tested_

```c
XrResult xrGetBodyTrackerBatteryPICO(
    XrInstance instance,
    int trackerId,
    int* battery
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetFitnessBandBattery <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2772)

---

### xrGetBodyTrackerCalibStatePICO

_Not tested_

```c
XrResult xrGetBodyTrackerCalibStatePICO(
    XrInstance instance,
    int* calibrated
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetFitnessBandCalibState <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2775)

---

### xrSetBodyTrackingAlgParamPICO

_Not tested_

```c
XrResult xrSetBodyTrackingAlgParamPICO(
    XrInstance instance,
    BodyTrackingAlgParamType algParamType,
    BodyTrackingAlgParam* param
);
```

**Parameters not documented**

See [BodyTrackingAlgParamType](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L1581) and [BodyTrackingAlgParam](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L1587).

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingAlgParam <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2781)

---

### xrCreateBodyTrackerBD

```c
XrResult xrCreateBodyTrackerBD(
    XrInstance instance,
    int* param_2
    long* param_3
);
```

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

Status: **To be RE'd**

---

### xrDestroyBodyTrackerBD

```c
XrResult xrDestroyBodyTrackerBD(
    XrInstance instance,
);
```

Status: **To be RE'd**

---

### xrLocateBodyJointsBD

_Gets body tracking data._

```c
XrResult xrLocateBodyJointsBD(
    XrInstance instance,
    BodyTrackingGetDataInfo getInfo,
    BodyTrackingData data
);
```

**Parameters not documented**

See [BodyTrackingGetDataInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L644) and [BodyTrackingData](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L693).

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingData <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5412)

---

### xrStartBodyTrackingCalibAppBD

_Not tested_

```c
XrResult xrStartBodyTrackingCalibAppBD(
    XrInstance instance,
    char* calibFlagString,
    int calibMode
);
```

**Parameters not documented**

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_StartBodyTrackingCalibApp <br>
Status: [Only available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5400)

---

### xrGetBodyTrackingStateBD

_Gets the state of body tracking._

```c
XrResult xrGetBodyTrackingStateBD(
    XrInstance instance,
    bool* isTracking,
    BodyTrackingState state
);
```

| Parameter     | Description                                                                                                                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isTracking    | A bool that indicates whether body tracking is working                                                                                                                                                                        |
| trackingState | The body tracking state information. See [BodyTrackingState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L602). |

> [!NOTE]
> Requires XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingState <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#b87b2ff0)

---

```c
xrGetMotionTrackerConnectStateBD
```

External name: Pxr_GetMotionTrackerConnectState <br>
Status: **To be RE'd**

---

```c
xrGetMotionTrackerTypeBD
```

External name: Pxr_GetMotionTrackerType <br>
Status: **To be RE'd**

---

```c
xrGetMotionTrackerModeBD
```

External name: Pxr_GetMotionTrackerMode <br>
Status: **To be RE'd**

---

```c
xrGetMotionTrackerLocationsBD
```

External name: Pxr_GetMotionTrackerLocations <br>
Status: **To be RE'd**

---

```c
xrCheckMotionTrackerModeAndNumberBD
```

External name: Pxr_CheckMotionTrackerModeAndNumber <br>
Status: **To be RE'd**

---

```c
xrGetExtDevTrackerConnectStateBD
```

External name: Pxr_GetExtDevTrackerConnectState <br>
Status: **To be RE'd**

---

```c
xrSetExtDevTrackerMotorVibrateBD
```

External name: Pxr_SetExtDevTrackerMotorVibrate <br>
Status: **To be RE'd**

---

```c
xrSetExtDevTrackerPassDataStateBD
```

External name: Pxr_SetExtDevTrackerPassDataState <br>
Status: **To be RE'd**

---

```c
xrSetExtDevTrackerByPassDataBD
```

External name: Pxr_SetExtDevTrackerByPassData <br>
Status: **To be RE'd**

---

```c
xrGetExtDevTrackerByPassDataBD
```

External name: Pxr_GetExtDevTrackerByPassData <br>
Status: **To be RE'd**

---

```c
xrGetExtDevTrackerBatteryBD
```

External name: Pxr_GetExtDevTrackerKeyData <br>
Status: **To be RE'd**

---

```c
xrGetExtDevTrackerKeyDataBD
```

External name: Pxr_GetExtDevTrackerKeyData <br>
Status: **To be RE'd**

---

```c
xrSetIPDPICO
```

External name: Pxr_SetIPD <br>
Status: **To be RE'd**

---

```c
xrGetIPDPICO
```

External name: Pxr_GetIPD <br>
Status: **To be RE'd**

---

```c
xrSetTrackingIPDEnabledPICO
```

External name: Pxr_SetTrackingIPDEnabled <br>
Status: **To be RE'd**

---

```c
xrGetTrackingIPDEnabledPICO
```

External name: Pxr_GetTrackingIPDEnabled <br>
Status: **To be RE'd**

---

```c
xrGetEyeTrackingAutoIPDPICO
```

External name: Pxr_GetEyeTrackingAutoIPD <br>
Status: **To be RE'd**

---

```c
xrGetFrustumParametersPICO
```

External name: Pxr_GetFrustum <br>
Status: **To be RE'd**

---

```c
xrSetFrustumParametersPICO
```

External name: Pxr_SetFrustum <br>
Status: **To be RE'd**

---

```c
xrGetConfigPICO
```

External name: Pxr_GetConfig <br>
Status: **To be RE'd**

---

```c
xrSetConfigPICO
```

External name: Pxr_SetConfig <br>
Status: **To be RE'd**

---

```c
xrGetConfigsPICO
```

External name: Pxr_GetConfigs <br>
Status: **To be RE'd**

---

```c
xrSetConfigsPICO
```

External name: Pxr_SetConfigs <br>
Status: **To be RE'd**

---

```c
xrGetFoveationConfigPICO
```

External name: getFoveationConfig <br>
Status: **To be RE'd**

---

```c
xrGetMainClientInfoPICO
```

External name: Pxr_GetMainClientInfo <br>
Status: **To be RE'd**

---

```c
xrGetPerformanceInfoPICO
```

Status: **To be RE'd**

---

```c
xrResetSensorPICO
```

External name: Pxr_ResetSensor <br>
Status: **To be RE'd**

---

```c
xrSetTrackingModePICO
```

External name: Pxr_SetTrackingMode <br>
Status: **To be RE'd**

---

```c
xrStartFoveationPICO
```

Status: **To be RE'd**

---

```c
xrStopFoveationPICO
```

Status: **To be RE'd**

---

```c
xrGetEyeTrackingDataPICO
```

External name: Pxr_GetEyeTrackingData and Pxr_GetEyeTrackingData1 <br>
Status: **To be RE'd**

---

```c
xrGetTrackingModePICO
```

External name: Pxr_GetTrackingMode <br>
Status: **To be RE'd**

---

```c
xrGetFaceTrackingDataPICO
```

External name: Pxr_GetFaceTrackingState <br>
Status: **To be RE'd**

---

```c
xrGetEyeTrackingStatePICO
```

External name: Pxr_GetEyeTrackingState <br>
Status: **To be RE'd**

---

```c
xrGetFaceTrackingStatePICO
```

External name: Pxr_GetFaceTrackingState <br>
Status: **To be RE'd**

---

```c
xrGetPupilDistancePICO
```

External name: Pxr_GetPupilDistance <br>
Status: **To be RE'd**

---

```c
xrStartEyeTrackingPICO
```

External name: Pxr_StartEyeTracking <br>
Status: **To be RE'd**

---

```c
xrStopEyeTrackingPICO
```

External name: Pxr_StopEyeTracking <br>
Status: **To be RE'd**

---

```c
xrSetTrackingStatusPICO
```

External name: Pxr_SetTrackingStatus <br>
Status: **To be RE'd**

---

```c
xrGetEyeOpennessPICO
```

External name: Pxr_GetEyeOpenness <br>
Status: **To be RE'd**

---

```c
xrGetEyePupilInfoPICO
```

External name: Pxr_GetEyePupilInfo <br>
Status: **To be RE'd**

---

```c
xrGetPerEyePosePICO
```

External name: Pxr_GetPerEyePose <br>
Status: **To be RE'd**

---

```c
xrGetBlinkPICO
```

External name: Pxr_GetEyeBlink <br>
Status: **To be RE'd**

---

```c
xrSetControllerPositionPICO
```

External name: Pxr_SetControllerPosition <br>
Status: **To be RE'd**

---

```c
xrBoundaryTestNodePICO
```

External name: Pxr_BoundaryTestNode <br>
Status: **To be RE'd**

---

```c
xrBoundaryTestPointPICO
```

External name: Pxr_TestPointIsInBoundary <br>
Status: **To be RE'd**

---

```c
xrGetBoundaryGeometryPICO
```

External name: Pxr_GetBoundaryGeometry <br>
Status: **To be RE'd**

---

```c
xrGetBoundaryDimensionsPICO
```

External name: Pxr_GetBoundaryDimensions <br>
Status: **To be RE'd**

---

```c
xrGetSeeThroughDataPICO
```

External name: Pxr_GetSeeThroughData <br>
Status: **To be RE'd**

---

```c
xrInvokeFunctionsPICO
```

External name: Pxr_InvokeFunctions <br>
Status: **To be RE'd**

---

```c
xrStartMRModeBD
```

External name: Pxr_StartMRMode <br>
Status: **To be RE'd**

---

```c
xrStopMRModeBD
```

External name: Pxr_StopMRMode <br>
Status: **To be RE'd**

---

```c
xrStopSpatialRecognitionBD
```

External name: Pxr_StopSpatialRecognition <br>
Status: **To be RE'd**

---

```c
xrSetMrConfigurationBD
```

External name: Pxr_SetMrConfiguration <br>
Status: **To be RE'd**

---

```c
xrCreateSpatialAnchorSpaceBD
```

External name: Pxr_CreateSpatialAnchor <br>
Status: **To be RE'd**

---

```c
xrDestroySpatialAnchorBD
```

External name: Pxr_DestroySpatialAnchor <br>
Status: **To be RE'd**

---

```c
xrSetSpatialAnchorPropertyBD
```

External name: Pxr_SetSpatialAnchorProperty <br>
Status: **To be RE'd**

---

```c
xrGetSpatialAnchorPropertyBD
```

External name: Pxr_GetSpatialAnchorProperty <br>
Status: **To be RE'd**

---

```c
xrSetSpatialAnchorTagBD
```

External name: Pxr_SetSpatialAnchorTag <br>
Status: **To be RE'd**

---

```c
xrGetSpatialAnchorTagBD
```

External name: Pxr_GetSpatialAnchorTag <br>
Status: **To be RE'd**

---

```c
xrGetSpatialAnchorUuidBD
```

External name: Pxr_GetSpatialAnchorUuid <br>
Status: **To be RE'd**

---

```c
xrSaveSpatialAnchorBD
```

External name: Pxr_SaveSpatialAnchor <br>
Status: **To be RE'd**

---

```c
xrDeleteSpatialAnchorBD
```

External name: Pxr_DeleteSpatialAnchor <br>
Status: **To be RE'd**

---

```c
xrLoadSpatialAnchorByIdBD
```

External name: Pxr_LoadSpatialAnchorById <br>
Status: **To be RE'd**

---

```c
xrGetSpatialAnchorLoadResultsBD
```

External name: Pxr_GetSpatialAnchorLoadResults <br>
Status: **To be RE'd**

---

```c
xrExportSpatialInstanceBD
```

External name: Pxr_ExportSpatialInstance <br>
Status: **To be RE'd**

---

```c
xrImportSpatialInstanceBD
```

External name: Pxr_ImportSpatialInstance <br>
Status: **To be RE'd**

---

```c
xrStartRoomCaptureBD
```

External name: Pxr_StartRoomCapture <br>
Status: **To be RE'd**

---

```c
xrCreateRoomSceneDataBD
```

External name: Pxr_CreateRoomSceneData <br>
Status: **To be RE'd**

---

```c
xrDestroyRoomSceneDataBD
```

External name: Pxr_DestroyRoomSceneData <br>
Status: **To be RE'd**

---

```c
xrSaveRoomSceneDataBD
```

External name: Pxr_SaveRoomSceneData <br>
Status: **To be RE'd**

---

```c
xrStartHumanOcclusionBD
```

External name: Pxr_StartHumanOcclusion <br>
Status: **To be RE'd**

---

```c
xrAcquire_occlusion_infoBD
```

External name Pxr_AcquireMeshingInfo <br>
Status: **To be RE'd**

---

```c
xrStopHumanOcclusionBD
```

External name: Pxr_StopHumanOcclusion <br>
Status: **To be RE'd**

---

```c
xrGetMrcPosePICO
```

External name: Pxr_GetMrcPose <br>
Status: **To be RE'd**

---

```c
xrSetMrcPosePICO
```

External name: Pxr_SetMrcPose <br>
Status: **To be RE'd**

---

```c
xrSetIsSupportMovingMrcPICO
```

External name: Pxr_SetIsSupportMovingMrc <br>
Status: **To be RE'd**

---

```c
xrGetExternalCameraInfoBD
```

External name: Pxr_GetExternalCameraInfo <br>
Status: **To be RE'd**

---

```c
xrPassthroughLayerSetStylePICO
```

External name: Pxr_SetPassthroughStyle <br>
Status: **To be RE'd**

---

```c
xrCreateAnchorEntityBD
```

External name: Pxr_CreateAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrDestroyAnchorEntityBD
```

External name: Pxr_DestroyAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrCreateAnchorSpaceBD
```

External name: Pxr_CreateAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrGetAnchorEntityUuidBD
```

External name: Pxr_GetAnchorEntityUuid <br>
Status: **To be RE'd**

---

```c
xrAddAnchorComponentBD
```

External name: Pxr_AddAnchorComponent <br>
Status: **To be RE'd**

---

```c
xrRemoveAnchorComponentBD
```

External name: Pxr_RemoveAnchorComponent <br>
Status: **To be RE'd**

---

```c
xrGetAnchorComponentFlagsBD
```

External name: Pxr_GetAnchorComponentFlags <br>
Status: **To be RE'd**

---

```c
xrGetAnchorSceneLabelBD
```

External name: Pxr_GetAnchorSceneLabel <br>
Status: **To be RE'd**

---

```c
xrGetAnchorPlaneBoundaryInfoBD
```

External name: Pxr_GetAnchorPlaneBoundaryInfo <br>
Status: **To be RE'd**

---

```c
xrGetAnchorPlanePolygonInfoBD
```

External name: Pxr_GetAnchorPlanePolygonInfo <br>
Status: **To be RE'd**

---

```c
xrGetAnchorBoxInfoBD
```

External name: Pxr_GetAnchorBoxInfo <br>
Status: **To be RE'd**

---

```c
xrPersistAnchorEntityBD
```

External name: Pxr_PersistAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrUnpersistAnchorEntityBD
```

External name: Pxr_UnpersistAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrClearPersistedAnchorEntityBD
```

External name: Pxr_ClearPersistedAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrLoadAnchorEntityBD
```

External name: Pxr_LoadAnchorEntity <br>
Status: **To be RE'd**

---

```c
xrGetAnchorEntityLoadResultsBD
```

External name: Pxr_GetAnchorEntityLoadResults <br>
Status: **To be RE'd**

---

```c
xrStartSemiAutoRoomCaptureBD
```

External name: Pxr_StartSemiAutoRoomCapture <br>
Status: **To be RE'd**

---

```c
xrStopSemiAutoRoomCaptureBD
```

External name: Pxr_StopSemiAutoRoomCapture <br>
Status: **To be RE'd**

---

```c
xrSetFloorHeightBD
```

External name: Pxr_SetFloorHeight <br>
Status: **To be RE'd**

---

```c
xrSetCeilingHeightBD
```

External name: Pxr_SetCeilingHeight <br>
Status: **To be RE'd**

---

```c
xrSetFloorCornerBD
```

External name: Pxr_SetFloorCorner <br>
Status: **To be RE'd**

---

```c
xrGetSemiAutoRoomCaptureCandidatesBD
```

External name: Pxr_GetSemiAutoRoomCaptureCandidates <br>
Status: **To be RE'd**

---

```c
xrGetSpatialTrackingStateBD
```

External name: Pxr_GetSpatialTrackingState <br>
Status: **To be RE'd**

---

```c
xrBeginSpatialLocalizationBD
```

External name: Pxr_BeginSpatialLocalization <br>
Status: **To be RE'd**

---

```c
xrEndSpatialLocalizationBD
```

External name: Pxr_EndSpatialLocalization <br>
Status: **To be RE'd**

---

```c
xrBeginSpatialMapCreationBD
```

External name: Pxr_BeginSpatialMapCreation <br>
Status: **To be RE'd**

---

```c
xrEndSpatialMapCreationBD
```

External name: Pxr_EndSpatialMapCreation <br>
Status: **To be RE'd**

---

```c
xrStartSpatialSceneCaptureBD
```

External name: Pxr_StartSpatialSceneCapture <br>
Status: **To be RE'd**
