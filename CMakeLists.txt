if(APPLE)
  cmake_minimum_required(VERSION 2.8.11 FATAL_ERROR)
else()
  cmake_minimum_required(VERSION 2.8.7 FATAL_ERROR)
endif()

if(NOT BOOST_CONFIG_INCLUDE_DIRS)
  message(FATAL_ERROR "Cannot find boost.config!")
endif(NOT BOOST_CONFIG_INCLUDE_DIRS)

if(NOT BOOST_ASSERT_INCLUDE_DIRS)
  message(FATAL_ERROR "Cannot find boost.assert!")
endif(NOT BOOST_ASSERT_INCLUDE_DIRS)

if(NOT BOOST_CORE_INCLUDE_DIRS)
  message(FATAL_ERROR "Cannot find boost.core!")
endif(NOT BOOST_CORE_INCLUDE_DIRS)

if(NOT BOOST_SYSTEM_INCLUDE_DIRS OR NOT BOOST_SYSTEM_LIBRARIES)
  message(FATAL_ERROR "Cannot find boost.system!")
endif(NOT BOOST_SYSTEM_INCLUDE_DIRS OR NOT BOOST_SYSTEM_LIBRARIES)

option(BOOST_SHARED_LIB "Enable dynamic linking" ON)

set(BOOST_SYSTEM_INCLUDE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/include" CACHE STRING "Location of boost.system headers")

set(BOOST_INCLUDE_DIRS "${BOOST_INCLUDE_DIRS}" "${BOOST_FILESYSTEM_INCLUDE_DIRS}" CACHE STRING "All Boost headers" FORCE)

include_directories(${BOOST_INCLUDE_DIRS})

project(boost_filesystem)

set(SOURCE_FILES src/codecvt_error_category.cpp
  src/operations.cpp
  src/path.cpp
  src/path_traits.cpp
  src/portability.cpp
  src/unique_path.cpp
  src/utf8_codecvt_facet.cpp
  src/windows_file_codecvt.cpp
  )

if(BOOST_SHARED_LIB)
  add_definitions(-DBOOST_FILESYSTEM_DYN_LINK=1)
  add_library(boost_filesystem SHARED ${SOURCE_FILES})
else()
  add_definitions(-DBOOST_FILESYSTEM_STATIC_LINK=1)
  add_library(boost_filesystem STATIC ${SOURCE_FILES})
endif(BOOST_SHARED_LIB)
set_property(TARGET boost_filesystem PROPERTY CXX_STANDARD 11)
set_property(TARGET boost_filesystem PROPERTY CXX_STANDARD_REQUIRED ON)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  set(BOOST_FILESYSTEM_LIBRARIES "-L ${CMAKE_CURRENT_BINARY_DIR} -lboost_filesystem" CACHE STRING "Location of boost.filesystem library")

  set(BOOST_LIBRARIES "${BOOST_LIBRARIES}" "${BOOST_FILESYSTEM_LIBRARIES}" CACHE STRING "All Boost libraries" FORCE)
else()
  message(WARNING "You will have to manually link boost_filesystem. BOOST_FILESYSTEM_LIBRARIES is currently supported only on GCC and Clang.")
endif()

