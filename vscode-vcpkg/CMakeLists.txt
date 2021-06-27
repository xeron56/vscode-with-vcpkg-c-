cmake_minimum_required(VERSION 3.0.0)
project(rapidjson VERSION 0.1.0)
INCLUDE_DIRECTORIES(
	D:/vcpkg/installed/x86-windows/include
)
LINK_DIRECTORIES(
	D:/vcpkg/installed/x86-windows/lib
)

include(CTest)
enable_testing()

add_executable(vscode-vcpkg main.cpp)
TARGET_LINK_LIBRARIES(rapidjson

)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
