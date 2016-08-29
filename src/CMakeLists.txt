set(UDT_NAME udt)
set(UDT_SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR})

set_property(GLOBAL PROPERTY UDT_INCLUDE_DIR ${UDT_SRC_DIR})
set_property(GLOBAL PROPERTY UDT_NAME ${UDT_NAME})

aux_source_directory(${UDT_SRC_DIR} UDT_SRC)
include_directories(${UDT_SRC_DIR})

set(UDT_INCLUDE_FILES
        api.h
        buffer.h
        cache.h
        ccc.h
        channel.h
        common.h
        core.h
        epoll.h
        list.h
        md5.h
        packet.h
        queue.h
        udt.h
        window.h
        )

add_library(${UDT_NAME}s STATIC ${UDT_SRC})
add_library(${UDT_NAME} SHARED ${UDT_SRC})

set_target_properties(${UDT_NAME}s PROPERTIES OUTPUT_NAME ${UDT_NAME})

install(TARGETS ${UDT_NAME}s  LIBRARY DESTINATION ${PROJECT_BINARY_DIR}/lib ARCHIVE DESTINATION ${PROJECT_BINARY_DIR}/lib)
install(TARGETS ${UDT_NAME}  LIBRARY DESTINATION ${PROJECT_BINARY_DIR}/lib ARCHIVE DESTINATION ${PROJECT_BINARY_DIR}/lib)

install(FILES  ${UDT_INCLUDE_FILES}  DESTINATION ${PROJECT_BINARY_DIR}/include/udt)
