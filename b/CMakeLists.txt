cmake_minimum_required(VERSION 2.8.12)

project(b)
set(b_VERSION 1.0)

find_package(a 1.0)

add_executable(b src/b.cc)
target_link_libraries(b PUBLIC A::a)

install(TARGETS b DESTINATION bin)
