# Copyright (c) Microsoft Corporation.
# Licensed under the MIT License.

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${QUIC_CXX_FLAGS}")

add_executable(spinquic spinquic.cpp)

target_link_libraries(spinquic msquic platform PLATFORM_CLOG_LIB CORE_CLOG_LIB)

set_property(TARGET spinquic PROPERTY FOLDER "tools")

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
    target_link_libraries(spinquic
        ws2_32 schannel ntdll bcrypt ncrypt crypt32 iphlpapi advapi32)
endif()
