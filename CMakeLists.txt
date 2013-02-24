CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(hello)

set (hello_VERSION_MAJOR 1)
set (hello_VERSION_MINOR 1)

ENABLE_TESTING()

ADD_LIBRARY(hello hello.cpp)

CONFIGURE_FILE(helloConfig.cmake.in helloConfig.cmake)

INSTALL(
  TARGETS
  hello
  DESTINATION
  lib/hello-${hello_VERSION_MAJOR}.${hello_VERSION_MINOR}
  )

INSTALL(
  FILES
  helloConfig.cmake
  DESTINATION
  lib/hello-${hello_VERSION_MAJOR}.${hello_VERSION_MINOR}
  )

INSTALL(
  FILES
  hello.h
  DESTINATION
  include/hello-${hello_VERSION_MAJOR}.${hello_VERSION_MINOR}
  )
