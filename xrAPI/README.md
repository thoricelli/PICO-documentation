# PICO OpenXR API <!-- omit in toc -->

Content dumped from libpxrruntime.so, used by com.pico.xr.openxr\*runtime. <br>
Path: _/system/priv-app/XRRuntime/XRRuntime.apk/lib/arm64-v8a/libpxrruntime.so_

PICO's OpenXR runtime is documented [here](https://sdk.picovr.com/docs/OpenXRMobileSDKv2/en/index.html).

OpenXR uses a function called xrGetInstanceProcAdrr, documented [here](https://registry.khronos.org/OpenXR/specs/1.0/man/html/xrGetInstanceProcAddr.html). <br>
Original source code from OpenXR for the xrGetInstanceProcAddr function is [here](https://github.com/KhronosGroup/OpenXR-SDK-Source/blob/d0bbcabc2a2e6565035ef3a68ec1f789a2dc9562/src/loader/loader_core.cpp#L715).

# Table of contents <!-- omit in toc -->

- [PICO Extensions](#pico-extensions)
- [PICO Specific XR functions](#pico-specific-xr-functions)
  - [Logging](#logging)
    - [xrLogSdkApiPICO](#xrlogsdkapipico)
  - [Settings (XR_EXT_performance_settings)](#settings-xr_ext_performance_settings)
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
  - [Hand tracking (XR_PICO_android_controller_function_ext_enable and XR_PICO_hand_tracking)](#hand-tracking-xr_pico_android_controller_function_ext_enable-and-xr_pico_hand_tracking)
    - [xrGetHandTrackingEnabledPico](#xrgethandtrackingenabledpico)
    - [xrGetHandTrackingHandStatePico](#xrgethandtrackinghandstatepico)
    - [xrGetHandTrackingSkeletonPico](#xrgethandtrackingskeletonpico)
    - [xrGetHandTrackerSettingStatePICO](#xrgethandtrackersettingstatepico)
    - [xrGetHandTrackerActiveInputTypePICO](#xrgethandtrackeractiveinputtypepico)
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
  - [Motion tracking (XR_BD_motion_tracking)](#motion-tracking-xr_bd_motion_tracking)
    - [xrGetMotionTrackerConnectStateBD](#xrgetmotiontrackerconnectstatebd)
    - [xrGetMotionTrackerTypeBD](#xrgetmotiontrackertypebd)
    - [xrGetMotionTrackerModeBD](#xrgetmotiontrackermodebd)
    - [xrGetMotionTrackerLocationsBD](#xrgetmotiontrackerlocationsbd)
    - [xrCheckMotionTrackerModeAndNumberBD](#xrcheckmotiontrackermodeandnumberbd)
    - [xrGetExtDevTrackerConnectStateBD](#xrgetextdevtrackerconnectstatebd)
    - [xrSetExtDevTrackerMotorVibrateBD](#xrsetextdevtrackermotorvibratebd)
    - [xrSetExtDevTrackerPassDataStateBD](#xrsetextdevtrackerpassdatastatebd)
    - [xrSetExtDevTrackerByPassDataBD](#xrsetextdevtrackerbypassdatabd)
    - [xrGetExtDevTrackerByPassDataBD](#xrgetextdevtrackerbypassdatabd)
    - [xrGetExtDevTrackerBatteryBD](#xrgetextdevtrackerbatterybd)
    - [xrGetExtDevTrackerKeyDataBD](#xrgetextdevtrackerkeydatabd)
  - [IPD (XR_PICO_ipd or XR_PICO_view_ipd)](#ipd-xr_pico_ipd-or-xr_pico_view_ipd)
    - [xrSetIPDPICO](#xrsetipdpico)
    - [xrGetIPDPICO](#xrgetipdpico)
    - [xrSetTrackingIPDEnabledPICO](#xrsettrackingipdenabledpico)
    - [xrGetTrackingIPDEnabledPICO](#xrgettrackingipdenabledpico)
    - [xrGetEyeTrackingAutoIPDPICO](#xrgeteyetrackingautoipdpico)
  - [Frustum (XR_PICO_view_frustum or XR_PICO_view_frustum_ext)](#frustum-xr_pico_view_frustum-or-xr_pico_view_frustum_ext)
    - [xrGetFrustumParametersPICO](#xrgetfrustumparameterspico)
    - [xrSetFrustumParametersPICO](#xrsetfrustumparameterspico)
  - [Configs (XR_PICO_configuration or XR_PICO_configs_ext)](#configs-xr_pico_configuration-or-xr_pico_configs_ext)
    - [xrGetConfigPICO](#xrgetconfigpico)
    - [xrSetConfigPICO](#xrsetconfigpico)
    - [xrGetConfigsPICO](#xrgetconfigspico)
    - [xrSetConfigsPICO](#xrsetconfigspico)
  - [Foveation (XR_PICO_configuration or XR_PICO_configs_ext)](#foveation-xr_pico_configuration-or-xr_pico_configs_ext)
    - [xrGetFoveationConfigPICO](#xrgetfoveationconfigpico)
    - [xrGetMainClientInfoPICO](#xrgetmainclientinfopico)
    - [xrGetPerformanceInfoPICO](#xrgetperformanceinfopico)
    - [xrResetSensorPICO](#xrresetsensorpico)
  - [Eye \& Face tracking (XR_EXT_eye_gaze_interaction)](#eye--face-tracking-xr_ext_eye_gaze_interaction)
    - [xrSetTrackingModePICO](#xrsettrackingmodepico)
    - [xrStartFoveationPICO](#xrstartfoveationpico)
    - [xrStopFoveationPICO](#xrstopfoveationpico)
    - [xrSetEyeTrackerModePICO](#xrseteyetrackermodepico)
    - [xrGetEyeTrackerModePICO](#xrgeteyetrackermodepico)
    - [xrGetEyeTrackerDataPICO](#xrgeteyetrackerdatapico)
    - [xrGetEyeTrackingDataPICO](#xrgeteyetrackingdatapico)
    - [xrGetTrackingModePICO](#xrgettrackingmodepico)
    - [xrGetFaceTrackingDataPICO](#xrgetfacetrackingdatapico)
    - [xrGetEyeTrackingStatePICO](#xrgeteyetrackingstatepico)
    - [xrGetFaceTrackingStatePICO](#xrgetfacetrackingstatepico)
    - [xrGetPupilDistancePICO](#xrgetpupildistancepico)
    - [xrStartEyeTrackingPICO](#xrstarteyetrackingpico)
    - [xrStopEyeTrackingPICO](#xrstopeyetrackingpico)
    - [xrSetTrackingStatusPICO](#xrsettrackingstatuspico)
    - [xrGetEyeOpennessPICO](#xrgeteyeopennesspico)
    - [xrGetEyePupilInfoPICO](#xrgeteyepupilinfopico)
    - [xrGetPerEyePosePICO](#xrgetpereyeposepico)
    - [xrGetBlinkPICO](#xrgetblinkpico)
  - [Boundary (XR_PICO_boundary)](#boundary-xr_pico_boundary)
    - [xrSetControllerPositionPICO](#xrsetcontrollerpositionpico)
    - [xrBoundaryTestNodePICO](#xrboundarytestnodepico)
    - [xrBoundaryTestPointPICO](#xrboundarytestpointpico)
    - [xrGetBoundaryGeometryPICO](#xrgetboundarygeometrypico)
    - [xrGetBoundaryDimensionsPICO](#xrgetboundarydimensionspico)
    - [xrGetSeeThroughDataPICO](#xrgetseethroughdatapico)
    - [xrInvokeFunctionsPICO](#xrinvokefunctionspico)
  - [Mixed Reality (XR_BD_mr_management)](#mixed-reality-xr_bd_mr_management)
    - [xrStartMRModeBD](#xrstartmrmodebd)
    - [xrStopMRModeBD](#xrstopmrmodebd)
    - [xrStopSpatialRecognitionBD](#xrstopspatialrecognitionbd)
    - [xrSetMrConfigurationBD](#xrsetmrconfigurationbd)
  - [Spatial anchor (XR_BD_spatial_anchor and XR_BD_spatial_anchor)](#spatial-anchor-xr_bd_spatial_anchor-and-xr_bd_spatial_anchor)
    - [xrCreateSpatialAnchorSpaceBD](#xrcreatespatialanchorspacebd)
    - [xrDestroySpatialAnchorBD](#xrdestroyspatialanchorbd)
    - [xrSetSpatialAnchorPropertyBD](#xrsetspatialanchorpropertybd)
    - [xrGetSpatialAnchorPropertyBD](#xrgetspatialanchorpropertybd)
    - [xrSetSpatialAnchorTagBD](#xrsetspatialanchortagbd)
    - [xrGetSpatialAnchorTagBD](#xrgetspatialanchortagbd)
    - [xrGetSpatialAnchorUuidBD](#xrgetspatialanchoruuidbd)
    - [xrSaveSpatialAnchorBD](#xrsavespatialanchorbd)
    - [xrDeleteSpatialAnchorBD](#xrdeletespatialanchorbd)
    - [xrLoadSpatialAnchorByIdBD](#xrloadspatialanchorbyidbd)
    - [xrGetSpatialAnchorLoadResultsBD](#xrgetspatialanchorloadresultsbd)
    - [xrExportSpatialInstanceBD](#xrexportspatialinstancebd)
    - [xrImportSpatialInstanceBD](#xrimportspatialinstancebd)
  - [Room capturing (XR_BD_room_scene)](#room-capturing-xr_bd_room_scene)
    - [xrStartRoomCaptureBD](#xrstartroomcapturebd)
    - [xrCreateRoomSceneDataBD](#xrcreateroomscenedatabd)
    - [xrDestroyRoomSceneDataBD](#xrdestroyroomscenedatabd)
    - [xrSaveRoomSceneDataBD](#xrsaveroomscenedatabd)
    - [xrDeleteRoomSceneDataBD](#xrdeleteroomscenedatabd)
    - [xrGetRoomSceneLoadResultsBD](#xrgetroomsceneloadresultsbd)
    - [xrLoadRoomSceneBD](#xrloadroomscenebd)
  - [Human occlusion (XR_BD_human_occlusion_ext)](#human-occlusion-xr_bd_human_occlusion_ext)
    - [xrStartHumanOcclusionBD](#xrstarthumanocclusionbd)
    - [xrAcquire_occlusion_infoBD](#xracquire_occlusion_infobd)
    - [xrStopHumanOcclusionBD](#xrstophumanocclusionbd)
  - [Mixed Reality Capture (XR_PICO_mrc_pose_ext_enable or XR_PICO_mrc_pose)](#mixed-reality-capture-xr_pico_mrc_pose_ext_enable-or-xr_pico_mrc_pose)
    - [xrGetMrcPosePICO](#xrgetmrcposepico)
    - [xrSetMrcPosePICO](#xrsetmrcposepico)
    - [xrSetIsSupportMovingMrcPICO](#xrsetissupportmovingmrcpico)
  - [External camera (XR_BD_external_camera)](#external-camera-xr_bd_external_camera)
    - [xrGetExternalCameraInfoBD](#xrgetexternalcamerainfobd)
  - [Passthrough (XR_PICO_passthrough)](#passthrough-xr_pico_passthrough)
    - [xrPassthroughLayerSetStylePICO](#xrpassthroughlayersetstylepico)
  - [Anchor entity (XR_BD_anchor_entity)](#anchor-entity-xr_bd_anchor_entity)
    - [xrCreateAnchorEntityBD](#xrcreateanchorentitybd)
    - [xrDestroyAnchorEntityBD](#xrdestroyanchorentitybd)
    - [xrCreateAnchorSpaceBD](#xrcreateanchorspacebd)
    - [xrGetAnchorEntityUuidBD](#xrgetanchorentityuuidbd)
    - [xrAddAnchorComponentBD](#xraddanchorcomponentbd)
    - [xrRemoveAnchorComponentBD](#xrremoveanchorcomponentbd)
    - [xrGetAnchorComponentFlagsBD](#xrgetanchorcomponentflagsbd)
    - [xrGetAnchorSceneLabelBD](#xrgetanchorscenelabelbd)
    - [xrGetAnchorPlaneBoundaryInfoBD](#xrgetanchorplaneboundaryinfobd)
    - [xrGetAnchorPlanePolygonInfoBD](#xrgetanchorplanepolygoninfobd)
    - [xrGetAnchorBoxInfoBD](#xrgetanchorboxinfobd)
    - [xrPersistAnchorEntityBD](#xrpersistanchorentitybd)
    - [xrUnpersistAnchorEntityBD](#xrunpersistanchorentitybd)
    - [xrClearPersistedAnchorEntityBD](#xrclearpersistedanchorentitybd)
    - [xrLoadAnchorEntityBD](#xrloadanchorentitybd)
    - [xrGetAnchorEntityLoadResultsBD](#xrgetanchorentityloadresultsbd)
  - [Room capture and Spatial mapping (XR_BD_semi_auto_room_capture and XR_BD_spatial_localization_and_tracking)](#room-capture-and-spatial-mapping-xr_bd_semi_auto_room_capture-and-xr_bd_spatial_localization_and_tracking)
    - [xrStartSemiAutoRoomCaptureBD](#xrstartsemiautoroomcapturebd)
    - [xrStopSemiAutoRoomCaptureBD](#xrstopsemiautoroomcapturebd)
    - [xrSetFloorHeightBD](#xrsetfloorheightbd)
    - [xrSetCeilingHeightBD](#xrsetceilingheightbd)
    - [xrSetFloorCornerBD](#xrsetfloorcornerbd)
    - [xrGetSemiAutoRoomCaptureCandidatesBD](#xrgetsemiautoroomcapturecandidatesbd)
    - [xrGetSpatialTrackingStateBD](#xrgetspatialtrackingstatebd)
    - [xrBeginSpatialLocalizationBD](#xrbeginspatiallocalizationbd)
    - [xrEndSpatialLocalizationBD](#xrendspatiallocalizationbd)
    - [xrBeginSpatialMapCreationBD](#xrbeginspatialmapcreationbd)
    - [xrEndSpatialMapCreationBD](#xrendspatialmapcreationbd)
    - [Pxr_StartSpatialSceneCapture](#pxr_startspatialscenecapture)
  - [Functions from other vendors that are available](#functions-from-other-vendors-that-are-available)

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

## Logging

### xrLogSdkApiPICO

```c
XrResult xrLogSdkApiPICO(
    XrInstance instance,
    long param_2
);
```

External name: Pxr_LogPluginApi <br>
Status: **To be RE'd.** <br>

---

## Settings (XR_EXT_performance_settings)

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

> [!TIP]
> Requires the [XR_EXT_performance_settings](https://registry.khronos.org/OpenXR/specs/1.0/man/html/XR_EXT_performance_settings.html) extension to be enabled

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

> [!TIP]
> Requires the [XR_EXT_performance_settings](https://registry.khronos.org/OpenXR/specs/1.0/man/html/XR_EXT_performance_settings.html) extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: getControllerSensorDataPredict <br>
Status: [Available in header source code](./include_openXR/openxr_pico.h?plain=1#L847)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetEngineVersionPico <br>
Status: [Available in header source code](./include_openXR/openxr_pico.h?plain=1#L836) <br>
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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerEnterPairing <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L488)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerStopPairing <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L861)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

**Parameters not documented**

External name: Pxr_SetControllerUpgrade <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L861)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerUnbind <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L863)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetControllerDelay <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L508)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetVibrateDelayTime <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L509)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_StartVibrateBySharemF and Pxr_StartVibrateBySharemU <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L510)

---

### xrGetVibrateSharemPico

```c
XrResult xrGetVibrateSharemPico(
    XrInstance instance,
    long param_2,
    int param3
);
```

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_ResumeVibrate <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_Input/#PXR_ResumeVibrate)

---

### xrReleaseControllerBufferPico

```c
XrResult xrReleaseControllerBufferPico(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_SetAppHandTrackingEnabled <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L519)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetActiveInputDeviceType <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L520)

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetHandTrackingMesh <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L524)

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: getControllerSensorDataPredict <br>
Status: [Available in header source code](./include_openXR/openxr_pico.h?plain=1#L847)

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_ResetController <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2601)

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetArmModelParameters <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2604)

---

### xrGetControllerHandnessPICO

_Not tested_

```c
XrResult xrGetControllerHandnessPICO(
    XrInstance instance,
    int* handness
);
```

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetControllerHandness <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2604)

---

### xrGetControllerTypePICO

```c
XrResult xrGetControllerTypePICO(
    XrInstance instance,
    long param_2,
    int* param_3
);
```

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_SetControllerEnableKey <br>
Status: [Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/dd/d11/_pxr_input_8h.html#a75859deb3d1097a444ae985c926a218a)

---

### xrCreateControllerClientPICO

```c
XrResult xrCreateControllerClientPICO(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> When slotConfig = 1, the left controller vibrates with the audio source from right soundtrack, and vice versa.

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetCurrentFrameSequence <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2666)

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_RemovePHFHaptic <br>
Status: **To be RE'd**

---

### xrGetPHFStreamMemPICO

```c
xrGetPHFStreamMemPICO
```

> [!TIP]
> Requires the XR_PICO_controller_interaction extension to be enabled

External name: Pxr_GetPHFStreamMem <br>
Status: **To be RE'd**

---

## Hand tracking (XR_PICO_android_controller_function_ext_enable and XR_PICO_hand_tracking)

### xrGetHandTrackingEnabledPico

_Not tested_

```c
XrResult xrGetHandTrackingEnabledPico(
    XrInstance instance,
    bool* handTrackingEnabled
);
```

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetHandTrackingEnabled <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L521)

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

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetHandTrackingHandState <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L522)

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

**Parameters not documented**

See [PxrSkeletonType](./include/PxrInput.h?plain=1#L204) and [PxrSkeleton](./include/PxrInput.h?plain=1#L328)

> [!TIP]
> Requires the XR_PICO_android_controller_function_ext_enable extension to be enabled

External name: Pxr_GetHandTrackingSkeleton <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L523)

---

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

> [!TIP]
> Requires the XR_PICO_hand_tracking extension to be enabled

External name: Pxr_GetHandTrackerSettingState <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L528)

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

> [!TIP]
> Requires the XR_PICO_hand_tracking extension to be enabled

External name: Pxr_GetHandTrackerActiveInputType <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L529)

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingStaticCalibState <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L550)

---

### xrSetBodyTrackerModePICO

_Not tested_

```c
XrResult xrSetBodyTrackerModePICO(
    XrInstance instance,
    int mode
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingMode <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2766C1-L2766C68)

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingPose <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L550)

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingImuData <br>
Status: [Available in header source code](./include/PxrInput.h?plain=1#L552)

---

### xrGetBodyTrackerConnectStatePICO

```c
XrResult xrGetBodyTrackerConnectStatePICO(
    XrInstance instance,
    bool trackerId,
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetFitnessBandBattery <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2772)

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetFitnessBandCalibState <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2775)

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

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_SetBodyTrackingAlgParam <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2781)

---

### xrCreateBodyTrackerBD

```c
XrResult xrCreateBodyTrackerBD(
    XrInstance instance,
    int* param_2
    long* param_3
);
```

> [!TIP]
> Requires the XR_BD_body_tracking extension to be enabled

Status: **To be RE'd**

---

### xrDestroyBodyTrackerBD

```c
XrResult xrDestroyBodyTrackerBD(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_BD_body_tracking extension to be enabled

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

> [!TIP]
> Requires the XR_BD_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingData <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5412)

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

> [!TIP]
> Requires the XR_BD_body_tracking extension to be enabled
>
> External name: Pxr_StartBodyTrackingCalibApp <br>
> Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5400)

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

| Parameter  | Description                                                                                                                                                                                                                   |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isTracking | A bool that indicates whether body tracking is working                                                                                                                                                                        |
| state      | The body tracking state information. See [BodyTrackingState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L602). |

> [!TIP]
> Requires the XR_PICO_body_tracking extension to be enabled

External name: Pxr_GetBodyTrackingState <br>
Status: [Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#b87b2ff0)

---

## Motion tracking (XR_BD_motion_tracking)

### xrGetMotionTrackerConnectStateBD

_Not tested_

```c
XrResult xrGetMotionTrackerConnectStateBD(
    XrInstance instance,
    MotionTrackerType trackerType
);
```

**Parameters not documented**

See [MotionTrackerType](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L714).

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetMotionTrackerConnectState <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5523)

---

### xrGetMotionTrackerTypeBD

_Not tested_

```c
XrResult xrGetMotionTrackerTypeBD(
    XrInstance instance,
    MotionTrackerType trackerType
);
```

**Parameters not documented**

See [MotionTrackerType](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L714).

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetMotionTrackerType <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5523)

---

### xrGetMotionTrackerModeBD

_Not tested_

```c
XrResult xrGetMotionTrackerModeBD(
    XrInstance instance,
    MotionTrackerMode trackerMode
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

See [MotionTrackerMode](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L723).

External name: Pxr_GetMotionTrackerMode <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5527)

---

### xrGetMotionTrackerLocationsBD

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetMotionTrackerLocationsBD(
    XrInstance instance,
    float worldToMetersScale,
    char* trackerSN,
    MotionTrackerLocations* locations,
    MotionTrackerConfidence confidence
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetMotionTrackerLocations <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#a18688d1)

---

### xrCheckMotionTrackerModeAndNumberBD

_Not tested_

```c
XrResult xrCheckMotionTrackerModeAndNumberBD(
    XrInstance instance,
    MotionTrackerMode trackerType,
    int trackerNumber
);
```

| Parameter     | Description                                                                                                                                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| trackerType   | Desired tracking mode. See [MotionTrackerMode](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L723). |
| trackerNumber | Desired number of tracker, value range:[0,3].                                                                                                                                                                   |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_CheckMotionTrackerModeAndNumber <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#a18688d1)

---

### xrGetExtDevTrackerConnectStateBD

_Gets the connect state of externally developed trackers._

```c
XrResult xrGetExtDevTrackerConnectStateBD(
    XrInstance instance,
    ExtDevTrackerConnectState connectState
);
```

| Parameter    | Description                                                                                                                                                                                                                                          |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| connectState | The connect state of externally developed trackers. See [ExtDevTrackerConnectState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L838). |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetExtDevTrackerConnectState <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#ebdd731c)

---

### xrSetExtDevTrackerMotorVibrateBD

_Sets the viberation of externally developed trackers._

```c
XrResult xrSetExtDevTrackerMotorVibrateBD(
    XrInstance instance,
    ExtDevTrackerMotorVibrate* motorVibrate
);
```

| Parameter    | Description                                                                                                                                                                                                                 |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| motorVibrate | Spread spectrum vibration. See [ExtDevTrackerConnectState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L849). |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_SetExtDevTrackerMotorVibrate <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#0a2f6710)

---

### xrSetExtDevTrackerPassDataStateBD

_Sets the pass data state of externally developed trackers._

```c
bool xrSetExtDevTrackerPassDataStateBD(
    XrInstance instance,
    bool state
);
```

**Parameters not documented**

Returns

| Type | Return value                                               |
| ---- | ---------------------------------------------------------- |
| bool | True: Pass data is enabled <br> False: Pass data is closed |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_SetExtDevTrackerPassDataState <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#01ee7cde)

---

### xrSetExtDevTrackerByPassDataBD

_Sets the externally developed trackers by pass data._

```c
XrResult xrSetExtDevTrackerByPassDataBD(
    XrInstance instance,
    ExtDevTrackerPassData* passData
);
```

| Parameter | Description                                                                                                                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| passData  | Pass data. See [ExtDevTrackerPassData](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L863). |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_SetExtDevTrackerByPassData <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#e642f2c3)

---

### xrGetExtDevTrackerByPassDataBD

_Gets the externally developed trackers by pass data._

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetExtDevTrackerByPassDataBD(
    XrInstance instance,
    ExtDevTrackerPassData[] passDatas,
    int* realLength
);
```

| Parameter | Description                                                                                                                                                                                                      |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| passDatas | Array of pass data. See [ExtDevTrackerPassData](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L863). |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetExtDevTrackerByPassData <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#1a6cbf5c)

---

### xrGetExtDevTrackerBatteryBD

_Gets the externally developed trackers' battery._

```c
XrResult xrGetExtDevTrackerBatteryBD(
    XrInstance instance,
    char* trackerSN,
    int* out_battery,
    int* out_charger
);
```

| Parameter   | Description                                                                   |
| ----------- | ----------------------------------------------------------------------------- |
| trackerSN   | SN of externally developed trackers.                                          |
| out_battery | Battery of externally developed trackers, value range: [0-10].                |
| out_charger | Whether the tracker is on charging, 0 for not on charging, 1 for on charging. |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetExtDevTrackerBattery <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#956217e2)

---

### xrGetExtDevTrackerKeyDataBD

_Gets the key data of externally developed trackers._

```c
XrResult xrGetExtDevTrackerKeyDataBD(
    XrInstance instance,
    char* trackerSN,
    ExtDevTrackerKeyData keyData
);
```

| Parameter | Description                                                                                                                                                                                                           |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| keyData   | Key data of the trackers. See [ExtDevTrackerKeyData](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L907). |

> [!TIP]
> Requires the XR_BD_motion_tracking extension to be enabled

External name: Pxr_GetExtDevTrackerKeyData <br>
Status: [Documented by PICO.](https://developer.picoxr.com/reference/unreal/client-api/PXR_HandTracking/#befd7127)

---

## IPD (XR_PICO_ipd or XR_PICO_view_ipd)

### xrSetIPDPICO

_Not tested_

> [!CAUTION]
> Be careful when setting the IPD with motorized lenses.

```c
XrResult xrSetIPDPICO(
    XrInstance instance,
    float ipd
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_ipd or XR_PICO_view_ipd extension to be enabled

External name: Pxr_SetIPD <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L261)

---

### xrGetIPDPICO

_Gets the interpupillary distance (IPD) of the current device._

```c
XrResult xrGetIPDPICO(
    XrInstance instance,
    float* ipd.
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_ipd or XR_PICO_view_ipd extension to be enabled

External name: Pxr_GetIPD <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L262)

---

### xrSetTrackingIPDEnabledPICO

_Not tested_

```c
XrResult xrSetTrackingIPDEnabledPICO(
    XrInstance instance,
    bool enable
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_ipd or XR_PICO_view_ipd extension to be enabled

External name: Pxr_SetTrackingIPDEnabled <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L263)

---

### xrGetTrackingIPDEnabledPICO

_Not tested_

```c
XrResult xrGetTrackingIPDEnabledPICO(
    XrInstance instance,
    bool* enabled
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_ipd or XR_PICO_view_ipd extension to be enabled

External name: Pxr_GetTrackingIPDEnabled <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L264)

---

### xrGetEyeTrackingAutoIPDPICO

_Not tested_

```c
XrResult xrGetEyeTrackingAutoIPDPICO(
    XrInstance instance,
    float* autoIPD
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_ipd or XR_PICO_view_ipd extension to be enabled

External name: Pxr_GetEyeTrackingAutoIPD <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L265)

---

## Frustum (XR_PICO_view_frustum or XR_PICO_view_frustum_ext)

### xrGetFrustumParametersPICO

_Not tested_

```c
XrResult xrGetFrustumParametersPICO(
    XrInstance instance,
    XrViewFrustum *pLeftFrustum,
    XrViewFrustum *pRightFrustum
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_view_frustum or XR_PICO_view_frustum_ext extension to be enabled

See [XrViewFrustum](./include/PxrEnums.h?plain=1#L78).

External name: Pxr_GetFrustum <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L265)

---

### xrSetFrustumParametersPICO

_Not tested_

```c
XrResult xrSetFrustumParametersPICO(
    XrInstance instance,
    XrViewFrustum *pLeftFrustum,
    XrViewFrustum *pRightFrustum
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_view_frustum or XR_PICO_view_frustum_ext extension to be enabled

External name: Pxr_SetFrustum <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L324)

---

## Configs (XR_PICO_configuration or XR_PICO_configs_ext)

### xrGetConfigPICO

_Not tested_

```c
XrResult xrGetConfigPICO(
    XrInstance instance,
    ConfigsEXT configIndex,
    float* configData
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_configuration or XR_PICO_configs_ext extension to be enabled

See [ConfigsEXT](./include_OpenXR/openxr_pico.h?plain=1#L347) or [PxrConfigType](./include/PxrEnums.h?plain=1#L112).

External name: Pxr_GetConfig <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L406)

---

### xrSetConfigPICO

_Not tested_

```c
XrResult xrSetConfigPICO(
    XrInstance instance,
    ConfigsSetEXT configIndex,
    char* configData
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_configuration or XR_PICO_configs_ext extension to be enabled

See [ConfigsEXT](./include_OpenXR/openxr_pico.h?plain=1#L370) or [PxrConfigType](./include/PxrEnums.h?plain=1#L112).

External name: Pxr_SetConfig <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L415)

---

### xrGetConfigsPICO

_Not tested_

```c
XrResult xrGetConfigsPICO(
    XrInstance instance,
    int* configCount,
    float[]* configArray
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_configuration or XR_PICO_configs_ext extension to be enabled

External name: Pxr_GetConfigs <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L411)

---

### xrSetConfigsPICO

_Not tested_

```c
XrResult xrSetConfigsPICO(
    XrInstance instance,
    ConfigsSetPICO* configsData
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_configuration or XR_PICO_configs_ext extension to be enabled

See [ConfigsSetPICO](./include_OpenXR/openxr_pico.h?plain=1#L395).

External name: Pxr_SetConfigs <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L419)

---

## Foveation (XR_PICO_configuration or XR_PICO_configs_ext)

### xrGetFoveationConfigPICO

_Not tested_

```c
XrResult xrGetFoveationConfigPICO(
    XrInstance instance,
    XrFoveationLevel level,
    float* gainX,
    float* gainY,
    float* area,
    float* minimum
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_configuration or XR_PICO_configs_ext extension to be enabled

See [XrFoveationLevel](./include_OpenXR/openxr_pico.h?plain=1#L225).

External name: getFoveationConfig <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L419)

---

### xrGetMainClientInfoPICO

```c
XrResult xrGetMainClientInfoPICO(
    XrInstance instance,
    long* param_2
);
```

> [!TIP]
> Requires the XR_PICO_MetricsTool_ext extension to be enabled

External name: Pxr_GetMainClientInfo <br>
Status: **To be RE'd**

---

### xrGetPerformanceInfoPICO

```c
XrResult xrGetPerformanceInfoPICO(
    XrInstance instance,
    long* param_2
);
```

> [!TIP]
> Requires the XR_PICO_performance_metrics extension to be enabled

Status: **To be RE'd**

---

### xrResetSensorPICO

_Not tested_

```c
XrResult xrResetSensorPICO(
    XrInstance instance,
    XrResetSensorOption option
);
```

**Parameters not documented**

See [XrResetSensorOption](./include_OpenXR/openxr_pico.h?plain=1#L461).

> [!TIP]
> Requires the XR_PICO_reset_sensor extension to be enabled

External name: Pxr_ResetSensor <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L468)

---

## Eye & Face tracking (XR_EXT_eye_gaze_interaction)

### xrSetTrackingModePICO

_Not tested_

```c
XrResult xrSetTrackingModePICO(
    XrInstance instance,
    uint32_t trackingMode
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_SetTrackingMode <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L185)

---

### xrStartFoveationPICO

```c
XrResult xrStartFoveationPICO(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

Status: **To be RE'd**

---

### xrStopFoveationPICO

```c
XrResult xrStopFoveationPICO(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

Status: **To be RE'd**

---

### xrSetEyeTrackerModePICO

```c
XrResult xrSetEyeTrackerModePICO(
    XrInstance instance,
    int param_2 //Probably PxrTrackingModeFlags.
);
```

> [!TIP]
> Requires the XR_PICO_eye_tracking extension to be enabled

Status: **To be RE'd**

---

### xrGetEyeTrackerModePICO

```c
XrResult xrGetEyeTrackerModePICO(
    XrInstance instance,
    int param_2 //Probably PxrTrackingModeFlags.
);
```

> [!TIP]
> Requires the XR_PICO_eye_tracking extension to be enabled

Status: **To be RE'd**

---

### xrGetEyeTrackerDataPICO

```c
XrResult xrGetEyeTrackerDataPICO(
    XrInstance instance,
    long timestamp,
    EyeTrackerData* EyeTrackerData
);
```

**Parameters not documented**

See [EyeTrackerData (EyeTrackingData)](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L239).

> [!NOTE]
> The EyeTrackingData struct has an extra value: The timestamp.
>
> ```
> EyeTrackingData {
>   long timestamp
>   int32_t leftEyePoseStatus
>   ...
> }
> ```

> [!TIP]
> Requires the XR_PICO_eye_tracking extension to be enabled

---

### xrGetEyeTrackingDataPICO

Tested

```c
XrResult xrGetEyeTrackingDataPICO(
    XrInstance instance,
    flags flags,
    EyeTrackingData* eyeTrackingData
);
```

**Parameters not documented**

See [EyeTrackingDataGetInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L97).

See [EyeTrackingData](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L239).

> [!NOTE]
> The EyeTrackingData struct has an extra value: The timestamp.
>
> ```
> EyeTrackingData {
>   long timestamp
>   int32_t leftEyePoseStatus
>   ...
> }
> ```

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetEyeTrackingData and Pxr_GetEyeTrackingData1 <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L188)

---

### xrGetTrackingModePICO

_Not tested_

```c
XrResult xrGetTrackingModePICO(
    XrInstance instance,
    uint32_t* trackingMode
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetTrackingMode <br>
Status: [Available in header source code](./include_OpenXR/openxr_pico.h?plain=1#L186)

---

### xrGetFaceTrackingDataPICO

_Not tested_

```c
XrResult xrGetFaceTrackingDataPICO(
    XrInstance instance,
    int64_t ts,
    int flags,
    PxrFTInfo* data
);
```

**Parameters not documented**

See [PxrFTInfo](./include/PxrTypes.h?plain=1#L492).

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetFaceTrackingData <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L91)

---

### xrGetEyeTrackingStatePICO

_Not tested_

```c
XrResult xrGetEyeTrackingStatePICO(
    XrInstance instance,
    bool* isTracking,
    EyeTrackingState* state
);
```

**Parameters not documented**

See [EyeTrackingState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L156).

> [!TIP]
> Requires the XR_PICO_eye_tracking extension to be enabled

External name: Pxr_GetEyeTrackingState <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5166)

---

### xrGetFaceTrackingStatePICO

_Not tested_

```c
XrResult xrGetFaceTrackingStatePICO(
    XrInstance instance,
    bool* isTracking,
    FaceTrackingState state*
);
```

**Parameters not documented**

See [FaceTrackingState](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L455).

> [!TIP]
> Requires the XR_PICO_eye_tracking extension to be enabled

External name: Pxr_GetFaceTrackingState <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5316)

---

### xrGetPupilDistancePICO

_Not tested_

```c
XrResult xrGetPupilDistancePICO(
    XrInstance instance,
    float* ipd
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetPupilDistance <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L92)

---

### xrStartEyeTrackingPICO

_Not tested_

```c
XrResult xrStartEyeTrackingPICO(
    XrInstance instance,
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_StartEyeTracking <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L93)

---

### xrStopEyeTrackingPICO

_Not tested_

```c
XrResult xrStopEyeTrackingPICO(
    XrInstance instance,
    int mode
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_StopEyeTracking <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L94)

---

### xrSetTrackingStatusPICO

_Not tested_

```c
XrResult xrSetTrackingStatusPICO(
    XrInstance instance,
    char* key,
    char* value
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_SetTrackingStatus <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2753)

---

### xrGetEyeOpennessPICO

_Not tested_

```c
XrResult xrGetEyeOpennessPICO(
    XrInstance instance,
    float* leftEyeOpenness,
    float* rightEyeOpeness
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetEyeOpenness <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5170)

---

### xrGetEyePupilInfoPICO

_Not tested_

> [!IMPORTANT]
> This function [does not work](https://www.reddit.com/r/virtualreality/comments/1cyn329/pico_4_enterprise/), and only returns empty values.

```c
XrResult xrGetEyePupilInfoPICO(
    XrInstance instance,
    EyePupilInfo eyePupilPosition
);
```

**Parameters not documented**

See [EyePupilInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_MotionTracking.cs#L258).

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetEyePupilInfo <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5172)

---

### xrGetPerEyePosePICO

_Not tested_

```c
XrResult xrGetPerEyePosePICO(
    XrInstance instance,
    long* timestamp,
    Posef* leftEyePose,
    Posef* rightEyePose
);
```

**Parameters not documented**

See [Posef](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/Features/PXR_HandTracking.cs#L84).

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetPerEyePose <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5174)

---

### xrGetBlinkPICO

_Not tested_

> [!NOTE]
> This function [does not work](https://www.reddit.com/r/virtualreality/comments/1cyn329/pico_4_enterprise/), and only returns empty values.

```c
XrResult xrGetBlinkPICO(
    XrInstance instance,
    long* timestamp,
    bool* isLeftBlink,
    bool* isRightBlink
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_EXT_eye_gaze_interaction extension to be enabled

External name: Pxr_GetEyeBlink <br>
Status: [Available in external source code.](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L5176)

---

## Boundary (XR_PICO_boundary)

### xrSetControllerPositionPICO

_Not tested_

```c
XrResult xrSetControllerPositionPICO(
    XrInstance instance,
    float x,
    float y,
    float z,
    float w,
    float px,
    float py,
    float pz,
    int hand,
    bool valid,
    int keyEvent
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_SetControllerPosition <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L563)

---

### xrBoundaryTestNodePICO

_Not tested_

```c
XrResult xrBoundaryTestNodePICO(
    XrInstance instance,
    int node,
    bool isPlayArea,
    bool* pisTriggering,
    float* pclosestDistance,
    float* ppx,
    float* ppy,
    float* ppz,
    float* pnx,
    float* pny,
    float* pnz,
    int* ret
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_BoundaryTestNode <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L576)

---

### xrBoundaryTestPointPICO

_Checks whether a tracked point in the coordinate system will trigger the boundary._

```c
XrResult xrBoundaryTestPointPICO(
    XrInstance instance,
    float x,
    float y,
    float z,
    bool isPlayArea,
    bool* pisTriggering,
    float* pclosestDistance,
    float* ppx,
    float* ppy,
    float* ppz,
    float* pnx,
    float* pny,
    float* pnz,
    int* ret
);
```

**Parameters conflict with documentation**

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_TestPointIsInBoundary <br>
Status: <br>
[Available in header source code](./include/PxrPlugin.h?plain=1#L590) <br>
[Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/de/d7f/_pxr_api_8h.html#a72a2411e7c4679e933d41e11e29049c5)

---

### xrGetBoundaryGeometryPICO

_Gets the collection of boundary points._

```c
XrResult xrGetBoundaryGeometryPICO(
    XrInstance instance,
    float[]* outPointsFloat,
    bool isPlayArea,
    int* ret
);
```

| Parameter      | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| outPointsFloat | The points acquired.                                                                                                  |
| isPlayArea     | Whether it is an internal rectangular area. <br> true: internal rectangular area <br> false: external custom boundary |

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_GetBoundaryGeometry2 <br>
Status: <br>
[Available in header source code](./include/PxrPlugin.h?plain=1#L606) <br>
[Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/de/d7f/_pxr_api_8h.html#a19d3de546d3fdead4fc29d9a2ce0592c)

---

### xrGetBoundaryDimensionsPICO

_Not tested_

```c
XrResult xrGetBoundaryDimensionsPICO(
    XrInstance instance,
    float* x,
    float* y,
    float* z,
    bool isPlayArea,
    int* ret
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_GetBoundaryDimensions <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L612)

---

### xrGetSeeThroughDataPICO

_Not tested_

```c
XrResult xrGetSeeThroughDataPICO(
    XrInstance instance,
    uint8_t* leftEye,
    uint8_t* rightEye,
    uint32_t* width,
    uint32_t* height,
    uint32_t* exposure,
    int64_t* start_of_exposure_ts,
    int* ret
);
```

| Parameter           | Description                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| leftEye             | The left eye holds the handle of the SeeThrough camera image. Setting it to 0 indicates not to acquire the left-eye image   |
| rightEye            | The right eye holds the handle of the SeeThrough camera image. Setting it to 0 indicates not to acquire the right-eye image |
| width               | The desired image width (in pixels). The output is the actual width acquired                                                |
| height              | The desired image height (in pixels). The output is the actual height acquired                                              |
| exposure            | The exposure time acquired                                                                                                  |
| startTimeOfExposure | The start time of exposure                                                                                                  |
| ret                 | Whether the acquired data is valid                                                                                          |

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_GetSeeThroughData <br>
Status: <br>
[Available in header source code](./include/PxrPlugin.h?plain=1#L612) <br>
[Documented by PICO](https://pdocor.pico-interactive.com/reference/native/xr/2.0.1/de/d7f/_pxr_api_8h.html#a37793078d69282c1a769df5925b81827)

---

### xrInvokeFunctionsPICO

_Not tested_

```c
XrResult xrInvokeFunctionsPICO(
    XrInstance instance,
    xrFunctionName name,
    void * input,
    unsigned int size_in,
    void[]* output,
    unsigned int size_out
);
```

| No.    | Function name                         |
| ------ | ------------------------------------- |
| 0      | XR_SET_SEETHROUGH_VISIBLE             |
| 1      | XR_SET_GUARDIANSYSTEM_DISABLE         |
| 2      | No function assigned.                 |
| 4      | XR_PAUSE_GUARDIANSYSTEM_FOR_STS       |
| 5-8    | No function assigned.                 |
| 9      | XR_START_CAMERA_PREVIEW               |
| 10-11  | No function assigned.                 |
| 12     | XR_SET_MONO_MODE                      |
| 13     | XR_GET_BOUNDARY_CONFIGURED            |
| 14     | XR_SET_BOUNDARY_VISIBLE               |
| 15     | XR_SET_SEETHROUGH_BACKGROUND          |
| 16     | XR_GET_BOUNDARY_VISIBLE               |
| 17     | Sets first 4 output arguments to 0xFF |
| 18     | No function assigned.                 |
| 19     | xrInvokeFunctionsPICO ???             |
| 19-999 | No function assigned.                 |
| 1000   | ipc?                                  |
| 1001   | ipc?                                  |
| 1002   | Unkown function.                      |
| 1003   | Unkown function.                      |

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_boundary extension to be enabled

External name: Pxr_InvokeFunctions <br>
Status: [Available in header source code](./include/PxrPlugin.h?plain=1#L555)

---

## Mixed Reality (XR_BD_mr_management)

### xrStartMRModeBD

```c
XrResult xrStartMRModeBD(
    XrInstance instance,
    int param_2
);
```

> [!TIP]
> Requires the XR_BD_mr_management extension to be enabled

External name: Pxr_StartMRMode <br>
Status: **To be RE'd**

---

### xrStopMRModeBD

```c
XrResult xrStopMRModeBD(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_BD_mr_management extension to be enabled

External name: Pxr_StopMRMode <br>
Status: **To be RE'd**

---

### xrStopSpatialRecognitionBD

```c
XrResult xrStopSpatialRecognitionBD(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_BD_mr_management extension to be enabled

External name: Pxr_StopSpatialRecognition <br>
Status: **To be RE'd**

---

### xrSetMrConfigurationBD

```c
XrResult xrSetMrConfigurationBD(
    XrInstance instance,
    int param_2,
    int param_3,
    int param_4,
    long param_5
);
```

> [!TIP]
> Requires the XR_BD_mr_management extension to be enabled

External name: Pxr_SetMrConfiguration <br>
Status: **To be RE'd**

---

## Spatial anchor (XR_BD_spatial_anchor and XR_BD_spatial_anchor)

### xrCreateSpatialAnchorSpaceBD

_Not tested_

```c
XrResult xrCreateSpatialAnchorSpaceBD(
    XrInstance instance,
    PxrSpatialAnchorCreateInfo* info,
    uint64_t* handle
);
```

**Parameters not documented**

See [PxrSpatialAnchorCreateInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L365).

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_CreateSpatialAnchor <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1689)

---

### xrDestroySpatialAnchorBD

_Not tested_

```c
XrResult xrDestroySpatialAnchorBD(
    XrInstance instance,
    uint64_t handle
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_DestroySpatialAnchor <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1691)

---

### xrSetSpatialAnchorPropertyBD

```c
XrResult xrSetSpatialAnchorPropertyBD();
```

Not implemented, returns _XR_ERROR_FUNCTION_UNSUPPORTED_.

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_SetSpatialAnchorProperty <br>

---

### xrGetSpatialAnchorPropertyBD

```c
XrResult xrGetSpatialAnchorPropertyBD();
```

Not implemented, returns _XR_ERROR_FUNCTION_UNSUPPORTED_.

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_GetSpatialAnchorProperty <br>

---

### xrSetSpatialAnchorTagBD

```c
XrResult xrSetSpatialAnchorTagBD();
```

Not implemented, returns _XR_ERROR_FUNCTION_UNSUPPORTED_.

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_SetSpatialAnchorTag <br>

---

### xrGetSpatialAnchorTagBD

```c
XrResult xrGetSpatialAnchorTagBD();
```

Not implemented, returns _XR_ERROR_FUNCTION_UNSUPPORTED_.

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_GetSpatialAnchorTag <br>
Status: **To be RE'd**

---

### xrGetSpatialAnchorUuidBD

_Not tested_

```c
XrResult xrGetSpatialAnchorUuidBD(
    XrInstance instance,
    uint64_t handle,
    PxrSpatialInstanceUuid* uuid
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_spatial_anchor extension to be enabled

External name: Pxr_GetSpatialAnchorUuid <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1703)

---

### xrSaveSpatialAnchorBD

_Not tested_

```c
XrResult xrSaveSpatialAnchorBD(
    XrInstance instance,
    PxrSpatialAnchorSaveInfo* info,
    uint64_t* requestId
);
```

**Parameters not documented**

See [PxrSpatialAnchorSaveInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L373).

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_SaveSpatialAnchor <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1693)

---

### xrDeleteSpatialAnchorBD

_Not tested_

```c
XrResult xrDeleteSpatialAnchorBD(
    XrInstance instance,
    PxrSpatialAnchorDeleteInfo* info,
    uint64_t* requestId
);
```

**Parameters not documented**

See [PxrSpatialAnchorDeleteInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L381).

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_DeleteSpatialAnchor <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1695)

---

### xrLoadSpatialAnchorByIdBD

_Not tested_

```c
XrResult xrLoadSpatialAnchorByIdBD(
    XrInstance instance,
    PxrSpatialInstanceLoadByIdInfo* info,
    uint64_t* requestId
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_LoadSpatialAnchorById <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1697)

---

### xrGetSpatialAnchorLoadResultsBD

_Not tested_

```c
XrResult xrGetSpatialAnchorLoadResultsBD(
    XrInstance instance,
    uint64_t requestId,
    PxrSpatialAnchorLoadResult loadResults
);
```

**Parameters not documented**

See [PxrSpatialAnchorLoadResults](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L493).

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_GetSpatialAnchorLoadResults <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1699)

---

### xrExportSpatialInstanceBD

```c
XrResult xrExportSpatialInstanceBD(
    XrInstance instance,
    long param_2,
    long param_3
);
```

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_ExportSpatialInstance <br>
Status: **To be RE'd**

---

### xrImportSpatialInstanceBD

```c
XrResult xrImportSpatialInstanceBD(
    XrInstance instance,
    long param_2,
    long param_3
);
```

> [!TIP]
> Requires the XR_BD_spatial_anchor_persistence extension to be enabled

External name: Pxr_ImportSpatialInstance <br>
Status: **To be RE'd**

---

## Room capturing (XR_BD_room_scene)

### xrStartRoomCaptureBD

_Not tested_

```c
XrResult xrStartRoomCaptureBD(
    XrInstance instance
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_StartRoomCapture <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1720)

---

### xrCreateRoomSceneDataBD

```c
XrResult xrCreateRoomSceneDataBD(
    XrInstance instance,
    PxrSpatialInstanceUuid anchorUuid,
    int* roomSceneData,
    int dataLen,
    unsigned long roomSceneDataHandle
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_CreateRoomSceneData <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1720)

---

### xrDestroyRoomSceneDataBD

```c
XrResult xrDestroyRoomSceneDataBD(
    XrInstance instance,
    unsigned long* roomSceneDataHandle
);
```

**Parameters not documented**

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_DestroyRoomSceneData <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1710)

---

### xrSaveRoomSceneDataBD

_Not tested_

```c
XrResult xrSaveRoomSceneDataBD(
    XrInstance instance,
    PxrRoomSceneDataSaveInfo* saveInfo,
    unsigned long* requestId
);
```

**Parameters not documented**

See [PxrRoomSceneDataSaveInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L524).

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_SaveRoomSceneData <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1712)

---

### xrDeleteRoomSceneDataBD

_Not tested_

```c
XrResult xrDeleteRoomSceneDataBD(
    XrInstance instance,
    PxrRoomSceneDataDeleteInfo* saveInfo,
    unsigned long* requestId
);
```

**Parameters not documented**

See [PxrRoomSceneDataDeleteInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L530).

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_DeleteRoomSceneData <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1712)

---

### xrGetRoomSceneLoadResultsBD

_Not tested_

```c
XrResult xrGetRoomSceneLoadResultsBD(
    XrInstance instance,
    unsigned long requestId,
    PxrRoomSceneLoadResults* results
);
```

**Parameters not documented**

See [PxrRoomSceneLoadResults](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L580).

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_GetRoomSceneLoadResults <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1718C35-L1718C62)

---

### xrLoadRoomSceneBD

_Not tested_

```c
XrResult xrLoadRoomSceneBD(
    XrInstance instance,
    PxrRoomSceneLoadInfo* loadInfo,
    unsigned long* requestId
);
```

**Parameters not documented**

See [PxrRoomSceneLoadInfo](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L556).

> [!TIP]
> Requires the XR_BD_room_scene extension to be enabled

External name: Pxr_LoadRoomScene <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1716C35-L1716C52)

---

## Human occlusion (XR_BD_human_occlusion_ext)

### xrStartHumanOcclusionBD

_Not tested_

```c
XrResult xrStartHumanOcclusionBD(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_BD_human_occlusion_ext extension to be enabled

External name: Pxr_StartHumanOcclusion <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1683)

---

### xrAcquire_occlusion_infoBD

```c
XrResult xrAcquire_occlusion_infoBD(
    XrInstance instance,
    long param_2,
    long param_3
);
```

> [!TIP]
> Requires the XR_BD_human_occlusion_ext extension to be enabled

External name Pxr_AcquireMeshingInfo? <br>
Status: **To be RE'd**

---

### xrStopHumanOcclusionBD

_Not tested_

```c
XrResult xrStopHumanOcclusionBD(
    XrInstance instance,
);
```

> [!TIP]
> Requires the XR_BD_human_occlusion_ext extension to be enabled

External name: Pxr_StopHumanOcclusion <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1683)

---

## Mixed Reality Capture (XR_PICO_mrc_pose_ext_enable or XR_PICO_mrc_pose)

### xrGetMrcPosePICO

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetMrcPosePICO(
    XrInstance instance,
    PxrPosef pose
);
```

**Parameters not documented**

See [PxrPosef](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1388).

> [!TIP]
> Requires the XR_PICO_mrc_pose_ext_enable or XR_PICO_mrc_pose extension to be enabled

External name: Pxr_GetMrcPose <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1683)

---

### xrSetMrcPosePICO

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrSetMrcPosePICO(
    XrInstance instance,
    PxrPosef* pose
);
```

**Parameters not documented**

See [PxrPosef](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1388).

> [!TIP]
> Requires the XR_PICO_mrc_pose_ext_enable or XR_PICO_mrc_pose extension to be enabled

External name: Pxr_SetMrcPose <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L2113)

---

### xrSetIsSupportMovingMrcPICO

_Not tested_

```c
XrResult xrSetIsSupportMovingMrcPICO(
    XrInstance instance,
    bool support
),
```

**Parameters not documented**

> [!TIP]
> Requires the XR_PICO_mrc_pose_ext_enable or XR_PICO_mrc_pose extension to be enabled

External name: Pxr_SetIsSupportMovingMrc <br>
Status: [Available in external source code](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L2116)

---

## External camera (XR_BD_external_camera)

### xrGetExternalCameraInfoBD

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrGetExternalCameraInfoBD(
    XrInstance instance,
    PxrTrackingOrigin pxrTrackingOrigin,
    PxrPosef* outPose
);
```

**Parameters not documented**

See [PxrTrackingOrigin](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L857).

See [PxrPosef](https://github.com/Pico-Developer/Getstarted-Unity/blob/0501b7a2d9e56f563ce32e885c61815ccf282484/PICO%20Unity%20Integration%20SDK%20230/Runtime/Scripts/PXR_Plugin.cs#L1388).

> [!TIP]
> Requires the XR_BD_external_camera extension to be enabled

External name: Pxr_GetExternalCameraInfo <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2791)

---

## Passthrough (XR_PICO_passthrough)

### xrPassthroughLayerSetStylePICO

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrPassthroughLayerSetStylePICO(
    XrInstance instance,
    PxrLayerEffect type,
    float value,
    float duration
);
```

**Parameters not documented**

See [PxrLayerEffect](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L895).

> [!TIP]
> Requires the XR_PICO_passthrough extension to be enabled

External name: Pxr_SetPassthroughStyle <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2791)

---

## Anchor entity (XR_BD_anchor_entity)

### xrCreateAnchorEntityBD

_Not tested_

```c
XrResult xrCreateAnchorEntityBD(
    XrInstance instance,
    PxrAnchorEntityCreateInfo* info,
    unsigned long* anchorHandle
);
```

**Parameters not documented**

See [PxrAnchorEntityCreateInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L573).

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_CreateAnchorEntity <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2261)

---

### xrDestroyAnchorEntityBD

_Not tested_

```c
XrResult xrDestroyAnchorEntityBD(
    XrInstance instance,
    PxrAnchorEntityDestroyInfo* info
);
```

**Parameters not documented**

See [PxrAnchorEntityDestroyInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L580).

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_DestroyAnchorEntity <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2264)

---

### xrCreateAnchorSpaceBD

_Not tested_

```c
XrResult xrCreateAnchorSpaceBD(
    XrInstance instance,
    PxrAnchorEntityCreateInfo* info,
    unsigned long* anchorHandle
);
```

**Parameters not documented**

See [PxrAnchorEntityCreateInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L573).

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_CreateAnchorEntity <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2261)

---

### xrGetAnchorEntityUuidBD

_Gets the universally unique identifier (UUID) of an anchor entity._

```c
XrResult xrGetAnchorEntityUuidBD(
    XrInstance instance,
    unsigned long anchorHandle,
    PxrUuid* uuid
);
```

| Parameter    | Description                                               |
| ------------ | --------------------------------------------------------- |
| anchorHandle | The the bound actor of the anchor entity to get UUID for. |
| uuid         | Returns the UUID of the anchor entity.                    |

See [PxrUuid](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L549).

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorEntityUuid <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2270)

---

### xrAddAnchorComponentBD

```c
XrResult xrAddAnchorComponentBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_AddAnchorComponent <br>
Status: **To be RE'd**

---

### xrRemoveAnchorComponentBD

```c
XrResult xrRemoveAnchorComponentBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_RemoveAnchorComponent <br>
Status: **To be RE'd**

---

### xrGetAnchorComponentFlagsBD

_Gets the components supported by an anchor entity._

```c
XrResult xrGetAnchorComponentFlagsBD(
    XrInstance instance,
    unsigned long actorHandle,
    unsigned long* outAnchorComponentFlag
);
```

| Parameter   | Description                                                                |
| ----------- | -------------------------------------------------------------------------- |
| actorHandle | Specifies the handle of the anchor entity to get supported components for. |
| flag        | Returns the flags of the supported components.                             |

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorComponentFlags <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2273) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#PXR_GetAnchorComponentFlags)

---

### xrGetAnchorSceneLabelBD

_Gets the scene label of an anchor entity._

```c
XrResult xrGetAnchorSceneLabelBD(
    XrInstance instance,
    unsigned long actorHandle,
    PxrSceneLabel* label
);
```

| Parameter   | Description                                                                                                                                                                                                       |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| actorHandle | Specifies the handle of the anchor entity.                                                                                                                                                                        |
| label       | Returns the anchor entity's scene label. <br> See [PxrSceneLabel](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L864). |

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorSceneLabel <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2277) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#PXR_GetAnchorSceneLabel)

---

### xrGetAnchorPlaneBoundaryInfoBD

_Gets the information about the boundary (rectangle) for an anchor entity. Before calling this method, you need to load anchor entities and get the anchor entity load result first. The result contains the actors and UUIDs of anchor entities loaded._

```c
XrResult xrGetAnchorPlaneBoundaryInfoBD(
    XrInstance instance,
    unsigned long anchorHandle,
    PxrAnchorPlaneBoundaryInfo* info
);
```

| Parameter    | Description                                                                                                                                                                      |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| anchorHandle | Specifies the handle of the anchor entity.                                                                                                                                       |
| info         | See [PxrAnchorPlaneBoundaryInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L615). |

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorPlaneBoundaryInfo <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2284) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#PXR_GetAnchorEntityUuid)

---

### xrGetAnchorPlanePolygonInfoBD

_Gets the information about the polygon (irregular plane) for an anchor entity. Before calling this method, you need to load anchor entities and get the anchor entity load result first._

```c
XrResult xrGetAnchorPlanePolygonInfoBD(
    XrInstance instance,
    unsigned long anchorHandle,
    PxrAnchorPlanePolygonInfo info
);
```

| Parameter    | Description                                                                                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| anchorHandle | Specifies the handle of the anchor entity.                                                                                                                                      |
| info         | See [PxrAnchorPlanePolygonInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L621). |

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorPlanePolygonInfo <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2284) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#PXR_GetAnchorPlanePolygonInfo)

---

### xrGetAnchorBoxInfoBD

_Not tested_

```c
XrResult xrGetAnchorBoxInfoBD(
    XrInstance instance,
    unsigned long anchorHandle,
    PxrAnchorVolumeInfo* info
);
```

**Parameters not documented**

See [PxrAnchorVolumeInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L628).

> [!TIP]
> Requires the XR_BD_anchor_entity extension to be enabled

External name: Pxr_GetAnchorBoxInfo <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2288)

---

### xrPersistAnchorEntityBD

_Not tested_

```c
XrResult xrPersistAnchorEntityBD(
    XrInstance instance,
    PxrAnchorEntityPersistInfo info,
    unsigned long* taskId
);
```

**Parameters not documented**

See [PxrAnchorEntityPersistInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L640).

> [!TIP]
> Requires the XR_BD_anchor_entity_persistence extension to be enabled

External name: Pxr_PersistAnchorEntity <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2291) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#0a67613d)

---

### xrUnpersistAnchorEntityBD

_Unpersists specified anchor entities, which means deleting anchor entities from the location where they are saved. Currently, only supports deleting anchor entities saved in the device's local storage._

```c
XrResult xrUnpersistAnchorEntityBD(
    XrInstance instance,
    PxrAnchorEntityUnPersistInfo info,
    unsigned long* taskId
);
```

**Parameters not documented**

See [PxrAnchorEntityUnPersistInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L688).

> [!TIP]
> Requires the XR_BD_anchor_entity_persistence extension to be enabled

External name: Pxr_UnpersistAnchorEntity <br>
Status: <br>
[Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2295) <br>
[Documented by PICO](https://developer.picoxr.com/reference/unreal/client-api/#3356925f)

---

### xrClearPersistedAnchorEntityBD

_Not tested_

```c
XrResult xrClearPersistedAnchorEntityBD(
    PxrAnchorEntityClearInfo info,
    unsigned long* taskId
);
```

**Parameters not documented**

See [PxrAnchorEntityClearInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L713).

> [!TIP]
> Requires the XR_BD_anchor_entity_persistence extension to be enabled

External name: Pxr_ClearPersistedAnchorEntity <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2295)

---

### xrLoadAnchorEntityBD

```c
XrResult xrLoadAnchorEntityBD(
    XrInstance instance,
    PxrAnchorEntityLoadInfo* info,
    unsigned long* taskId
);
```

**Parameters not documented**

See [PxrAnchorEntityLoadInfo](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L737).

> [!TIP]
> Requires the XR_BD_anchor_entity_persistence extension to be enabled

External name: Pxr_LoadAnchorEntity <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2303)

---

### xrGetAnchorEntityLoadResultsBD

_Not tested_

```c
XrResult xrGetAnchorEntityLoadResultsBD(
    XrInstance instance,
    unsigned long taskId,
    PxrAnchorEntityLoadResults results
);
```

**Parameters not documented**

See [PxrAnchorEntityLoadResults](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L770).

> [!TIP]
> Requires the XR_BD_anchor_entity_persistence extension to be enabled

External name: Pxr_GetAnchorEntityLoadResults <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2306)

---

## Room capture and Spatial mapping (XR_BD_semi_auto_room_capture and XR_BD_spatial_localization_and_tracking)

### xrStartSemiAutoRoomCaptureBD

_Not tested_

```c
XrResult xrStartSemiAutoRoomCaptureBD(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_StartSemiAutoRoomCapture <br>

---

### xrStopSemiAutoRoomCaptureBD

_Not tested_

```c
XrResult xrStopSemiAutoRoomCaptureBD(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_StopSemiAutoRoomCapture <br>

---

### xrSetFloorHeightBD

_Not tested_

```c
XrResult xrSetFloorHeightBD(
    XrInstance instance,
    int* height
);
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_SetFloorHeight <br>

---

### xrSetCeilingHeightBD

_Not tested_

```c
XrResult xrSetCeilingHeightBD(
    XrInstance instance,
    long* height
);
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_SetCeilingHeight <br>

---

### xrSetFloorCornerBD

```c
XrResult xrSetFloorCornerBD(
    XrInstance instance,
    int* param_2
),
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_SetFloorCorner <br>
Status: **To be RE'd**

---

### xrGetSemiAutoRoomCaptureCandidatesBD

```c
XrResult xrGetSemiAutoRoomCaptureCandidatesBD(
    XrInstance instance,
    long param_2,
    long param_3
);
```

> [!TIP]
> Requires the XR_BD_semi_auto_room_capture extension to be enabled

External name: Pxr_GetSemiAutoRoomCaptureCandidates <br>
Status: **To be RE'd**

---

### xrGetSpatialTrackingStateBD

```c
XrResult xrGetSpatialTrackingStateBD(
    XrInstance instance
);
```

> [!TIP]
> Requires the XR_BD_spatial_localization_and_tracking extension to be enabled

External name: Pxr_GetSpatialTrackingState <br>
Status: **To be RE'd**

---

### xrBeginSpatialLocalizationBD

```c
XrResult xrBeginSpatialLocalizationBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_spatial_localization_and_tracking extension to be enabled

External name: Pxr_BeginSpatialLocalization <br>
Status: **To be RE'd**

---

### xrEndSpatialLocalizationBD

```c
XrResult xrEndSpatialLocalizationBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_spatial_localization_and_tracking extension to be enabled

External name: Pxr_EndSpatialLocalization <br>
Status: **To be RE'd**

---

### xrBeginSpatialMapCreationBD

```c
XrResult xrBeginSpatialMapCreationBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_spatial_localization_and_tracking extension to be enabled

External name: Pxr_BeginSpatialMapCreation <br>
Status: **To be RE'd**

---

### xrEndSpatialMapCreationBD

```c
XrResult xrEndSpatialMapCreationBD(
    XrInstance instance,
    long param_2
);
```

> [!TIP]
> Requires the XR_BD_spatial_localization_and_tracking extension to be enabled

External name: Pxr_EndSpatialMapCreation <br>
Status: **To be RE'd**

---

### Pxr_StartSpatialSceneCapture

_Not tested_

> [!IMPORTANT]  
> Conflict with reverse engineered function signature. <br>
> This function signature may be incorrect or outdated.

```c
XrResult xrStartSpatialSceneCaptureBD(
    XrInstance instance,
    unsigned long* taskId
);
```

> [!TIP]
> Requires the XR_BD_spatial_scene extension to be enabled

External name: Pxr_StartSpatialSceneCapture <br>
Status: [Available in external source code](https://github.com/Pico-Developer/PICO-Unity-Integration-SDK/blob/fec80f9432f90e59c23495fffccec78044ec43f5/Runtime/Scripts/PXR_Plugin.cs#L2309)

## Functions from other vendors that are available

- xrGetInstanceProcAddr
- xrEnumerateInstanceExtensionProperties
- xrCreateInstance
- xrDestroyInstance
- xrGetInstanceProperties
- xrPollEvent
- xrResultToString
- xrStructureTypeToString
- xrGetSystem
- xrGetSystemProperties
- xrEnumerateEnvironmentBlendModes
- xrCreateSession
- xrDestroySession
- xrEnumerateReferenceSpaces
- xrCreateReferenceSpace
- xrGetReferenceSpaceBoundsRect
- xrCreateActionSpace
- xrLocateSpace
- xrDestroySpace
- xrEnumerateViewConfigurations
- xrGetViewConfigurationProperties
- xrEnumerateViewConfigurationViews
- xrEnumerateSwapchainFormats
- xrCreateSwapchain
- xrDestroySwapchain
- xrEnumerateSwapchainImages
- xrAcquireSwapchainImage
- xrWaitSwapchainImag
- xrReleaseSwapchainImage
- xrBeginSession
- xrEndSession
- xrWaitFrame
- xrBeginFrame
- xrEndFrame
- xrRequestExitSession
- xrLocateViews
- xrStringToPath
- xrPathToString
- xrCreateActionSet
- xrDestroyActionSet
- xrCreateAction
- xrDestroyAction
- xrSuggestInteractionProfileBindings
- xrAttachSessionActionSet
- xrGetCurrentInteractionProfile
- xrGetActionStateBoolean
- xrGetActionStateFloat
- xrGetActionStateVector2f
- xrGetActionStatePose
- xrSyncAction
- xrEnumerateBoundSourcesForActio
- xrGetInputSourceLocalizedName
- xrApplyHapticFeedback
- xrStopHapticFeedback
- xrConvertTimespecTimeToTimeKHR
- xrConvertTimeToTimespecTimeKHR
- xrCreateHandTrackerEXT
- xrDestroyHandTrackerEXT
- xrLocateHandJointsEXT
- xrSetDebugUtilsObjectNameEXT
- xrCreateDebugUtilsMessengerEXT
- xrDestroyDebugUtilsMessengerEXT
- xrSubmitDebugUtilsMessageEXT
- xrSessionBeginDebugUtilsLabelRegionEXT
- xrSessionEndDebugUtilsLabelRegionEXT
- xrSessionInsertDebugUtilsLabelEXT
- xrGetOpenGLESGraphicsRequirementsKHR
- xrGetVulkanInstanceExtensionsKHR
- xrGetVulkanDeviceExtensionsKHR
- xrGetVulkanGraphicsDeviceKHR
- xrGetVulkanGraphicsRequirementsKHR
- xrGetVulkanGraphicsDevice2KHR
- xrCreateVulkanDeviceKHR
- xrGetVulkanGraphicsRequirements2KHR
- xrCreateVulkanInstanceKHR
- xrSetAndroidApplicationThreadKH
- xrEnumerateDisplayRefreshRatesFB
- xrGetDisplayRefreshRateFB
- xrRequestDisplayRefreshRateFB
- xrCreateSwapchainAndroidSurfaceKHR
- xrUpdateSwapchainFB
- xrGetSwapchainStateFB
- xrGetFoveationEyeTrackedStateMETA
- xrCreatePassthroughFB
- xrDestroyPassthroughFB
- xrPassthroughStartFB
- xrPassthroughPauseFB
- xrCreatePassthroughLayerFB
- xrDestroyPassthroughLayerFB
- xrPassthroughLayerPauseFB
- xrPassthroughLayerResumeFB
- xrPassthroughLayerSetStyleFB
- xrCreateGeometryInstanceFB
- xrDestroyGeometryInstanceFB
- xrGeometryInstanceSetTransformFB
- xrCreateTriangleMeshFB
- xrDestroyTriangleMeshFB
- xrTriangleMeshGetVertexBufferFB
- xrTriangleMeshGetIndexBufferFB
- xrTriangleMeshBeginUpdateFB
- xrTriangleMeshEndUpdateFB
- xrTriangleMeshBeginVertexBufferUpdateFB
- xrTriangleMeshEndVertexBufferUpdateFB
- xrCreateFoveationProfileFB
- xrDestroyFoveationProfileFB
