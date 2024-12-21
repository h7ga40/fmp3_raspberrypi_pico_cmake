# TOPPERS/FMP3 サンプルアプリ（sample1）
cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_C_COMPILER_WORKS 1)
set(CMAKE_CXX_COMPILER_WORKS 1)

set(FMP3_TARGET raspberrypi_pico_gcc)

include(fmp3/fmp3.cmake)

find_program(CMAKE_C_COMPILER NAMES ${CMAKE_C_COMPILER} ${PICO_TOOLCHAIN_PATH})
find_program(CMAKE_CXX_COMPILER NAMES ${CMAKE_CXX_COMPILER} ${PICO_TOOLCHAIN_PATH})
find_program(CMAKE_ASM_COMPILER NAMES ${CMAKE_ASM_COMPILER} ${PICO_TOOLCHAIN_PATH})
find_program(CMAKE_OBJCOPY NAMES ${CMAKE_OBJCOPY} ${PICO_TOOLCHAIN_PATH})
find_program(CMAKE_OBJDUMP NAMES ${CMAKE_OBJDUMP} ${PICO_TOOLCHAIN_PATH})
find_program(CMAKE_NM NAMES ${CMAKE_NM} ${PICO_TOOLCHAIN_PATH})

project(sample1 C)

set(FMP3_APP_CFG_FILE ${FMP3_ROOT_DIR}/sample/sample1.cfg)
set(FMP3_APP_INCLUDE_DIRS ${FMP3_ROOT_DIR}/sample)

add_executable(sample1
    ${FMP3_ROOT_DIR}/sample/sample1.c
)

add_subdirectory(fmp3)

target_link_libraries(sample1 fmp3)

target_include_directories(sample1 PRIVATE
    ${FMP3_ROOT_DIR}/sample
    ${CMAKE_CURRENT_LIST_DIR}
)

include(${FMP3_ROOT_DIR}/library/library.cmake)
include(${FMP3_ROOT_DIR}/syssvc/syssvc.cmake)

target_link_options(sample1 PRIVATE "LINKER:-Map=sample1.map")

fmp3_cfg_check(sample1)

fmp3_add_extra_outputs(sample1)
