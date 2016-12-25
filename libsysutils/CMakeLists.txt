project(sysutils)


aux_source_directory(src SYSUTILS_SRCS)

set(SYSUTILS_SRCS ${SYSUTILS_SRCS} EventLogTags.logtags)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../include)

add_library(sysutils
    STATIC
    ${LIBCUTILS_SRCS}
    )

set_target_properties(sysutils PROPERTIES LINKER_LANGUAGE CXX)
target_link_libraries(sysutils cutils log)
