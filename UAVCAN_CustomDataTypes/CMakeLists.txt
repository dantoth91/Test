cmake_minimum_required(VERSION 2.8)
project(UAVCAN_custom_messages)

set(UAVCAN_FOLDERS
	./apucontroller
	./bms
	./dlmesc
	./genesc
)

# Location of standart datatypes
set(UAVCAN_DSDL_DEFINITIONS "../../libuavcan/dsdl/uavcan")

#
# Invoke the DSDL compiler to generate headers for our custom data types.
# The default output directory is "dsdlc_generated"; it can be overridden if needed.
# If libuavcan is installed, we can use directly the compiler's executable "libuavcan_dsdlc".
# If the library isn't installed, use a relative path to the compiler in the libuavcan source tree.
#

execute_process(
	COMMAND ../../libuavcan/libuavcan/dsdl_compiler/libuavcan_dsdlc -I${UAVCAN_DSDL_DEFINITIONS} ${UAVCAN_FOLDERS}
	WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

