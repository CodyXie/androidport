project(androidport)

cmake_minimum_required(VERSION 2.8)
set_property(GLOBAL PROPERTY TARGET_SUPPORTS_SHARED_LIBS TRUE)

message(STATUS "cmake version ${CMAKE_VERSION}")
if(NOT CMAKE_VERSION VERSION_LESS "2.8.12.20131121")
    cmake_policy(SET CMP0025 OLD) # report Apple's Clang as just Clang
    cmake_policy(SET CMP0042 OLD) # do not require MACOSX_RPATH
endif()

set( CMAKE_SHARED_LIBRARY_RUNTIME_C_FLAG "" )
set( CMAKE_SKIP_RPATH TRUE CACHE BOOL "If set, runtime paths are not added when using shared libraries." )

set(INSTALL_BIN_DIR "${CMAKE_INSTALL_PREFIX}/bin" CACHE PATH "Installing directory for executables")
set(INSTALL_LIB_DIR "${CMAKE_INSTALL_PREFIX}/lib" CACHE PATH "Installing directory for libraries")
set(INSTALL_INC_DIR "${CMAKE_INSTALL_PREFIX}/include" CACHE PATH "Installing directory for headers")

#set(CMAKE_C_FLAGS "-fPIC -DNDEBUG -O2 -mcpu=cortex-a7 -mfloat-abi=hard -mfpu=neon-vfpv4 -fstack-protector-strong -D_FORTIFY_SOURCE=2")
#set(CMAKE_CXX_FLAGS "-fPIC -DNDEBUG -O2 -mcpu=cortex-a7 -mfloat-abi=hard -mfpu=neon-vfpv4 -fstack-protector-strong -D_FORTIFY_SOURCE=2")
set(CMAKE_C_FLAGS "-fPIC -DNDEBUG -O2 -D_FORTIFY_SOURCE=2 -fvisibility=hidden")
set(CMAKE_CXX_FLAGS "-fPIC -DNDEBUG -O2 -D_FORTIFY_SOURCE=2 -fvisibility=hidden")
#set(CMAKE_C_FLAGS "-fPIC -DNDEBUG -O2 -D_FORTIFY_SOURCE=2")
#set(CMAKE_CXX_FLAGS "-fPIC -DNDEBUG -O2 -D_FORTIFY_SOURCE=2")

add_definitions(-DHAVE_PTHREADS -DFAKE_LOG_DEVICE -DHAVE_SYS_UIO_H)
add_definitions(-DANDROID_SMP)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_subdirectory(libcutils)
add_subdirectory(safe-iop)
add_subdirectory(libutils)
add_subdirectory(liblog)
add_subdirectory(libsysutils)
add_subdirectory(logwrapper)
add_subdirectory(googletest)
add_subdirectory(tests)
