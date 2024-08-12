# This component demonstrates how to add an existing third-party library as a component
# to ESP-IDF build system.
#
# Since we are wrapping the library inside a component,
# the component has to be registered first:
idf_component_register(PRIV_REQUIRES lwip mbedtls)

set(WITH_GSSAPI OFF)
set(WITH_ZLIB OFF)
set(WITH_GCRYPT OFF)
set(WITH_MBEDTLS ON)
set(WITH_PCAP OFF)
set(BUILD_SHARED_LIBS OFF)
set(WITH_EXAMPLES OFF)
set(WITH_INSECURE_NONE ON)
set(WITH_EXEC OFF)

add_subdirectory(libssh)

# Link the imported library to the current component.
target_link_libraries(${COMPONENT_LIB} INTERFACE libssh)
