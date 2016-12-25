project(logwrapper)

add_definitions(-DHAVE_PTHREADS -DFAKE_LOG_DEVICE -DHAVE_SYS_UIO_H)
add_definitions(-DANDROID_SMP)

set(LOGWRAP_SRCS logwrap.c)
set(LOGWRAPPER_srcs logwrapper.c)

add_library(logwrap
    SHARED
    ${LOGWRAP_SRCS}
    )

add_executable(logwrapper
    ${LOGWRAPPER_srcs}
    )

set_target_properties(logwrap PROPERTIES LINKER_LANGUAGE CXX)

target_link_libraries(logwrap
    pthread
    cutils
    utils
    log
    )

target_link_libraries(logwrapper
    pthread
    cutils
    logwrap
    )


