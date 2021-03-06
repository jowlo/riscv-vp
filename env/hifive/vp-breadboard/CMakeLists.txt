project(vp-breadboard) # Your project name

set(CMAKE_CXX_STANDARD 11) # This is equal to QMAKE_CXX_FLAGS += -std=c++0x

cmake_minimum_required(VERSION 3.1.0)

# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)


find_package(Qt5Widgets CONFIG REQUIRED)

include_directories(../../../vp/src/platform/hifive/)

set(HEADERS mainwindow.h)

set(UI mainwindow.ui)

set(RESOURCES resources.qrc)

set(SOURCES
    main.cpp
    mainwindow.cpp
    ../../../vp/src/platform/hifive/gpio/gpiocommon.cpp
    ../../../vp/src/platform/hifive/gpio/gpio-client.cpp
)

add_executable(vp-breadboard ${SOURCES} ${HEADERS} ${RESOURCES} ${UI})

target_link_libraries(vp-breadboard Qt5::Widgets pthread)

