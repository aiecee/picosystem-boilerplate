cmake_minimum_required(VERSION 3.13)

include(pico-sdk/pico_sdk_init.cmake)

project(game C CXX ASM)

include(picosystem/picosystem-config.cmake)

picosystem_executable(
  game
  src/game.cpp
)

pixel_double(game)
disable_startup_logo(game)