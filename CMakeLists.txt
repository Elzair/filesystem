if(APPLE)
  cmake_minimum_required(VERSION 2.8.11 FATAL_ERROR)
else()
  cmake_minimum_required(VERSION 2.8.7 FATAL_ERROR)
endif()

option(BOOST_FILESYSTEM_SHARED_LIB "Enable dynamic linking" ON)

set(SOURCE_FILES src/codecvt_error_category.cpp
  src/operations.cpp
  src/path.cpp
  src/path_traits.cpp
  src/portability.cpp
  src/unique_path.cpp
  src/utf8_codecvt_facet.cpp
  src/windows_file_codecvt.cpp)

if(BOOST_FILESYSTEM_SHARED_LIB)
  add_library(boost_filesystem SHARED GLOBAL ${SOURCE_FILES})
  target_compile_definitions(boost_filesystem PRIVATE BOOST_FILESYSTEM_DYN_LINK=1)
else()
  add_library(boost_filesystem STATIC GLOBAL ${SOURCE_FILES})
  target_compile_definitions(boost_filesystem PRIVATE BOOST_FILESYSTEM_STATIC_LINK=1)
endif(BOOST_FILESYSTEM_SHARED_LIB)

target_include_directories(boost_filesystem BEFORE PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

