project(aktualizr-torizon)
cmake_minimum_required(VERSION 3.8)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/src/libaktualizr)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/third_party/jsoncpp/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/third_party/googletest/googletest/include)

add_definitions(-DBOOST_LOG_DYN_LINK)

set(AKTUALIZR_VERSION "2020.8")

add_subdirectory("aktualizr")
add_subdirectory("src")
