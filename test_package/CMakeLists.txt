cmake_minimum_required(VERSION 3.8)
project(test_package LANGUAGES CXX)

find_package(fastcdr REQUIRED CONFIG)


add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE fastcdr)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)

if (MSVC)
	target_compile_definitions(${PROJECT_NAME} PRIVATE $<$<CONFIG:DEBUG>:_DEBUG>)
	set_target_properties(${PROJECT_NAME} PROPERTIES MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>DLL")
endif()