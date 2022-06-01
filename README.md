# Flycast-Libretro-Xbox-Builds
This repository just contains libretro builds of [Flycast](https://github.com/flyinghead/flycast) that only have DirectX 11 enabled. As the name of the repo implies, these are primarily intended to be used with Xbox consoles, but can also be used on Windows devices with DX11 installed.

All credit goes to [flyinghead](https://github.com/flyinghead) for this awesome emulator.

# Build Instructions

Should you wish to make a DX11 libretro build of Flycast, here's some instructions of how you can do so.

You will need to have [MSYS2](https://www.msys2.org/) installed alongside the following packages:
- [mingw-w64-x86_64-toolchain](https://packages.msys2.org/group/mingw-w64-x86_64-toolchain)
- [git](https://packages.msys2.org/base/git)
- [ccache](https://packages.msys2.org/package/mingw-w64-x86_64-ccache?repo=mingw64)
- [CMake](https://packages.msys2.org/package/mingw-w64-x86_64-cmake?repo=mingw64)
- [Lua](https://packages.msys2.org/package/mingw-w64-x86_64-lua?repo=mingw64)
- [SDL2](https://packages.msys2.org/package/mingw-w64-x86_64-SDL2?repo=mingw64)

Open MSYS2 (**MAKE SURE YOU OPEN THE MINGW x64 VARIANT**), then type the following command: `git clone --recurse-submodules https://github.com/flyinghead/flycast.git`
This will fetch the repository for you alongside the required submodules.

Now, use `cd flycast` to access the repository, where we will generate the build files using CMake.

![image](https://user-images.githubusercontent.com/35014183/171508503-12237b84-e768-4875-b7b0-5b7ca4063c41.png)

Type the following command to generate the build files: `cmake -B build -DLIBRETRO=ON -DUSE_VULKAN=OFF -DUSE_OPENGL=OFF -DCMAKE_BUILD_TYPE=Release -G "MinGW Makefiles"`
Then sit down and relax while the files are generated.

![image](https://user-images.githubusercontent.com/35014183/171509756-42463c29-ddd1-47d6-9526-a0de1a5781a4.png)

Finally, use this command to build the core: `cmake --build build --config Release -- -j4`

![image](https://user-images.githubusercontent.com/35014183/171515084-8a1310b2-23d9-432f-882a-3dd3805ef67f.png)

You should have a file called `flycast_libretro.dll` inside the `flycast/build` directory.
