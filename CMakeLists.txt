cmake_minimum_required(VERSION 3.23)
project(Example VERSION 0.1.0)

add_library(example "src/nil.cpp")

find_package(LLVM 16 REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

message(STATUS "Using LLVM include: ${LLVM_INCLUDE_DIRS}")
message(STATUS "Using LLVM library: ${LLVM_LIBRARY_DIRS}")
message(STATUS "Using LLVM tool dir: ${LLVM_TOOLS_BINARY_DIR}")

execute_process(COMMAND ${LLVM_TOOLS_BINARY_DIR}/llvm-config --libs all
  OUTPUT_VARIABLE LLVM_LIBS OUTPUT_STRIP_TRAILING_WHITESPACE)
message(STATUS "LLVM libs: ${LLVM_LIBS}")

