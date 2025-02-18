# Face & eye trackng

This file will contain the documentation for the eye and face tracking aspect of the PICO 4 P/E.

The eye tracking on the PICO 4 PRO and Enterprise models are provided by [Tobii](https://www.tobii.com/).

The libraries that are responsible for it's tracking:

- /system/lib/libeyetrackingclient.pxr.so
  - ???
- /system/lib/libpxreyetrackingservice.pxr.so
  - Contains listener class for libpxreyetracking.phoenix.so which reads the buffer libpxreyetracking.phoenix listens to.
- /system/lib/libpxreyetracking.phoenix.so
  - Actually gets the eye and face tracking data (using OpenCV?) and puts it into a buffer (where? No clue!).

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
