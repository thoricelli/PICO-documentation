# PICO OpenXR API

Content dumped from libpxrruntime.so, used by com.pico.xr.openxr_runtime

OpenXR uses a function called xrGetInstanceProcAdrr, documented [here](https://registry.khronos.org/OpenXR/specs/1.0/man/html/xrGetInstanceProcAddr.html). <br>
Original source code from OpenXR for the xrGetInstanceProcAddr function is [here](https://github.com/KhronosGroup/OpenXR-SDK-Source/blob/d0bbcabc2a2e6565035ef3a68ec1f789a2dc9562/src/loader/loader_core.cpp#L715).

# PICO Specific XR functions

## Non-categorized

Written here are all the PICO specific XR extensions that I could find.

Note: External type refers to the name given to the function in libpxrplugin.so <br>
(PICO's library used by Unreal and Unity.)

```c
xrLogSdkApiPICO
```

External name: Pxr_LogPluginApi <br>
Status: **To be RE'd.** <br>
Note: No source code available anywhere.

```c
xrGetControllerSensorDataPredictPico
```

External name: Pxr_GetControllerConnectStatus <br>
Status: **To be RE'd.**

```c
xrSetEngineVersionPico
```

External name: Pxr_SetEngineVersionPico <br>
Status: **To be RE'd.** <br>
Note: Not made public through libpxrplugin.so.

```c
xrSetMainControllerHandlePico
```

External name: Pxr_SetControllerMainInputHandle <br>
Status: **To be RE'd.**

```c
xrGetMainControllerHandlePico
```

External name: Pxr_GetControllerMainInputHandle <br>
Status: **To be RE'd.**

```c
xrGetControllerConnectionStatePico
```

External name: Pxr_GetControllerConnectStatus <br>
Status: **To be RE'd**

```c
xrGetPhyControllerInfoPico
```

External name: Pxr_GetControllerinfo <br>
Status: **To be RE'd**

```c
xrGetPhyControllerTypePico
```

External name: getControllerType <br>
Status: **To be RE'd**

```c
xrVibrateControllerPico
```

External name: Pxr_SetControllerVibration <br>
Status: **To be RE'd**

```c
xrVibrateControllerEventPico
```

External name: Pxr_SetControllerVibrationEvent <br>
Status: **To be RE'd**

```c
xrSetPhyControllerEnterPairingPico
```

External name: Pxr_SetControllerEnterPairing <br>
Status: **To be RE'd**

```c
xrSetPhyControllerStopPairingPico
```

External name: Pxr_SetControllerStopPairing <br>
Status: **To be RE'd**

```c
xrSetPhyControllerUpgradePico
```

External name: Pxr_SetControllerUpgrade <br>
Status: **To be RE'd**

```c
xrSetPhyControllerUnbindPico
```

External name: Pxr_SetControllerUnbind <br>
Status: **To be RE'd**

```c
xrSetPhyControllerEnableKeyPico
```

External name: Pxr_SetControllerEnableKey <br>
Status: **To be RE'd**

```c
xrSetVirtualKeyPico
```

Status: **To be RE'd**

```c
xrStartPhyControllerVCMotorPico
```

External name: Pxr_StartControllerVCMotor <br>
Status: **To be RE'd**

```c
xrStopPhyControllerVCMotorPico
```

External name: Pxr_StopControllerVCMotor <br>
Status: **To be RE'd**

```c
xrSetControllerAmpPico
```

External name: Pxr_SetControllerAmp <br>
Status: **To be RE'd**

```c
xrSetMotorDelayPico
```

External name: Pxr_SetControllerDelay <br>
Status: **To be RE'd**

```c
xrGetVibrateDelayTimePico
```

External name: Pxr_GetVibrateDelayTime <br>
Status: **To be RE'd**

```c
xrStartVibrateBySharemPico
```

External name: Pxr_StartVibrateBySharemF and Pxr_StartVibrateBySharemU <br>
Status: **To be RE'd**

```c
xrGetVibrateSharemPico
```

External name: Pxr_GetVibrateSharem <br>
Status: **To be RE'd**

```c
xrStartVibrateByPHFPico
```

External name: Pxr_StartVibrateByPHF <br>
Status: **To be RE'd**

```c
xrGetPHFSharedMemPico
```

External name: Pxr_GetPHFSharedMem <br>
Status: **To be RE'd**

```c
xrPauseVibratePico
```

External name: Pxr_PauseVibrate <br>
Status: **To be RE'd**

```c
xrResumeVibratePico
```

External name: Pxr_ResumeVibrate <br>
Status: **To be RE'd**

```c
xrReleaseControllerBufferPico
```

External name: Pxr_ReleaseControllerBuffer <br>
Status: **To be RE'd**

```c
xrStartVibrateByCachePico
```

External name: Pxr_StartVibrateByCache <br>
Status: **To be RE'd**

```c
xrClearVibrateByCachePico
```

External name: Pxr_ClearVibrateByCache <br>
Status: **To be RE'd**

```c
xrSetAppHandTrackingEnabledPico
```

External name: Pxr_SetAppHandTrackingEnabled <br>
Status: **To be RE'd**

```c
xrGetActiveInputDeviceTypePico
```

External name: Pxr_GetActiveInputDeviceType <br>
Status: **To be RE'd**

```c
xrGetHandTrackingEnabledPico
```

External name: Pxr_GetHandTrackingEnabled <br>
Status: **To be RE'd**

```c
xrGetHandTrackingHandStatePico
```

External name: Pxr_GetHandTrackingHandState <br>
Status: **To be RE'd**

```c
xrGetHandTrackingSkeletonPico
```

External name: Pxr_GetHandTrackingSkeleton <br>
Status: **To be RE'd**

```c
xrGetHandTrackingMeshPico
```

External name: Pxr_GetHandTrackingMesh <br>
Status: **To be RE'd**

```c
xrGetControllerSensorDataPredictPICO
```

External name: getControllerSensorDataPredict <br>
Status: **To be RE'd**

```c
xrSetControllerMainHandlePICO
```

External name: Pxr_SetControllerMainInputHandle <br>
Status: **To be RE'd**

```c
xrGetControllerMainHandlePICO
```

External name: Pxr_GetControllerMainInputHandle <br>
Status: **To be RE'd**

```c
xrGetControllerConnectionStatePICO
```

External name: Pxr_GetControllerConnectStatus <br>
Status: **To be RE'd**

```c
xrGetControllerInfoPICO
```

External name: Pxr_GetControllerinfo <br>
Status: **To be RE'd**

```c
xrResetControllerPICO
```

External name: Pxr_ResetController <br>
Status: **To be RE'd**

```c
xrSetArmModelParametersPICO
```

External name: Pxr_SetArmModelParameters <br>
Status: **To be RE'd**

```c
xrGetControllerHandnessPICO
```

External name: Pxr_GetControllerHandness <br>
Status: **To be RE'd**

```c
xrGetControllerTypePICO
```

External name: getControllerType <br>
Status: **To be RE'd**

```c
xrSetControllerVibratePICO
```

External name: Pxr_SetControllerVibration <br>
Status: **To be RE'd**

```c
xrSetControllerVibrateEventPICO
```

External name: Pxr_SetControllerVibrationEvent <br>
Status: **To be RE'd**

```c
xrSetControllerEnterPairingPICO
```

External name: Pxr_SetControllerEnterPairing <br>
Status: **To be RE'd**

```c
xrSetControllerStopPairingPICO
```

External name: Pxr_SetControllerStopPairing <br>
Status: **To be RE'd**

```c
xrSetControllerUpgradePICO
```

External name: Pxr_SetControllerUpgrade <br>
Status: **To be RE'd**

```c
xrSetControllerUnbindPICO
```

External name: Pxr_SetControllerUnbind <br>
Status: **To be RE'd**

```c
xrSetControllerEnableKeyPICO
```

External name: Pxr_SetControllerEnableKey <br>
Status: **To be RE'd**

```c
xrStartPhyControllerVCMotorPICO
```

External name: Pxr_StartControllerVCMotor <br>
Status: **To be RE'd**

```c
xrStopPhyControllerVCMotorPICO
```

External name: Pxr_StopControllerVCMotor <br>
Status: **To be RE'd**

```c
xrSetControllerAmpPICO
```

External name: Pxr_SetControllerAmp <br>
Status: **To be RE'd**

```c
xrSetMotorDelayPICO
```

External name: Pxr_SetControllerDelay <br>
Status: **To be RE'd**

```c
xrGetVibrateDelayTimePICO
```

External name: Pxr_GetVibrateDelayTime <br>
Status: **To be RE'd**

```c
xrStartVibrateBySharemPICO
```

External name: Pxr_StartVibrateBySharemF and Pxr_StartVibrateBySharemU <br>
Status: **To be RE'd**

```c
xrGetVibrateSharemPICO
```

External name: Pxr_GetVibrateSharem <br>
Status: **To be RE'd**

```c
xrStartVibrateByPHFPICO
```

External name: Pxr_StartVibrateByPHF <br>
Status: **To be RE'd**

```c
xrGetPHFSharedMemPICO
```

External name: Pxr_GetPHFSharedMem <br>
Status: **To be RE'd**

```c
xrPauseVibratePICO
```

External name: Pxr_PauseVibrate <br>
Status: **To be RE'd**

```c
xrResumeVibratePICO
```

External name: Pxr_ResumeVibrate <br>
Status: **To be RE'd**

```c
xrReleaseControllerBufferPICO
```

External name: Pxr_ReleaseControllerBuffer <br>
Status: **To be RE'd**

```c
xrCreateControllerClientPICO
```

Status: **To be RE'd**

```c
xrStartVibrateByCachePICO
```

External name: Pxr_StartVibrateByCache <br>
Status: **To be RE'd**

```c
xrClearVibrateByCachePICO
```

External name: Pxr_ClearVibrateByCache <br>
Status: **To be RE'd**

```c
xrUpdateVibrateParamsPICO
```

External name: Pxr_UpdateVibrateParams <br>
Status: **To be RE'd**

```c
xrCreateHapticStreamPICO
```

External name: Pxr_CreateHapticStream <br>
Status: **To be RE'd**

```c
xrWriteHapticStreamPICO
```

External name: Pxr_WriteHapticStream <br>
Status: **To be RE'd**

```c
xrSetPHFHapticSpeedPICO
```

External name: Pxr_SetPHFHapticSpeed <br>
Status: **To be RE'd**

```c
xrGetPHFHapticSpeedPICO
```

External name: Pxr_GetPHFHapticSpeed <br>
Status: **To be RE'd**

```c
xrGetCurrentFrameSequencePICO
```

External name: Pxr_GetCurrentFrameSequence <br>
Status: **To be RE'd**

```c
xrStartPHFHapticPICO
```

External name: Pxr_StartPHFHaptic <br>
Status: **To be RE'd**

```c
xrStopPHFHapticPICO
```

External name: Pxr_StopPHFHaptic <br>
Status: **To be RE'd**

```c
xrRemovePHFHapticPICO
```

External name: Pxr_RemovePHFHaptic <br>
Status: **To be RE'd**

```c
xrGetPHFStreamMemPICO
```

External name: Pxr_GetPHFStreamMem <br>
Status: **To be RE'd**

```c
xrGetHandTrackerSettingStatePICO
```

External name: Pxr_GetHandTrackerSettingState <br>
Status: **To be RE'd**

```c
xrGetHandTrackerActiveInputTypePICO
```

External name Pxr_GetHandTrackerActiveInputType <br>
Status: **To be RE'd**

```c
xrSetEyeTrackerModePICO
```

Status: **To be RE'd**

```c
xrGetEyeTrackerModePICO
```

External name: Pxr_GetTrackingMode <br>
Status: **To be RE'd**

```c
xrGetEyeTrackerDataPICO
```

Status: **To be RE'd**

```c
xrSetBodyTrackerStaticCalibStatePICO
```

External name: Pxr_SetBodyTrackingStaticCalibState <br>
Status: **To be RE'd**

```c
xrSetBodyTrackerModePICO
```

External name: Pxr_SetBodyTrackingMode <br>
Status: **To be RE'd**

```c
xrGetBodyTrackerPosePICO
```

External name: Pxr_GetBodyTrackingPose <br>
Status: **To be RE'd**

```c
xrGetBodyTrackerImuDataPICO
```

External name: Pxr_GetBodyTrackingImuData <br>
Status: **To be RE'd**

```c
xrGetBodyTrackerConnectStatePICO
```

External name: Pxr_GetBodyTrackingState <br>
Status: **To be RE'd**

```c
xrGetBodyTrackerBatteryPICO
```

External name: Pxr_GetFitnessBandBattery <br>
Status: **To be RE'd**

```c
xrGetBodyTrackerCalibStatePICO
```

External name: Pxr_GetFitnessBandCalibState <br>
Status: **To be RE'd**

```c
xrSetBodyTrackingAlgParamPICO
```

External name: Pxr_SetBodyTrackingAlgParam <br>
Status: **To be RE'd**

```c
xrSetIPDPICO
```

External name: Pxr_SetIPD <br>
Status: **To be RE'd**

```c
xrGetIPDPICO
```

External name: Pxr_GetIPD <br>
Status: **To be RE'd**

```c
xrSetTrackingIPDEnabledPICO
```

External name: Pxr_SetTrackingIPDEnabled <br>
Status: **To be RE'd**

```c
xrGetTrackingIPDEnabledPICO
```

External name: Pxr_GetTrackingIPDEnabled <br>
Status: **To be RE'd**

```c
xrGetEyeTrackingAutoIPDPICO
```

External name: Pxr_GetEyeTrackingAutoIPD <br>
Status: **To be RE'd**

```c
xrGetFrustumParametersPICO
```

External name: Pxr_GetFrustum <br>
Status: **To be RE'd**

```c
xrSetFrustumParametersPICO
```

External name: Pxr_SetFrustum <br>
Status: **To be RE'd**

```c
xrGetConfigPICO
```

External name: Pxr_GetConfig <br>
Status: **To be RE'd**

```c
xrSetConfigPICO
```

External name: Pxr_SetConfig <br>
Status: **To be RE'd**

```c
xrGetConfigsPICO
```

External name: Pxr_GetConfigs <br>
Status: **To be RE'd**

```c
xrSetConfigsPICO
```

External name: Pxr_SetConfigs <br>
Status: **To be RE'd**

```c
xrGetFoveationConfigPICO
```

External name: getFoveationConfig <br>
Status: **To be RE'd**

```c
xrGetMainClientInfoPICO
```

External name: Pxr_GetMainClientInfo <br>
Status: **To be RE'd**

```c
xrGetPerformanceInfoPICO
```

Status: **To be RE'd**

```c
xrResetSensorPICO
```

External name: Pxr_ResetSensor <br>
Status: **To be RE'd**

```c
xrSetTrackingModePICO
```

External name: Pxr_SetTrackingMode <br>
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

External name: Pxr_GetEyeTrackingData and Pxr_GetEyeTrackingData1 <br>
Status: **To be RE'd**

```c
xrGetTrackingModePICO
```

External name: Pxr_GetTrackingMode <br>
Status: **To be RE'd**

```c
xrGetFaceTrackingDataPICO
```

External name: Pxr_GetFaceTrackingState <br>
Status: **To be RE'd**

```c
xrGetEyeTrackingStatePICO
```

External name: Pxr_GetEyeTrackingState <br>
Status: **To be RE'd**

```c
xrGetFaceTrackingStatePICO
```

External name: Pxr_GetFaceTrackingState <br>
Status: **To be RE'd**

```c
xrGetPupilDistancePICO
```

External name: Pxr_GetPupilDistance <br>
Status: **To be RE'd**

```c
xrStartEyeTrackingPICO
```

External name: Pxr_StartEyeTracking <br>
Status: **To be RE'd**

```c
xrStopEyeTrackingPICO
```

External name: Pxr_StopEyeTracking <br>
Status: **To be RE'd**

```c
xrSetTrackingStatusPICO
```

External name: Pxr_SetTrackingStatus <br>
Status: **To be RE'd**

```c
xrGetEyeOpennessPICO
```

External name: Pxr_GetEyeOpenness <br>
Status: **To be RE'd**

```c
xrGetEyePupilInfoPICO
```

External name: Pxr_GetEyePupilInfo <br>
Status: **To be RE'd**

```c
xrGetPerEyePosePICO
```

External name: Pxr_GetPerEyePose <br>
Status: **To be RE'd**

```c
xrGetBlinkPICO
```

External name: Pxr_GetEyeBlink <br>
Status: **To be RE'd**

```c
xrSetControllerPositionPICO
```

External name: Pxr_SetControllerPosition <br>
Status: **To be RE'd**

```c
xrBoundaryTestNodePICO
```

External name: Pxr_BoundaryTestNode <br>
Status: **To be RE'd**

```c
xrBoundaryTestPointPICO
```

External name: Pxr_TestPointIsInBoundary <br>
Status: **To be RE'd**

```c
xrGetBoundaryGeometryPICO
```

External name: Pxr_GetBoundaryGeometry <br>
Status: **To be RE'd**

```c
xrGetBoundaryDimensionsPICO
```

External name: Pxr_GetBoundaryDimensions <br>
Status: **To be RE'd**

```c
xrGetSeeThroughDataPICO
```

External name: Pxr_GetSeeThroughData <br>
Status: **To be RE'd**

```c
xrInvokeFunctionsPICO
```

External name: Pxr_InvokeFunctions <br>
Status: **To be RE'd**

```c
xrStartMRModeBD
```

External name: Pxr_StartMRMode <br>
Status: **To be RE'd**

```c
xrStopMRModeBD
```

External name: Pxr_StopMRMode <br>
Status: **To be RE'd**

```c
xrStopSpatialRecognitionBD
```

External name: Pxr_StopSpatialRecognition <br>
Status: **To be RE'd**

```c
xrSetMrConfigurationBD
```

External name: Pxr_SetMrConfiguration <br>
Status: **To be RE'd**

```c
xrCreateSpatialAnchorSpaceBD
```

External name: Pxr_CreateSpatialAnchor <br>
Status: **To be RE'd**

```c
xrDestroySpatialAnchorBD
```

External name: Pxr_DestroySpatialAnchor <br>
Status: **To be RE'd**

```c
xrSetSpatialAnchorPropertyBD
```

External name: Pxr_SetSpatialAnchorProperty <br>
Status: **To be RE'd**

```c
xrGetSpatialAnchorPropertyBD
```

External name: Pxr_GetSpatialAnchorProperty <br>
Status: **To be RE'd**

```c
xrSetSpatialAnchorTagBD
```

External name: Pxr_SetSpatialAnchorTag <br>
Status: **To be RE'd**

```c
xrGetSpatialAnchorTagBD
```

External name: Pxr_GetSpatialAnchorTag <br>
Status: **To be RE'd**

```c
xrGetSpatialAnchorUuidBD
```

External name: Pxr_GetSpatialAnchorUuid <br>
Status: **To be RE'd**

```c
xrSaveSpatialAnchorBD
```

External name: Pxr_SaveSpatialAnchor <br>
Status: **To be RE'd**

```c
xrDeleteSpatialAnchorBD
```

External name: Pxr_DeleteSpatialAnchor <br>
Status: **To be RE'd**

```c
xrLoadSpatialAnchorByIdBD
```

External name: Pxr_LoadSpatialAnchorById <br>
Status: **To be RE'd**

```c
xrGetSpatialAnchorLoadResultsBD
```

External name: Pxr_GetSpatialAnchorLoadResults <br>
Status: **To be RE'd**

```c
xrExportSpatialInstanceBD
```

External name: Pxr_ExportSpatialInstance <br>
Status: **To be RE'd**

```c
xrImportSpatialInstanceBD
```

External name: Pxr_ImportSpatialInstance <br>
Status: **To be RE'd**

```c
xrStartRoomCaptureBD
```

External name: Pxr_StartRoomCapture <br>
Status: **To be RE'd**

```c
xrCreateRoomSceneDataBD
```

External name: Pxr_CreateRoomSceneData <br>
Status: **To be RE'd**

```c
xrDestroyRoomSceneDataBD
```

External name: Pxr_DestroyRoomSceneData <br>
Status: **To be RE'd**

```c
xrSaveRoomSceneDataBD
```

External name: Pxr_SaveRoomSceneData <br>
Status: **To be RE'd**

```c
xrStartHumanOcclusionBD
```

External name: Pxr_StartHumanOcclusion <br>
Status: **To be RE'd**

```c
xrAcquire_occlusion_infoBD
```

External name Pxr_AcquireMeshingInfo <br>
Status: **To be RE'd**

```c
xrStopHumanOcclusionBD
```

External name: Pxr_StopHumanOcclusion <br>
Status: **To be RE'd**

```c
xrGetMrcPosePICO
```

External name: Pxr_GetMrcPose <br>
Status: **To be RE'd**

```c
xrSetMrcPosePICO
```

External name: Pxr_SetMrcPose <br>
Status: **To be RE'd**

```c
xrSetIsSupportMovingMrcPICO
```

External name: Pxr_SetIsSupportMovingMrc <br>
Status: **To be RE'd**

```c
xrGetExternalCameraInfoBD
```

External name: Pxr_GetExternalCameraInfo <br>
Status: **To be RE'd**

```c
xrPassthroughLayerSetStylePICO
```

External name: Pxr_SetPassthroughStyle <br>
Status: **To be RE'd**

```c
xrCreateAnchorEntityBD
```

External name: Pxr_CreateAnchorEntity <br>
Status: **To be RE'd**

```c
xrDestroyAnchorEntityBD
```

External name: Pxr_DestroyAnchorEntity <br>
Status: **To be RE'd**

```c
xrCreateAnchorSpaceBD
```

External name: Pxr_CreateAnchorEntity <br>
Status: **To be RE'd**

```c
xrGetAnchorEntityUuidBD
```

External name: Pxr_GetAnchorEntityUuid <br>
Status: **To be RE'd**

```c
xrAddAnchorComponentBD
```

External name: Pxr_AddAnchorComponent <br>
Status: **To be RE'd**

```c
xrRemoveAnchorComponentBD
```

External name: Pxr_RemoveAnchorComponent <br>
Status: **To be RE'd**

```c
xrGetAnchorComponentFlagsBD
```

External name: Pxr_GetAnchorComponentFlags <br>
Status: **To be RE'd**

```c
xrGetAnchorSceneLabelBD
```

External name: Pxr_GetAnchorSceneLabel <br>
Status: **To be RE'd**

```c
xrGetAnchorPlaneBoundaryInfoBD
```

External name: Pxr_GetAnchorPlaneBoundaryInfo <br>
Status: **To be RE'd**

```c
xrGetAnchorPlanePolygonInfoBD
```

External name: Pxr_GetAnchorPlanePolygonInfo <br>
Status: **To be RE'd**

```c
xrGetAnchorBoxInfoBD
```

External name: Pxr_GetAnchorBoxInfo <br>
Status: **To be RE'd**

```c
xrPersistAnchorEntityBD
```

External name: Pxr_PersistAnchorEntity <br>
Status: **To be RE'd**

```c
xrUnpersistAnchorEntityBD
```

External name: Pxr_UnpersistAnchorEntity <br>
Status: **To be RE'd**

```c
xrClearPersistedAnchorEntityBD
```

External name: Pxr_ClearPersistedAnchorEntity <br>
Status: **To be RE'd**

```c
xrLoadAnchorEntityBD
```

External name: Pxr_LoadAnchorEntity <br>
Status: **To be RE'd**

```c
xrGetAnchorEntityLoadResultsBD
```

External name: Pxr_GetAnchorEntityLoadResults <br>
Status: **To be RE'd**

```c
xrStartSemiAutoRoomCaptureBD
```

External name: Pxr_StartSemiAutoRoomCapture <br>
Status: **To be RE'd**

```c
xrStopSemiAutoRoomCaptureBD
```

External name: Pxr_StopSemiAutoRoomCapture <br>
Status: **To be RE'd**

```c
xrSetFloorHeightBD
```

External name: Pxr_SetFloorHeight <br>
Status: **To be RE'd**

```c
xrSetCeilingHeightBD
```

External name: Pxr_SetCeilingHeight <br>
Status: **To be RE'd**

```c
xrSetFloorCornerBD
```

External name: Pxr_SetFloorCorner <br>
Status: **To be RE'd**

```c
xrGetSemiAutoRoomCaptureCandidatesBD
```

External name: Pxr_GetSemiAutoRoomCaptureCandidates <br>
Status: **To be RE'd**

```c
xrGetSpatialTrackingStateBD
```

External name: Pxr_GetSpatialTrackingState <br>
Status: **To be RE'd**

```c
xrBeginSpatialLocalizationBD
```

External name: Pxr_BeginSpatialLocalization <br>
Status: **To be RE'd**

```c
xrEndSpatialLocalizationBD
```

External name: Pxr_EndSpatialLocalization <br>
Status: **To be RE'd**

```c
xrBeginSpatialMapCreationBD
```

External name: Pxr_BeginSpatialMapCreation <br>
Status: **To be RE'd**

```c
xrEndSpatialMapCreationBD
```

External name: Pxr_EndSpatialMapCreation <br>
Status: **To be RE'd**

```c
xrStartSpatialSceneCaptureBD
```

External name: Pxr_StartSpatialSceneCapture <br>
Status: **To be RE'd**
