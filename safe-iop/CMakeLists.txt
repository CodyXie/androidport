project(safe-iop)


set(SAFE_IOP_SRCS src/safe_iop.c)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library(safe-iop
    STATIC
    ${SAFE_IOP_SRCS}
    )
