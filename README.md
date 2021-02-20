# V-EZ

V-EZ is an open source, cross-platform wrapper intended to alleviate the inherent complexity and application responsibility of using the Vulkan API. V-EZ attempts to bridge the gap between traditional graphics APIs and Vulkan by providing similar semantics to Vulkan while lowering the barrier to entry and providing an easier to use API.

![](https://raw.githubusercontent.com/GPUOpen-LibrariesAndSDKs/V-EZ/master/Docs/img/VulkanAPI.PNG)

![](https://raw.githubusercontent.com/GPUOpen-LibrariesAndSDKs/V-EZ/master/Docs/img/V-EZ.PNG)

Original repository: https://github.com/GPUOpen-LibrariesAndSDKs/V-EZ

This repository is supported by `PRIME-tech OSS` in order to develop an active community version due to lack of maintenance of the original.
See discussion on [GitHub](https://github.com/GPUOpen-LibrariesAndSDKs/V-EZ/issues/73).
Old version is on branch `original` of this repo for developers to compare changes and merge back to GPUOpen in the future if possible.

## Main changes

- Visual Studio is not supported due to development workflow of PRIME-tech's core team. Merge requests (MR) for VS-related issues is welcomed.
- Ported & tested on multiple platforms, priority as follows: Linux (Ubuntu LTS), Windows 10, iOS, Android, MacOS.

## Projects using V-EZ
(Open an MR or Issue to add yours)

- [Saga3D](https://gitlab.com/PRIME-tech-OSS/Saga3D): minimal, simple and cross-platform library for modern graphics

## Documentation

The documentation for V-EZ can be found [here](https://gpuopen-librariesandsdks.github.io/V-EZ/).

## Prerequisites

- GCC 4.9 or later
- CMake 3.8 or later
- LunarG Vulkan SDK 1.1.70 or later

## Building V-EZ

- Run cmake to generate Visual Studio solution files or Linux make files. No specific settings need to be set.

- Pull down submodules

`git submodule init`

`git submodule update`

- Build V-EZ project

### Build for Android

```
export NDK_PATH=_YOUR_ABSOLUTE_PATH_/ndk-bundle/
export CMAKE_TOOLCHAIN=$NDK_PATH/build/cmake/android.toolchain.cmake

mkdir build
cd build

cmake .. -DCMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN} \
-DCMAKE_SYSTEM_NAME=Android \
-DCMAKE_ANDROID_NDK=${NDK_PATH} \
-DANDROID_FORCE_ARM_BUILD=TRUE \
-DANDROID_STL=c++_shared \
-DANDROID_TOOLCHAIN=clang \
-DANDROID_NATIVE_API_LEVEL=27 \
-DCMAKE_ANDROID_ARCH_ABI=armeabi-v7a \
-DCMAKE_INSTALL_PREFIX=$PWD/install \
-DVEZ_COMPILE_SAMPLES=OFF \
-DCMAKE_BUILD_TYPE=Release

make -j4 install
```

### Build for MacOS / iOS

Instructions will be updated, we haven't worked on Apple's platforms recently since the last testing.

The project is subjected to work on MacOS / iOS. If someone could try building, feel free to open MR or Issue and add some build commands examples.
