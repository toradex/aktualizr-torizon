project(aktualizr-torizon)
cmake_minimum_required(VERSION 3.8)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/src/libaktualizr)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/third_party/jsoncpp/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/aktualizr/third_party/googletest/googletest/include)

add_definitions(-DBOOST_LOG_DYN_LINK)

set(AKTUALIZR_VERSION "2020.8")

# TODO: Fully review this file based on the one in aktualizr/
# TODO: Enable testing (call enable_testing())
add_subdirectory("aktualizr")
add_subdirectory("src")

string(ASCII 27 Esc)
message(NOTICE "")
message(NOTICE "${Esc}[1;33mIMPORTANT:${Esc}[0m")
message(NOTICE "")
message(NOTICE "    ${Esc}[1;33mThis project is deprecated and will no longer be maintained.${Esc}[0m")
message(NOTICE "    ${Esc}[1;33mPlease clone https://github.com/toradex/aktualizr instead.${Esc}[0m")
message(NOTICE "")
