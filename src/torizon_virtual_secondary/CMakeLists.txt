set(SOURCES managedsecondary.cc virtualsecondary.cc
    dockercomposesecondary.cc dockertarballloader.cc dockerofflineloader.cc)

set(HEADERS managedsecondary.h virtualsecondary.h
    dockercomposesecondary.h dockertarballloader.h dockerofflineloader.h)

set(TARGET torizon_virtual_secondary)

# TODO: Remove this block after fully reviewing top-level CMakeLists.txt file (based on the one in aktualizr/)
if (CMAKE_CXX_COMPILER_ID MATCHES "(GNU|Clang)")
    add_definitions(-Wall -Wextra -Wformat-security -Wfloat-equal -Wcast-qual -Wswitch-default -Wconversion)
endif()

add_library(${TARGET} STATIC
  ${SOURCES}
)

target_include_directories(${TARGET} PUBLIC ${PROJECT_SOURCE_DIR}/src/torizon_virtual_secondary ${PROJECT_SOURCE_DIR}/src/aktualizr_torizon_primary)

add_aktualizr_test(NAME torizon_virtual_secondary SOURCES virtual_secondary_test.cc PROJECT_WORKING_DIRECTORY LIBRARIES uptane_generator_lib)
target_link_libraries(t_torizon_virtual_secondary torizon_virtual_secondary)

# TODO: Add tests after reviewing top-level CMakeLists.txt file.
# add_aktualizr_test(NAME dockertarballloader SOURCES dockertarballloader_test.cc PROJECT_WORKING_DIRECTORY LIBRARIES torizon_virtual_secondary aktualizr_lib gtest)

aktualizr_source_file_checks(${HEADERS} ${SOURCES} ${TEST_SOURCES})
