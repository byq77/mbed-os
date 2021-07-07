# Copyright (c) 2021 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_library(mbed-headers-mbedtls INTERFACE)

target_include_directories(mbed-headers-mbedtls
    INTERFACE
        ${mbed-os_SOURCE_DIR}/connectivity/mbedtls
        ${mbed-os_SOURCE_DIR}/connectivity/mbedtls/include
)

add_library(mbed-stubs-mbedtls)

target_include_directories(mbed-stubs-mbedtls
    PUBLIC
        .
)

target_sources(mbed-stubs-mbedtls
    PRIVATE
        aes_stub.c
        cipher_stub.c
        cmac_stub.c
        mbedtls_stub.c
)

target_link_libraries(mbed-stubs-mbedtls
    PRIVATE
        mbed-stubs-rtos-headers
        mbed-headers
        mbed-headers-mbedtls
        mbed-stubs-headers
        mbed-stubs-rtos
        gtest
)
