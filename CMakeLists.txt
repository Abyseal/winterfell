cmake_minimum_required(VERSION 3.14)

project(Winterfell VERSION 1.0 LANGUAGES CXX)
message(STATUS "Build Winterfell: ${Winterfell_VERSION}")


option(NOT_FETCH_SPDLOG "turn off if your project don't use spdlog elsewhere" ON)

if(NOT_FETCH_SPDLOG)
  include(FetchContent)
  FetchContent_Declare(
          spdlog
          URL https://github.com/gabime/spdlog/archive/refs/tags/v1.13.0.zip
  )
  FetchContent_MakeAvailable(spdlog)
endif()

#If no <type> is given the default is STATIC or SHARED based on the value of the BUILD_SHARED_LIBS variable.
add_library(Winterfell src/winterfell.cpp)

target_include_directories(Winterfell PUBLIC include)
target_link_libraries(Winterfell PUBLIC spdlog::spdlog)

# add_library(winterfell::winterfell ALIAS Winterfell)

#not tested. need sudo, to write to system folders
# install(TARGETS Winterfell
#  LIBRARY DESTINATION lib
#  ARCHIVE DESTINATION lib
#  RUNTIME DESTINATION bin)
#
# install(DIRECTORY include/ DESTINATION include)

