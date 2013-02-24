CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(hello)

SET(hello_VERSION_MAJOR 1)
SET(hello_VERSION_MINOR 1)

ADD_LIBRARY(hello hello.cpp)

SET(hello_VERSION_STRING  "${hello_VERSION_MAJOR}.${hello_VERSION_MINOR}")
SET(hello_DIRNAME         "hello-${hello_VERSION_STRING}")
SET(hello_DIRNAME_lib     "lib/${hello_DIRNAME}")
SET(hello_DIRNAME_include "include/${hello_DIRNAME}")

INCLUDE(CMakePackageConfigHelpers)

CONFIGURE_PACKAGE_CONFIG_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/helloConfig.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/helloConfig.cmake"
  INSTALL_DESTINATION
    ${hello_DIRNAME_lib}
  PATH_VARS
    hello_DIRNAME_lib
    hello_DIRNAME_include
  )

INSTALL(
  TARGETS
    hello
  DESTINATION
    ${hello_DIRNAME_lib}
  EXPORT
    helloExports
  )

INSTALL(
  EXPORT
    helloExports
  DESTINATION
    ${hello_DIRNAME_lib}
  )

INSTALL(
  FILES
    ${CMAKE_CURRENT_BINARY_DIR}/helloConfig.cmake
  DESTINATION
    ${hello_DIRNAME_lib}
  )

INSTALL(
  FILES
    hello.h
  DESTINATION
    ${hello_DIRNAME_include}/hello
  )
