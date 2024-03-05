
set(CMAKE_CXX_STANDARD 14)

include_directories(Game)

cmake_minimum_required(VERSION 3.7)
set(PROJECT_NAME DaveStation)

project(${PROJECT_NAME})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -static")

set(CMAKE_CXX_STANDARD 14)

set(SOURCE_FILES main.cpp  Game/Game.cpp Game/Game.h Game/Game_Interface.cpp  Game/Game_Interface.h  Game/GameText.cpp  Game/GameText.h   Game/Thumbnail.cpp Game/Thumbnail.h SpaceShooter/SpaceShooter.cpp SpaceShooter/SpaceShooter.h cmake-build-debug/Player.cpp SpaceShooter/Player.cpp SpaceShooter/Player.h SpaceShooter/Projectile.cpp SpaceShooter/Projectile.h SpaceShooter/Enemy.cpp SpaceShooter/Enemy.h)

if (CMAKE_BUILD_TYPE STREQUAL "Release")
    add_executable(${PROJECT_NAME} WIN32 ${SOURCE_FILES})
else ()
    add_executable(${PROJECT_NAME} ${SOURCE_FILES})
endif ()

set(SFML_ROOT C:/SFML-2.5.1)
set(SFML_STATIC_LIBRARIES TRUE)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake_modules")
#set(SFML_DIR C:/SFML/SFML-2.5.1/lib/cmake/SFML)
find_package(SFML  REQUIRED COMPONENTS audio graphics window system)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(${PROJECT_NAME} ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
endif ()