cmake_minimum_required(VERSION 3.28)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(
	CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fcoroutines -fexceptions -O0 -std=c++20"
)

project(
	Dijkstra
	VERSION 1.0
	LANGUAGES CXX
)

include(FetchContent)
FetchContent_Declare(
	googletest
	URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)

FetchContent_MakeAvailable(googletest)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "./bin")

enable_testing()

add_executable(
	tests
	src/dijkstra.cpp
	incl/dijkstra.hpp
	test/tests.cpp
)

add_executable(
	main
	src/dijkstra.cpp
	incl/dijkstra.hpp
	src/main.cpp
)

target_link_libraries(
	tests
	GTest::gtest_main
)
