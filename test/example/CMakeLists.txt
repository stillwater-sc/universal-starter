file (GLOB SRCS "./*.cpp")

# Universal is a C++ header-only library, so we do not need to build anything
include_directories(${STARTER_UNIVERSAL_INCLUDE_DIR})

# create a ctest target for every individual cpp file in this directory
compile_all("true" "testprefix" "Tests/example" "${SRCS}")
