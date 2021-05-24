set(SOURCES main.cc secondary_config.cc secondary.cc update_events.cc update_lock.cc command_runner.cc compose_manager.cc device_data_proxy.cc)
set(HEADERS secondary_config.h secondary.h update_events.h update_lock.h command_runner.h compose_manager.h device_data_proxy.h)

add_executable(aktualizr-torizon ${SOURCES})
target_link_libraries(aktualizr-torizon aktualizr_lib torizon_virtual_secondary aktualizr-posix)
target_include_directories(aktualizr-torizon PUBLIC ${PROJECT_SOURCE_DIR}/aktualizr/third_party)

install(TARGETS aktualizr-torizon RUNTIME DESTINATION bin COMPONENT aktualizr-torizon)

add_aktualizr_test(NAME torizon_primary_secondary_registration
                   SOURCES primary_secondary_registration_test.cc secondary.cc secondary_config.cc
                   PROJECT_WORKING_DIRECTORY LIBRARIES PUBLIC aktualizr-posix virtual_secondary uptane_generator_lib)
target_include_directories(t_torizon_primary_secondary_registration PUBLIC ${PROJECT_SOURCE_DIR}/src/libaktualizr-posix)

# Check the --help option works.
add_test(NAME aktualizr-torizon-option-help
         COMMAND aktualizr-torizon --help)

# Report version.
add_test(NAME aktualizr-torizon-option-version
         COMMAND aktualizr-torizon --version)
set_tests_properties(aktualizr-torizon-option-version PROPERTIES PASS_REGULAR_EXPRESSION "Current aktualizr-torizon version is: ${AKTUALIZR_VERSION}")

aktualizr_source_file_checks(${SOURCES} ${HEADERS} ${TEST_SOURCES})

# vim: set tabstop=4 shiftwidth=4 expandtab:
