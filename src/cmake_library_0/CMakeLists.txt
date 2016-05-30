cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

enable_testing()

project(cmake_library_0 VERSION 0.1 LANGUAGES CXX)

add_library(library_0 src/src.cpp)

target_include_directories(library_0 PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
  PRIVATE src)

install(TARGETS library_0
  ARCHIVE  DESTINATION lib
  LIBRARY  DESTINATION lib
  RUNTIME  DESTINATION bin)
install(DIRECTORY include/ DESTINATION include)

add_executable(test0 tests/test0.cpp)

target_link_libraries(test0 library_0)

add_test(test0 test0)
