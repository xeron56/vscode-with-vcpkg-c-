# vscode-with-vcpkg-c-

1. First need to download visual studio 2017 or visual studio 2019 with default c/c++ development feature added
2. install cmake
3. install vcpkg

i. First clone the letest vcpkg manager from github

```
> git clone https://github.com/Microsoft/vcpkg.git
> cd vcpkg
```
ii. Open the powershell in vcpkg directory and run
```
PS> .\bootstrap-vcpkg.bat
 ```
 iii. Now do intergate 
 ```
 PS> .\vcpkg integrate install
 ```
iv. Now add the vcpkge.exe path to the env variable so that u can use call vcpkg from anywhere

v. Now install package u want, like (ex: rapidjson)

```
vcpkg install rapidjson:x64-windows
```
4. Install vscode
5. install c++ extension and cmake extension pack vscode
6. Add this to setting.json in vscode

```
 "cmake.configureSettings": {
        "CMAKE_TOOLCHAIN_FILE": "D:/1907509MSC/vcpkg/scripts/buildsystems/vcpkg.cmake"
      },
```

7. add CMAKElists.txt file as

```
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
```
Here we include lib and include directory
```
INCLUDE_DIRECTORIES(
	D:/vcpkg/installed/x86-windows/include
)
LINK_DIRECTORIES(
	D:/vcpkg/installed/x86-windows/lib
)
```
Here we add the wanted library to add

```
TARGET_LINK_LIBRARIES(rapidjson

)
```
Now build and run project
