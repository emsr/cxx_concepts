cmake_minimum_required (VERSION 3.15.0)

project(
  cxx_concepts
  VERSION 0.1.0
  LANGUAGES CXX
)

include_directories(include)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_CXX_COMPILER /home/ed/bin/bin/g++)
set(CMAKE_CXX_FLAGS "-fconcepts -Wall -Wextra -Wno-psabi -Wno-deprecated-declarations -Wold-style-cast")

if (NOT MSVC)
  if (NOT CMAKE_CROSSCOMPILING)
    set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)
  endif ()
endif ()

enable_testing()

add_library(cxx_test_concepts INTERFACE)
target_include_directories(cxx_test_concepts INTERFACE include)

add_executable(test_concepts test_concepts.cpp)
target_link_libraries(test_concepts cxx_concepts)
add_test(NAME run_test_math_const COMMAND bash -c "./bin/test_concepts > output/test_concepts.txt")
