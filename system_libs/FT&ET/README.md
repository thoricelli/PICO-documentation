# Face & eye trackng

This file will contain the documentation for the eye and face tracking aspect of the PICO 4 P/E.

The libraries that are responsible for it's tracking:

- /system/lib/libeyetrackingclient.pxr.so
  - Contains listener class for libpxreyetracking.phoenix.so.
- /system/lib/libpxreyetrackingservice.pxr.so
  - Service that controls camera, LED, etc.
- /system/lib/libpxreyetracking.phoenix.so
  - Actually gets the eye and face tracking data (using OpenCV?) and puts it into a buffer using OpenCL shared memory.

## How to call a system library

```cpp
#include <dlfcn.h>

//Opens a system library within /system/lib, /system/lib64, etc...
void* handle = dlopen("systemlibrary.so", RTLD_GLOBAL | RTLD_NOW | RTLD_LAZY);

//Get function pointer.
void* function = dlsym(handle, "FunctionName");

//Cast function pointer to your function signature.
bool (*pFunction)(int* param_1, float* param_2) = (bool (*)(int*, float*))function

//Call the function.
bool value = function(0, 0.0);
```

Replace `systemlibrary.so` and `FunctionName`. <br>
See [dlopen](https://man7.org/linux/man-pages/man3/dlopen.3.html) and [dlsym](https://man7.org/linux/man-pages/man3/dlsym.3.html).

## TODO

API reference for calling these system classes is a TODO!

# Binder

A way to communicate between Android services.

The android service for eyetracking is: `pxreyetrackingservice` with interface `pvr.IEyeTrackingService`.

## Binder

RE note: The IEyeTrackingService checks read-only property `ro.pxr.externalfunc` to check if the device is an Enterprise device or not. Depending on the result it might not include certain data.

IEyeTrackingService:

- Initialize (1)
- SetTrackingMode (2)
- ResetTracking (3)
- Start
- Stop
- StartAlgorithm (6)
- SetAlgorithmParameters
- GetAlgorithmResult
- StopAlgorithm (9)
- SetCameraParameters
- AddServiceListener
- RemoveServiceListener
- OpenCamera
- StartPreview
- StopPreview
- CloseCamera
- GetCameraParameters (17)
- GetTrackingDataSharedMemory
- GetCameraFrameSharedMemory
- SetCameraErrorListener (20)
- AddToSpecifiedList (21)
- SetData
- GetData
- GetPupilDistance
- hasEyeCamera
- RegisterIPDCallback (26)
- SetIPD (27)
- FinishIPDCalibration (28)
