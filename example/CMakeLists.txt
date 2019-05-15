# ESP32 needs some special compilers. Set them here
SET(CMAKE_C_COMPILER "${ARDUINO_SDK_PATH}/hardware/tools/avr/bin/avr-gcc")
SET(CMAKE_CXX_COMPILER "${ARDUINO_SDK_PATH}/hardware/tools/avr/bin/avr-g++")
SET(CMAKE_AR "${ARDUINO_SDK_PATH}/hardware/tools/avr/bin/avr-gcc-ar")
SET(CMAKE_RANLIB "${ARDUINO_SDK_PATH}/hardware/tools/avr/bin/avr-gcc-ranlib")


# Set a variable for commands below
set(PROJECT_NAME example)

# Define your project and language
project(${PROJECT_NAME})

set(${PROJECT_NAME}_BOARD uno)

# Define the source code
set(${PROJECT_NAME}_SRCS example.cpp)

# Define the port for uploading code to the Arduino
set(${PROJECT_NAME}_PORT ttyACM0)


set(${PROJECT_NAME}_CPU atmega328p)

# Command to generate code arduino firmware (.hex file)
generate_arduino_firmware(${PROJECT_NAME})

