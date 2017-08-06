cmake_minimum_required(VERSION 2.8.12)

project(a)
set(a_VERSION 1.0)

add_library(a src/a.cc)
add_library(A::a ALIAS a)
target_include_directories(a PUBLIC
  $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
)

install(DIRECTORY include/ DESTINATION include)
install(TARGETS a EXPORT aTargets DESTINATION lib)
install(EXPORT aTargets FILE aTargets.cmake NAMESPACE A:: DESTINATION cmake)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  aConfigVersion.cmake
  VERSION ${a_VERSION}
  COMPATIBILITY SameMajorVersion
)

install(FILES
  aConfig.cmake ${PROJECT_BINARY_DIR}/aConfigVersion.cmake
  DESTINATION cmake
)
