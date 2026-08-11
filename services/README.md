# Services
`service list`
- ConfigurationService
- gd32ipdservice
- native_shell
- nettools
- PicoStation-new
- [pvr_manager](#pvr_manager)
- pvrtracking
- pxr_init_service
- pxr_net
- pxr_notification
- pxrcontrollerservice
- [pxreyetrackingservice](#pxreyetrackingservice)
- pxrfanservice
- [pxrhmdservice](#pxrhmdservice)
- pxrmedia.metrics
- pxrmrsystemservice
- pxrseethroughservice
- xrtruntime

Functions are written order of their transaction code, unless specified otherwise.
Most services are written in AIDL, however most of it is pseudocode!
## Testing
You can test a binder via `adb`:
```shell
$ adb shell
$ service call [service_name] [index] [type] [arguments]
```
eg:
```shell
$ service call pvr_manager 9 i32 0 i32 0
Result: Parcel(00000000    '....')
```

# ConfigurationService
Interface: com.pvr.configuration.IConfigServiceInterface

IConfigServiceInterface:
```C++
string getConfigPropertyDirectAccess(int param_0, String param_1, String param_2);
//TODO
```

# pvr_manager
Interface: com.pvr.IPvrManagerService    
Location: /system/app/PvrManager/PvrManager.apk  

IPvrManagerService:
```java
interface IPvrManagerService {
    //System apps only.
    boolean setSystemFeatures(int featureId, String featureValue, IBinder token); //1
    //System apps only.
    boolean addSystemService(String name, IBinder binder, IBinder token); //2
    //System apps only.
    String getSystemFeatures(String featureId, IBinder token); //3
    
    void addPvrCallback(String className, IPvrCallback pcb, int type); //4
    void removePvrCallback(String className); //5
    void sendPvrMessage(String event, String value, int type); //6
    
    void updateUserSettings(String countryCode); //7
    int getScreenBrightnessLevel(); //8
    void setCurrentScreenBrightnessLevel(int vrBrightness, int setLevel); //9
    void setLedStatus(int led, int color, int blink, int ontime, int offtime); //10
    int getHeadstrapStatus(); //11
    
    void addPvrCallbacks(IPvrCallback callback); //12
    void removePvrCallbacks(int pid); //13
    //System apps only.
    void sendPvrMessages(String event, String value); //14
    void updateDistributionChannel(String distributionChannel, boolean manuallyModified); //15
}
```
IPvrCallback:
```java
interface IPvrCallBack {
    void onEventChanged(Bundle param_1)
}
```

# pxreyetrackingservice
Interface: pvr.IEyeTrackingService   
Runs-as: root (native C++)  
Location: /system/lib/libpxreyetrackingservice.pxr.so  

```java
interface IPxrEyeTrackingService {
	// NOOP
    int Initialize(String param_1); //1
    int SetTrackingMode(int param_1); //2
    // NOOP
    int ResetTracking(int param_1, int param_2); //3
    // NOOP
    int Start(String param_1); //4
    // NOOP
    int Stop(String param_1); //5
    // parameters: 
    // Bit 2: openEyeCamera
    // Bit 3: openFaceCamera
    // Bit 12: IpdAlgoStarted
    // Bit 13: Face tracking flag?
    // Bit 14: Eye tracking calibration
    int StartAlgorithm(int cameraId, String parameters, int timeoutMs); //6
    // Keys: ipd_position, ft_lipsync_ctl, et_calib_position, et_calib_stop
    int SetAlgorithmParameters(int type, String key, String value); //7
    // Keys: mode, et_running, ft_lipsync_running, ft_running, lipsync_running
    int GetAlgorithmResult(int param_1, String key, out int param_3); //8
    // parameters:
    // Bit 2: Close eye tracking
    // Bit 3: Close face tracking
    int StopAlgorithm(int cameraId, int parameters); //9
    // UUID <= 1000
    // Keys: led_mode, brightness, width, height, format, fps, exposure_gain, flash, exposure, gain, face_led_brightness, single_id, torch, led_cross_lighted, keep_camera_opened
    int SetCameraParameters(int cameraId, String key, String value); //10
    void AddServiceListener(sp param_1); //11, SP: StrongBinder / Strong Pointer
    void RemoveServiceListener(sp param_1); //12
    // UUID <= 1000
    int OpenCamera(int cameraId, out DataBufferParcelable cameraFrameSharedMemoryFd); //13
    // UUID <= 1000
    void StartPreview(int cameraId); //14
    // UUID <= 1000
    void StopPreview(int cameraId); //15
    void CloseCamera(int cameraId); //16
    // UUID <= 1000
    Vector GetCameraParameters(String param_1); //17
    //Returns File Descriptor to shared memory, datatype: RingBuffer.
    // Type 1: 50 slots of pxr_eyepose: 168 bytes
    // Type 2: 50 slots of pxr_eyepose_data_v2_0: 200 bytes
    // Type 3: 5 slots of PicoFTInfo: 896 bytes
    int GetTrackingDataSharedMemory(int type, out DataBufferParcelable param_2); //18
    // UUID <= 1000
    int GetCameraFrameSharedMemory(int cameraId, out DataBufferParcelable param_2); //19
    // UUID <= 1000
    void SetCameraErrorListener(int param_1); //20
    // UUID <= 1000
    // NOOP?
    int AddToSpecifiedList(int param_1); //21
    int SetData(int param_1, Vector param_2); //22
    int GetData(int param_1, out Vector param_2); //23
    // Note: Hardcoded, always returns 0.0f.
    float GetPupilDistance(); //24
    boolean HasEyeCamera(); //25
    void RegisterIPDCallback(int param_1); //26
    void SetIPD(float param_1); //27
    void FinishIPDCalibration(int param_1, bool param_2); //28
}
```

Eye tracking service listener:
Interface: pvr.IEyeTrackingServiceListener

```java
interface BpEyeTrackingServiceListener {
	void onFrameAvailable(int param_1, int param_2, int param_3); //1
	void onAlgorithmResultsAvailable(int param_1, int param_2); //2
	void onDeviceError(int param_1, int param_2); //3
	void onIPDAvailable(bool param_1, float param_2); //4
	void onGlassWearableAvailable(bool param_1, int param_2); //5
	void onIPDFullDataAvailable(out Vector param_1, out Vector param_2, int param_3, float param_4); //6
}
```
# pxrhmdservice
Interface: android.Service.PxrHmdService  
Runs-as: root (native C++)  
Location: /system/lib/libpxrhmdservice.so  

TODO.