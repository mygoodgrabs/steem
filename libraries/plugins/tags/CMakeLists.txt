file(GLOB HEADERS "include/steemit/tags/*.hpp")

add_library( steemit_tags
             tags_plugin.cpp )

target_link_libraries( steemit_tags steemit_chain steemit_protocol steemit_app )
target_include_directories( steemit_tags
                            PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include" )

if( CLANG_TIDY_EXE )
   set_target_properties(
      steemit_tags PROPERTIES
      CXX_CLANG_TIDY "${DO_CLANG_TIDY}"
   )
endif( CLANG_TIDY_EXE )

install( TARGETS
   steemit_tags

   RUNTIME DESTINATION bin
   LIBRARY DESTINATION lib
   ARCHIVE DESTINATION lib
)
