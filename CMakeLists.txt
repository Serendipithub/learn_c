cmake_minimum_required(VERSION 3.22)
project(pure_c_projects)

enable_language(C CXX OBJC OBJCXX)

set(CMAKE_C_STANDARD 17)
set(CMAKE_CXX_STANDARD 17)

add_executable(oc_project main.m)

set(CMAKE_C_COMPILER clang)
set(CMAKE_CXX_COMPILER clang++)
set(CMAKE_OBJC_FLAGS  "${CMAKE_OBJC_FLAGS_DEBUG} -lobjc -fobjc-runtime=gnustep-2.1 -fobjc-arc -fblocks")
set(CMAKE_OBJCXX_FLAGS "${CMAKE_OBJCXX_FLAGS_DEBUG} -lobjc -fobjc-runtime=gnustep-2.1 -fobjc-arc -fblocks")

target_include_directories(
        oc_project
        PUBLIC
        /usr/GNUstep/Local/Library/Headers
)

target_link_directories(
        oc_project
        PUBLIC
        /usr/GNUstep/Local/Library/Libraries
)

target_link_libraries(
        oc_project
        PUBLIC
        gnustep-base
        objc
)

target_compile_definitions(
        oc_project
        PUBLIC
        _NATIVE_OBJC_EXCEPTIONS
)

target_compile_options(
        oc_project
        PUBLIC
        -fconstant-string-class=NSConstantString
)