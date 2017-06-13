cmake_minimum_required(VERSION 3.7)
project(gtkmmtut)

set(CMAKE_CXX_STANDARD 11)

file(GLOB SRC
        "*.h"
        "*.cpp"
        "*.cc"
        "*.c"
        )

FIND_PACKAGE(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GTKMM REQUIRED gtkmm-3.0)

INCLUDE_DIRECTORIES(${GTKMM_INCLUDE_DIRS})
LINK_DIRECTORIES(${GTKMM_LIBRARY_DIRS})

# Add other flags to the compiler
ADD_DEFINITIONS(${GTKMM_CFLAGS_OTHER})

# Add an executable compiled from hello.c
#ADD_EXECUTABLE(hello main.c)
add_executable(gtkmmtut ${SRC})

# Link the target to the GTK+ libraries
TARGET_LINK_LIBRARIES(gtkmmtut ${GTKMM_LIBRARIES} -lepoxy)