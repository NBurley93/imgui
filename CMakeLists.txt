cmake_minimum_required(VERSION 3.16)
project(imgui)

set(CMAKE_CXX_STANDARD 17)

add_library(imgui STATIC
    imgui.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
    imgui_demo.cpp
)
set(IMGUI_INCLUDE_DIRS ${PROJECT_SOURCE_DIR})
target_include_directories(imgui PUBLIC ${IMGUI_INCLUDE_DIRS})

if(MSVC)
    target_compile_options(imgui PRIVATE
        /MD$<$<CONFIG:Debug>:d>
        $<$<CONFIG:Debug>:/Od>$<$<CONFIG:Release>:/O2>
    )
endif()