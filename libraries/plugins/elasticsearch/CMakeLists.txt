file(GLOB HEADERS "include/graphene/elasticsearch/*.hpp")

add_library( graphene_elasticsearch
        elasticsearch_plugin.cpp
           )

if(MSVC)
  set_source_files_properties(elasticsearch_plugin.cpp PROPERTIES COMPILE_FLAGS "/bigobj" )
endif(MSVC)
target_link_libraries( graphene_elasticsearch graphene_app graphene_chain )
target_include_directories( graphene_elasticsearch
                            PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include" )


install( TARGETS
   graphene_elasticsearch

   RUNTIME DESTINATION bin
   LIBRARY DESTINATION lib
   ARCHIVE DESTINATION lib
)
INSTALL( FILES ${HEADERS} DESTINATION "include/graphene/elasticsearch" )

