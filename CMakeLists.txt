cmake_minimum_required(VERSION 3.13)
# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)
project(pico-hid-from-uart)
 
pico_sdk_init()

add_executable(pico-hid-from-uart)

target_include_directories(pico-hid-from-uart PRIVATE ${CMAKE_CURRENT_LIST_DIR})

target_sources(pico-hid-from-uart PRIVATE
        main.c
        usb_descriptors.c
        )
        
target_link_libraries(pico-hid-from-uart PRIVATE pico_stdlib tinyusb_device tinyusb_board)
pico_add_extra_outputs(pico-hid-from-uart)