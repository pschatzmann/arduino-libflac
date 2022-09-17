cmake_minimum_required(VERSION 3.16)

# set the project name
project(arduino_libflac)

include(FetchContent)

# lots of warnings and all warnings as errors
## add_compile_options(-Wall -Wextra )
set(CMAKE_CXX_STANDARD 17)

FetchContent_Declare(arduino_libopus GIT_REPOSITORY "https://github.com/pschatzmann/arduino-libopus.git" GIT_TAG main )
FetchContent_GetProperties(arduino_libopus)
if(NOT arduino_libopus_POPULATED)
    FetchContent_Populate(arduino_libopus)
    add_subdirectory(${arduino_libopus_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR}/arduino_libopus)
endif()



file(GLOB_RECURSE SRC_LIST_C CONFIGURE_DEPENDS  "${PROJECT_SOURCE_DIR}/src/*.c" )

# define libraries
add_library (arduino_libflac ${SRC_LIST_C})

#target_compile_options(arduino_libflac PRIVATE -Wdouble-promotion)
target_compile_definitions(arduino_libflac PUBLIC -DPACKAGE_VERSION="1.3.4" -DHAVE_LROUND -DFLAC__HAS_OGG=true )

target_link_libraries(arduino_libflac arduino_libopus)

# define location for header files
target_include_directories(arduino_libflac PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src )
