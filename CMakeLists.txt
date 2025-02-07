cmake_minimum_required(VERSION 3.14)
project(Winterfell 
  VERSION 1.0
  LANGUAGES CXX)


include(FetchContent)
FetchContent_Declare(
        spdlog
        URL https://github.com/gabime/spdlog/archive/refs/tags/v1.13.0.zip
)

FetchContent_MakeAvailable(spdlog)


add_library(Winterfell STATIC
  src/winterfell.cpp)
add_library(winterfell::winterfell ALIAS Winterfell)


target_include_directories(Winterfell
  PUBLIC include)
target_link_libraries(Winterfell PUBLIC spdlog::spdlog)

install(TARGETS Winterfell
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin)

install(DIRECTORY include/ DESTINATION include)

