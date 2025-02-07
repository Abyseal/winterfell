cmake_minimum_required(VERSION 3.14)
project(Winterfell 
  VERSION 1.0
  LANGUAGES CXX)

include(FetchContent)
FetchContent_Declare(
  spdlog
  GIT_REPOSITORY https://github.com/gabime/spdlog.git
  GIT_TAG v1.11.0
)
FetchContent_MakeAvailable(spdlog)

add_library(Winterfell STATIC
  src/winterfell.cpp)

target_include_directories(Winterfell
  PUBLIC include)
target_link_libraries(Winterfell PUBLIC spdlog::spdlog)

install(TARGETS Winterfell
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin)

install(DIRECTORY include/ DESTINATION include)

