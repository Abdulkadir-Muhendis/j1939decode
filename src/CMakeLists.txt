set(SOURCES
        j1939decode.c j1939decode.h
        cJSON.c cJSON.h
        )

add_library(${STATIC_LIB} STATIC ${SOURCES})
add_library(${SHARED_LIB} SHARED ${SOURCES})

set_target_properties(${STATIC_LIB} PROPERTIES OUTPUT_NAME ${PROJECT_NAME} CLEAN_DIRECT_OUTPUT 1)
set_target_properties(${SHARED_LIB} PROPERTIES OUTPUT_NAME ${PROJECT_NAME} CLEAN_DIRECT_OUTPUT 1)

# Install static lib
install(TARGETS ${STATIC_LIB}
        ARCHIVE DESTINATION lib)

# Install shared lib
install(TARGETS ${SHARED_LIB}
        LIBRARY DESTINATION lib)

# Install headers
set(HEADERS j1939decode.h)
set(HEADER_PATH ${CMAKE_PROJECT_NAME})
install(FILES ${HEADERS} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/${HEADER_PATH})