cmake_minimum_required(VERSION 3.25)
project(
  test-vcpkg-dcmtk
  VERSION 1.0.0
  LANGUAGES CXX)

find_package(DCMTK CONFIG REQUIRED)
add_library(foo SHARED foo.cxx)
# https://github.com/microsoft/vcpkg/issues/31395#issuecomment-1571881282
target_compile_options(foo PUBLIC "/Zc:__cplusplus")
# https://github.com/microsoft/vcpkg/blob/8c9416f/ports/dcmtk/portfile.cmake#L32
set_property(TARGET foo PROPERTY CXX_STANDARD 17)
target_link_libraries(foo PRIVATE DCMTK::DCMTK)
