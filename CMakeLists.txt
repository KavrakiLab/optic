cmake_minimum_required(VERSION 3.1...3.22)
project(
    optic
    VERSION 0.1
    LANGUAGES C CXX
)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

option(FORCE_COLORED_OUTPUT "Always produce ANSI-colored output." ON)
if(FORCE_COLORED_OUTPUT)
    if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
        add_compile_options(-fdiagnostics-color=always)
    elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
        add_compile_options(-fcolor-diagnostics)
    endif()
endif()

set(CMAKE_MODULE_PATH
    "${CMAKE_MODULE_PATH}"
    "${CMAKE_ROOT_DIR}/cmake/modules"
    "${CMAKE_CURRENT_SOURCE_DIR}/cmake"
)

include(CompilerSettings)

set(val_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src/VALfiles)
add_subdirectory(src/VALfiles)
add_subdirectory(src/optic)
