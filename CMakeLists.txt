################################################################################
#    Copyright (C) 2017 GSI Helmholtzzentrum fuer Schwerionenforschung GmbH    #
#                                                                              #
#              This software is distributed under the terms of the             #
#         GNU Lesser General Public Licence version 3 (LGPL) version 3,        #
#                  copied verbatim in the file "LICENSE"                       #
################################################################################

cmake_minimum_required(VERSION 3.7)
cmake_policy(SET CMP0028 NEW)

project(ExamplePlugin LANGUAGES CXX)

if(FAIRROOTPATH)
    include(${FAIRROOTPATH}/include/cmake/FairMQ.cmake)
else()
    message(FATAL "Specify -DFAIRROOTPATH to FairRoot installation!")
endif()
find_package(Boost 1.61 COMPONENTS thread system timer program_options random filesystem chrono exception regex serialization log log_setup atomic date_time)

set(plugin FairMQPlugin_example)
set(VERSION_MAJOR 1)
set(VERSION_MINOR 0)
set(VERSION_PATCH 0)
set(VERSION ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH})
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/ExamplePlugin.h.in ${CMAKE_CURRENT_BINARY_DIR}/ExamplePlugin.h)
add_library(${plugin} SHARED ${CMAKE_CURRENT_SOURCE_DIR}/ExamplePlugin.cxx ${CMAKE_CURRENT_BINARY_DIR}/ExamplePlugin.h)
target_link_libraries(${plugin} FairRoot::FairMQ)
target_include_directories(${plugin} PUBLIC ${CMAKE_CURRENT_BINARY_DIR})
set_target_properties(${plugin} PROPERTIES CXX_VISIBILITY_PRESET hidden)
set_target_properties(${plugin} PROPERTIES VERSION ${VERSION})
