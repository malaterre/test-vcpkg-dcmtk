cmake_minimum_required(VERSION 3.25)
project(
  test-vcpkg-dcmtk
  VERSION 1.0.0
  LANGUAGES CXX)

find_package(DCMTK CONFIG REQUIRED)
add_library(foo SHARED foo.cxx)
target_link_libraries(foo PRIVATE DCMTK::DCMTK)