cmake_minimum_required(VERSION 3.13)

project(hello-world)

picosystem_executable(
  hello-world
  HelloWorld.cpp
)

pixel_double(hello-world)
disable_startup_logo(hello-world)