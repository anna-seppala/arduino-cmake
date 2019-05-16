# ESP32 needs some special compilers. Set them here
SET(CMAKE_C_COMPILER "/home/aseppala/Downloads/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-gcc")
SET(CMAKE_C_COMPILER_WORKS 1)
SET(CMAKE_CXX_COMPILER "/home/aseppala/Downloads/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-g++")
SET(CMAKE_CXX_COMPILER_WORKS 1)
SET(CMAKE_AR  "/home/aseppala/Downloads/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-ar")
SET(CMAKE_RANLIB "/home/aseppala/Downloads/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-ranlib")

include_directories(
  "${ARDUINO_SDK_PATH}/hardware/arduino/sam/system/libsam")

get_property(inc_dirs DIRECTORY PROPERTY INCLUDE_DIRECTORIES)
message("included dirs = ${inc_dirs}")
# Set a variable for commands below
set(PROJECT_NAME example_sam)

# Define your project and language
project(${PROJECT_NAME})

set(${PROJECT_NAME}_BOARD arduino_due_x)#featheresp32)

# Define the source code
set(${PROJECT_NAME}_SRCS example_sam.cpp)

# Define the port for uploading code to the Arduino
set(${PROJECT_NAME}_PORT /dev/ttyUACM0)

# Select a specific upload speed for the board
set(${${PROJECT_NAME}_BOARD}.upload.speed 921600)

# Select a specific flash frequence for the board
set(${${PROJECT_NAME}_BOARD}.build.flash_freq 80m)

# Command to generate code arduino firmware (.hex file)
generate_arduino_firmware(${PROJECT_NAME}
  LIBS ${CORE_LIB})
