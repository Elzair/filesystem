cmake_minimum_required(VERSION 3.3)

project(boost_filesystem)

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
  add_library(boost_filesystem SHARED ${SOURCE_FILES} )
  target_compile_definitions(boost_filesystem PRIVATE BOOST_FILESYSTEM_DYN_LINK=1)
else()
  add_library(boost_filesystem STATIC ${SOURCE_FILES})
  target_compile_definitions(boost_filesystem PRIVATE BOOST_FILESYSTEM_STATIC_LINK=1)
endif(BOOST_FILESYSTEM_SHARED_LIB)

target_include_directories(boost_filesystem BEFORE PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

target_link_libraries(boost_filesystem
  boost::align boost::array boost::assert
  boost::bind
  boost::concept_check boost::config boost::conversion boost::core
  boost::detail
  boost::function boost::function_types boost::functional boost::fusion
  boost::integer boost::io boost::iterator
  boost::move boost::mpl
  boost::numeric::conversion
  boost::optional
  boost::predef boost::preprocessor
  boost::range
  boost::smart_ptr boost::static_assert
  boost::throw_exception boost::tuple boost::type_index boost::type_traits boost::typeof
  boost::utility
  boost::system
  boost::regex)

install(TARGETS boost_filesystem DESTINATION lib)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/boost DESTINATION include)

add_library(boost::filesystem ALIAS boost_filesystem)
