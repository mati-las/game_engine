cmake_minimum_required(VERSION 3.30)
project(game_engine)

set(CMAKE_CXX_STANDARD 20)

include(FetchContent)

FetchContent_Declare(
        googletest
        URL https://github.com/google/googletest/archive/refs/heads/main.zip
)
set(INSTALL_GTEST OFF)
FetchContent_MakeAvailable(googletest)

set(SOURCE_FILES
        src/Game.cpp
        src/GameObject.cpp
)

add_library(game_engineLib ${SOURCE_FILES})
target_include_directories(game_engineLib PUBLIC include)

if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/main.cpp")
    add_executable(game_engine main.cpp)
    target_link_libraries(game_engine game_engineLib)
endif()


