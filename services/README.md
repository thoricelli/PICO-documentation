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
- pxrhmdservice
- pxrmedia.metrics
- pxrmrsystemservice
- pxrseethroughservice
- xrtruntime

# ConfigurationService
Interface: com.pvr.configuration.IConfigServiceInterface

IConfigServiceInterface:
```java
String getConfigPropertyDirectAccess(int param0, String param1, String param2);
//TODO
```

# pvr_manager
Interface: com.pvr.IPvrManagerService  
Location: /system/app/PvrManager/PvrManager.apk

IPvrManagerService:
```java
boolean setSystemFeatures(int param1, in String param2, in IBinder param3);
boolean addSystemService(in String param1, in IBinder param2, in IBinder param3);
String getSystemFeatures(in String param1, in IBinder param2);
void addPvrCallback(in String param1, in IPvrCallback callback, int param3);
void removePvrCallback(in String param1);
void sendPvrMessage(in String param1, in String param2, int param3);
void updateUserSettings(in String param1, boolean param2);
int getScreenBrightnessLevel();
void setCurrentScreenBrightnessLevel(int param1, int param2);
void setLedStatus(int param1, int param2, int param3, int param4, int param5);
int getHeadstrapStatus();
void addPvrCallbacks(in IPvrCallback callback);
void removePvrCallbacks(int param1);
void sendPvrMessages(in String param1, in String param2);
void updateDistributionChannel(in String param1, boolean param2);
```
IPvrCallback:
```java
void onEventChanged(Bundle param1)
```

# pxreyetrackingservice
Interface: pvr.IEyeTrackingService  
Location: /system/lib/libpxreyetrackingservice.pxr.so