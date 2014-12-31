Mesa_Android-x86_experimental
=============================

Experimental Mesa repository for Android-x86

 * * *
 
 This repository contains Mesa (currently 10.4.0) + changes to allow compiling on Android-x86 (Kitkat).
 
 Important Note: Had to include a prebuilt library (libstdc++ 4.8, bundled with Kitkat) using this procedure 
 before compiling Mesa:
 
1) Created a directory under "external" and named it "maledeto_tr1"

2) Inside the created directory, created an "Android.mk" file with the following content (included gcc 4.8 lib as a prebuilt shared lib):

include $(CLEAR_VARS)
LOCAL_MODULE := libgnustl_shared
LOCAL_MODULE_TAGS := optional
LOCAL_SRC_FILES := ../../prebuilts/ndk/9/sources/cxx-stl/gnu-libstdc++/4.8/libs/x86/libgnustl_shared.so
LOCAL_MODULE_CLASS := SHARED_LIBRARIES
LOCAL_MODULE_SUFFIX := $(TARGET_SHLIB_SUFFIX)
include $(BUILD_PREBUILT)

3) Executed "mm" inside this directory to "build" the lib

4) Removed the directory "maledeto_tr1" from external (At first I wanted to keep it to automate this step, but had problems during linkage)
 
* * *

This is meant for testing purposes only...
