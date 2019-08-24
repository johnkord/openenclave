# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

include(oeedl_file)

oeedl_file(../oecert.edl host gen)

add_executable(oecert host.cpp ${gen})

target_include_directories(oecert PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(oecert oehost)

