# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Initialise pico_sdk from installed location
# (note this can come from environment, CMake cache etc)

# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.2.0)
set(toolchainVersion 14_2_Rel1)
set(picotoolVersion 2.2.0-a4)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
set(PICO_BOARD pico2 CACHE STRING "Board type")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(usbhost01 C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1

add_executable(usbhost
 usbhost.c 
 hid_app.c 
 cdc_app.c
 msc_app.c
 tusb_config.h)

pico_set_program_name(usbhost "usbhost")
pico_set_program_version(usbhost "0.1")

# Modify the below lines to enable/disable output over UART/USB
# Note: stdio_usb cannot be used when running as USB Host
# pico_enable_stdio_uart(usbhost01 1)
# pico_enable_stdio_usb(usbhost01 0)

# Add the standard library to the build
target_link_libraries(usbhost
        pico_stdlib
        tinyusb_host
        tinyusb_board
        )

# Add the standard include files to the build
target_include_directories(usbhost PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}
)

pico_add_extra_outputs(usbhost)

