cmake_minimum_required(VERSION 3.22)

project(Mo)

#Qt Kit Pass
set(CMAKE_PREFIX_PATH "C:/Qt/6.3.1/mingw_64")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

#Qt Components 
find_package(Qt6 REQUIRED COMPONENTS
    Widgets
    Core
    Gui
)

qt_standard_project_setup()

# The Project Files
set(SRC_FILES
    main.cpp
    ./include/widget.hpp
    ./src/widget.cpp
    widget.ui
)

# Excuting The App
add_executable(out ./${SRC_FILES})

target_include_directories(out PUBLIC ./include ./src)

target_link_libraries(out PRIVATE 
    Qt6::Widgets
    Qt6::Core
    Qt6::Gui
)

set_target_properties(out PROPERTIES
    WIN32_EXECUTABLE ON
    MACOSX_BUNDLE ON
)
