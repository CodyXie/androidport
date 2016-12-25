
include_directories(${CMAKE_INSTALL_PREFIX}/include)

add_executable(Looper_test Looper_test.cpp)

target_link_libraries(Looper_test log utils cutils gtest gtest_main) 
