# PicoSystem C++ Boilerplate

This is a quick and dirty boilerplate repo to get you started quickly developing games for the PicoSystem.

## Getting Started

1. Install the tool chain.
```
$ sudo apt update
$ sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib build-essential
```

2. Update the submodules.
This pulls in [Raspberry Pi's Pico SDK](https://github.com/raspberrypi/pico-sdk), [Pimoroni's PicoSystem Sdk](https://github.com/raspberrypi/pico-sdk) and pulls [TinyUSB](https://github.com/hathach/tinyusb) into pico-sdk.
```
$ git submodule update --init
$ cd pico-sdk
$ git submodule update --init
$ cd ..
```

3. Create the build folder and build hello-world.
After making you'll be able to drag the `build/games/hello-world/hello-world.uf2` into the PicoSystem when it's booted into [DFU mode](https://github.com/pimoroni/picosystem#booting-picosystem-into-dfu-mode).
```
$ mkdir build
$ cd build
$ cmake ..
$ make -j8
```

## Adding your own games

1. Create a new folder under games.
```
$ mkdir games/new-game
```

2. Create your game entry file in the new folder, the following can be used as a template.
```
#include "picosystem.hpp"

using namespace picosystem;

void init()
{
}

void update(uint32_t time_ms)
{
}

void draw()
{
}
```

3. Create a new CMakeLists.txt in the new folder, the following can be used as a template.
```
cmake_minimum_required(VERSION 3.13)

project({ProjectName})

picosystem_executable(
  {ProjectName}
  {GameFile}.cpp
)

pixel_double({ProjectName})
disable_startup_logo({ProjectName})
```
Replacing {ProjectName} with the name of the project and {GameFile} with the name of the file created in the previous step.

4. Add the new folder into the `games/CMakeLists.txt`
```
add_subdirectory(hello-world)
add_subdirectory({NewFolder})
```

5. Write your game!

6. Build your game.
After making you'll be able to drag the `build/games/{ProjectName}/{ProjectName}.uf2` into the PicoSystem when it's booted into [DFU mode](#booting-picosystem-into-dfu-mode).
```
$ cd build
$ cmake ..
$ make -j8
```