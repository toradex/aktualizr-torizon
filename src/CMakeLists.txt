if(BUILD_WITH_CODE_COVERAGE)
    add_definitions(${COVERAGE_COMPILER_FLAGS})
endif()

add_subdirectory("aktualizr_torizon_primary")
add_subdirectory("torizon_virtual_secondary")
