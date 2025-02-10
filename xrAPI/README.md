# PICO OpenXR API

Content dumped from libpxrruntime.so, used by com.pico.xr.openxr_runtime

OpenXR uses a function called xrGetInstanceProcAdrr, documented [here](https://registry.khronos.org/OpenXR/specs/1.0/man/html/xrGetInstanceProcAddr.html).
Original source code from OpenXR for the xrGetInstanceProcAddr function is [here](https://github.com/KhronosGroup/OpenXR-SDK-Source/blob/d0bbcabc2a2e6565035ef3a68ec1f789a2dc9562/src/loader/loader_core.cpp#L715).

# PICO Specific XR functions

## Non-categorized

Written here are all the PICO specific XR extensions that I could find.

```c
xrLogSdkApiPICO
```

Status: **To be RE'd.**

```c
xrGetControllerSensorDataPredictPico
```

Status: **To be RE'd.**

```c
xrSetEngineVersionPico
```

Status: **To be RE'd.**

```c
xrSetMainControllerHandlePico
```

Status: **To be RE'd.**

```c
xrGetMainControllerHandlePico
```

Status: **To be RE'd.**

```c
xrGetControllerConnectionStatePico
```

Status: **To be RE'd**

```c
xrGetPhyControllerInfoPico
```

Status: **To be RE'd**

```c
xrGetPhyControllerTypePico
```

Status: **To be RE'd**

```c
xrVibrateControllerPico
```

Status: **To be RE'd**

```c
xrVibrateControllerEventPico
```

Status: **To be RE'd**

```c
xrSetPhyControllerEnterPairingPico
```

Status: **To be RE'd**

```c
xrSetPhyControllerStopPairingPico
```

Status: **To be RE'd**

```c
xrSetPhyControllerUpgradePico
```

Status: **To be RE'd**

```c
xrSetPhyControllerUnbindPico
```

Status: **To be RE'd**

```c
xrSetPhyControllerEnableKeyPico
```

Status: **To be RE'd**

```c
xrSetVirtualKeyPico
```

Status: **To be RE'd**

```c
xrStartPhyControllerVCMotorPico
```

Status: **To be RE'd**

```c
xrStopPhyControllerVCMotorPico
```

Status: **To be RE'd**

```c
xrSetControllerAmpPico
```

Status: **To be RE'd**

```c
xrSetMotorDelayPico
```

Status: **To be RE'd**

```c
xrGetVibrateDelayTimePico
```

Status: **To be RE'd**

```c
xrStartVibrateBySharemPico
```

Status: **To be RE'd**

```c
xrGetVibrateSharemPico
```

Status: **To be RE'd**

```c
xrStartVibrateByPHFPico
```

Status: **To be RE'd**

```c
xrGetPHFSharedMemPico
```

Status: **To be RE'd**

```c
xrPauseVibratePico
```

Status: **To be RE'd**

```c
xrResumeVibratePico
```

Status: **To be RE'd**

```c
xrReleaseControllerBufferPico
```

Status: **To be RE'd**

```c
xrStartVibrateByCachePico
```

Status: **To be RE'd**

```c
xrClearVibrateByCachePico
```

Status: **To be RE'd**

```c
xrSetAppHandTrackingEnabledPico
```

Status: **To be RE'd**

```c
xrGetActiveInputDeviceTypePico
```

Status: **To be RE'd**

```c
xrGetHandTrackingEnabledPico
```

Status: **To be RE'd**

```c
xrGetHandTrackingHandStatePico
```

Status: **To be RE'd**

```c
xrGetHandTrackingSkeletonPico
```

Status: **To be RE'd**

```c
xrGetHandTrackingMeshPico
```

Status: **To be RE'd**

```c
xrGetControllerSensorDataPredictPICO
```

Status: **To be RE'd**

```c
xrSetControllerMainHandlePICO
```

Status: **To be RE'd**

```c
xrGetControllerMainHandlePICO
```

Status: **To be RE'd**

```c
xrGetControllerConnectionStatePICO
```

Status: **To be RE'd**

```c
xrGetControllerInfoPICO
```

Status: **To be RE'd**

```c
xrResetControllerPICO
```

Status: **To be RE'd**

```c
xrSetArmModelParametersPICO
```

Status: **To be RE'd**

```c
xrGetControllerHandnessPICO
```

Status: **To be RE'd**

```c
xrGetControllerTypePICO
```

Status: **To be RE'd**

```c
xrSetControllerVibratePICO
```

Status: **To be RE'd**

```c
xrSetControllerVibrateEventPICO
```

Status: **To be RE'd**

```c
xrSetControllerEnterPairingPICO
```

Status: **To be RE'd**

```c
xrSetControllerStopPairingPICO
```

Status: **To be RE'd**

```c
xrSetControllerUpgradePICO
```

Status: **To be RE'd**

```c
xrSetControllerUnbindPICO
```

Status: **To be RE'd**

```c
xrSetControllerEnableKeyPICO
```

Status: **To be RE'd**

```c
xrStartPhyControllerVCMotorPICO
```

Status: **To be RE'd**

```c
xrStopPhyControllerVCMotorPICO
```

Status: **To be RE'd**

```c
xrSetControllerAmpPICO
```

Status: **To be RE'd**

```c
xrSetMotorDelayPICO
```

Status: **To be RE'd**

```c
xrGetVibrateDelayTimePICO
```

Status: **To be RE'd**

```c
xrStartVibrateBySharemPICO
```

Status: **To be RE'd**

```c
xrGetVibrateSharemPICO
```

Status: **To be RE'd**

```c
xrStartVibrateByPHFPICO
```

Status: **To be RE'd**

```c
xrGetPHFSharedMemPICO
```

Status: **To be RE'd**

```c
xrPauseVibratePICO
```

Status: **To be RE'd**

```c
xrResumeVibratePICO
```

Status: **To be RE'd**

```c
xrReleaseControllerBufferPICO
```

Status: **To be RE'd**

```c
xrCreateControllerClientPICO
```

Status: **To be RE'd**

```c
xrStartVibrateByCachePICO
```

Status: **To be RE'd**

```c
xrClearVibrateByCachePICO
```

Status: **To be RE'd**

```c
xrUpdateVibrateParamsPICO
```

Status: **To be RE'd**

```c
xrCreateHapticStreamPICO
```

Status: **To be RE'd**

```c
xrWriteHapticStreamPICO
```

Status: **To be RE'd**

```c
xrSetPHFHapticSpeedPICO
```

Status: **To be RE'd**

```c
xrGetPHFHapticSpeedPICO
```

Status: **To be RE'd**

```c
xrGetCurrentFrameSequencePICO
```

Status: **To be RE'd**

```c
xrStartPHFHapticPICO
```

Status: **To be RE'd**

```c
xrStopPHFHapticPICO
```

Status: **To be RE'd**

```c
xrRemovePHFHapticPICO
```

Status: **To be RE'd**

```c
xrGetPHFStreamMemPICO
```

Status: **To be RE'd**

```c
xrGetHandTrackerSettingStatePICO
```

Status: **To be RE'd**

```c
xrGetHandTrackerActiveInputTypePICO
```

Status: **To be RE'd**

```c
xrSetEyeTrackerModePICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackerModePICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackerDataPICO
```

Status: **To be RE'd**

```c
xrSetBodyTrackerStaticCalibStatePICO
```

Status: **To be RE'd**

```c
xrSetBodyTrackerModePICO
```

Status: **To be RE'd**

```c
xrGetBodyTrackerPosePICO
```

Status: **To be RE'd**

```c
xrGetBodyTrackerImuDataPICO
```

Status: **To be RE'd**

```c
xrGetBodyTrackerConnectStatePICO
```

Status: **To be RE'd**

```c
xrGetBodyTrackerBatteryPICO
```

Status: **To be RE'd**

```c
xrGetBodyTrackerCalibStatePICO
```

Status: **To be RE'd**

```c
xrSetBodyTrackingAlgParamPICO
```

Status: **To be RE'd**

```c
xrSetIPDPICO
```

Status: **To be RE'd**

```c
xrGetIPDPICO
```

Status: **To be RE'd**

```c
xrSetTrackingIPDEnabledPICO
```

Status: **To be RE'd**

```c
xrGetTrackingIPDEnabledPICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackingAutoIPDPICO
```

Status: **To be RE'd**

```c
xrGetFrustumParametersPICO
```

Status: **To be RE'd**

```c
xrSetFrustumParametersPICO
```

Status: **To be RE'd**

```c
xrGetConfigPICO
```

Status: **To be RE'd**

```c
xrSetConfigPICO
```

Status: **To be RE'd**

```c
xrGetConfigsPICO
```

Status: **To be RE'd**

```c
xrSetConfigsPICO
```

Status: **To be RE'd**

```c
xrGetFoveationConfigPICO
```

Status: **To be RE'd**

```c
xrGetFoveationConfigPICO
```

Status: **To be RE'd**

```c
xrGetMainClientInfoPICO
```

Status: **To be RE'd**

```c
xrGetPerformanceInfoPICO
```

Status: **To be RE'd**

```c
xrResetSensorPICO
```

Status: **To be RE'd**

```c
xrSetTrackingModePICO
```

Status: **To be RE'd**

```c
xrStartFoveationPICO
```

Status: **To be RE'd**

```c
xrStopFoveationPICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackingDataPICO
```

Status: **To be RE'd**

```c
xrGetTrackingModePICO
```

Status: **To be RE'd**

```c
xrGetFaceTrackingDataPICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackingStatePICO
```

Status: **To be RE'd**

```c
xrGetFaceTrackingStatePICO
```

Status: **To be RE'd**

```c
xrGetPupilDistancePICO
```

Status: **To be RE'd**

```c
xrStartEyeTrackingPICO
```

Status: **To be RE'd**

```c
xrStopEyeTrackingPICO
```

Status: **To be RE'd**

```c
xrSetTrackingStatusPICO
```

Status: **To be RE'd**

```c
xrGetEyeOpennessPICO
```

Status: **To be RE'd**

```c
xrGetEyePupilInfoPICO
```

Status: **To be RE'd**

```c
xrGetPerEyePosePICO
```

Status: **To be RE'd**

```c
xrGetBlinkPICO
```

Status: **To be RE'd**

```c
xrSetControllerPositionPICO
```

Status: **To be RE'd**

```c
xrBoundaryTestNodePICO
```

Status: **To be RE'd**

```c
xrBoundaryTestPointPICO
```

Status: **To be RE'd**

```c
xrGetBoundaryGeometryPICO
```

Status: **To be RE'd**

```c
xrGetBoundaryDimensionsPICO
```

Status: **To be RE'd**

```c
xrGetSeeThroughDataPICO
```

Status: **To be RE'd**

```c
xrInvokeFunctionsPICO
```

Status: **To be RE'd**

```c
xrInvokeFunctionsPICO
```

Status: **To be RE'd**

Note: Are these part of PICO's API? I can't find them in any OpenXR source code...

```c
xrStartMRModeBD
```

Status: **To be RE'd**

```c
xrStopMRModeBD
```

Status: **To be RE'd**

```c
xrStopSpatialRecognitionBD
```

Status: **To be RE'd**

```c
xrSetMrConfigurationBD
```

Status: **To be RE'd**

```c
xrCreateSpatialAnchorSpaceBD
```

Status: **To be RE'd**

```c
xrDestroySpatialAnchorBD
```

Status: **To be RE'd**

```c
xrSetSpatialAnchorPropertyBD
```

Status: **To be RE'd**

```c
xrGetSpatialAnchorPropertyBD
```

Status: **To be RE'd**

```c
xrSetSpatialAnchorTagBD
```

Status: **To be RE'd**

```c
xrGetSpatialAnchorTagBD
```

Status: **To be RE'd**

```c
xrGetSpatialAnchorUuidBD
```

Status: **To be RE'd**

```c
xrSaveSpatialAnchorBD
```

Status: **To be RE'd**

```c
xrDeleteSpatialAnchorBD
```

Status: **To be RE'd**

```c
xrLoadSpatialAnchorByIdBD
```

Status: **To be RE'd**

```c
xrGetSpatialAnchorLoadResultsBD
```

Status: **To be RE'd**

```c
xrExportSpatialInstanceBD
```

Status: **To be RE'd**

```c
xrImportSpatialInstanceBD
```

Status: **To be RE'd**

```c
xrStartRoomCaptureBD
```

Status: **To be RE'd**

```c
xrCreateRoomSceneDataBD
```

Status: **To be RE'd**

```c
xrDestroyRoomSceneDataBD
```

Status: **To be RE'd**

```c
xrSaveRoomSceneDataBD
```

Status: **To be RE'd**

```c
xrAcquire_occlusion_infoBD
```

Status: **To be RE'd**

```c
xrStopHumanOcclusionBD
```

Status: **To be RE'd**

```c
xrGetMrcPosePICO
```

Status: **To be RE'd**

```c
xrSetMrcPosePIC
```

Status: **To be RE'd**

```c
xrSetIsSupportMovingMrcPICO
```

Status: **To be RE'd**

```c
xrSetIsSupportMovingMrcPICO
```

Status: **To be RE'd**

```c
xrGetExternalCameraInfoBD
```

Status: **To be RE'd**

```c
xrPassthroughLayerSetStylePICO
```

Status: **To be RE'd**

```c
xrPassthroughLayerSetStylePICO
```

Status: **To be RE'd**

```c
xrCreateAnchorEntityBD
```

Status: **To be RE'd**

```c
xrDestroyAnchorEntityBD
```

Status: **To be RE'd**

```c
xrCreateAnchorSpaceBD
```

Status: **To be RE'd**

```c
xrGetAnchorEntityUuidBD
```

Status: **To be RE'd**

```c
xrAddAnchorComponentBD
```

Status: **To be RE'd**

```c
xrRemoveAnchorComponentBD
```

Status: **To be RE'd**

```c
xrGetAnchorComponentFlagsBD
```

Status: **To be RE'd**

```c
xrGetAnchorComponentFlagsBD
```

Status: **To be RE'd**

```c
xrGetAnchorSceneLabelBD
```

Status: **To be RE'd**

```c
xrGetAnchorPlaneBoundaryInfoBD
```

Status: **To be RE'd**

```c
xrGetAnchorPlanePolygonInfoBD
```

Status: **To be RE'd**

```c
xrGetAnchorBoxInfoBD
```

Status: **To be RE'd**

```c
xrPersistAnchorEntityBD
```

Status: **To be RE'd**

```c
xrUnpersistAnchorEntityBD
```

Status: **To be RE'd**

```c
xrClearPersistedAnchorEntityBD
```

Status: **To be RE'd**

```c
xrLoadAnchorEntityBD
```

Status: **To be RE'd**

```c
xrGetAnchorEntityLoadResultsBD
```

Status: **To be RE'd**

```c
xrStartSemiAutoRoomCaptureBD
```

Status: **To be RE'd**

```c
xrStopSemiAutoRoomCaptureBD
```

Status: **To be RE'd**

```c
xrSetFloorHeightBD
```

Status: **To be RE'd**

```c
xrSetCeilingHeightBD
```

Status: **To be RE'd**

```c
xrSetFloorCornerBD
```

Status: **To be RE'd**

```c
xrGetSemiAutoRoomCaptureCandidatesBD
```

Status: **To be RE'd**

```c
xrGetSpatialTrackingStateBD
```

Status: **To be RE'd**

```c
xrBeginSpatialLocalizationBD
```

Status: **To be RE'd**

```c
xrEndSpatialLocalizationBD
```

Status: **To be RE'd**

```c
xrBeginSpatialMapCreationBD
```

Status: **To be RE'd**

```c
xrEndSpatialMapCreationBD
```

Status: **To be RE'd**

```c
xrStartSpatialSceneCaptureBD
```

Status: **To be RE'd**

```c
xrStartSpatialSceneCaptureBD
```

Status: **To be RE'd**
