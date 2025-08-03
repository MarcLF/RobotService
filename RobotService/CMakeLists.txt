cmake_minimum_required (VERSION 3.27)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("RobotService" LANGUAGES CXX)

add_executable (RobotService "RobotService.cpp" "RobotService.h")

set_property(TARGET RobotService PROPERTY CXX_STANDARD 23)

add_subdirectory(src)
enable_testing()
add_subdirectory(tests)