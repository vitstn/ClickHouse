if(USE_PROTOBUF)
    protobuf_generate_cpp(ProtobufDelimitedMessagesSerializer_Srcs ProtobufDelimitedMessagesSerializer_Hdrs ${CMAKE_CURRENT_SOURCE_DIR}/../../tests/queries/0_stateless/00825_protobuf_format.proto)
    protobuf_generate_cpp(ProtobufDelimitedMessagesSerializer_Srcs2 ProtobufDelimitedMessagesSerializer_Hdrs2 ${CMAKE_CURRENT_SOURCE_DIR}/../../tests/queries/0_stateless/00825_protobuf_format_syntax2.proto)
    add_executable (ProtobufDelimitedMessagesSerializer ProtobufDelimitedMessagesSerializer.cpp ${ProtobufDelimitedMessagesSerializer_Srcs} ${ProtobufDelimitedMessagesSerializer_Hdrs} ${ProtobufDelimitedMessagesSerializer_Srcs2} ${ProtobufDelimitedMessagesSerializer_Hdrs2})
    target_include_directories (ProtobufDelimitedMessagesSerializer SYSTEM BEFORE PRIVATE ${Protobuf_INCLUDE_DIR} ${CMAKE_CURRENT_BINARY_DIR})
    target_link_libraries (ProtobufDelimitedMessagesSerializer PRIVATE ${Protobuf_LIBRARY} ${Boost_PROGRAM_OPTIONS_LIBRARY})
    get_filename_component(ProtobufDelimitedMessagesSerializer_OutputDir "${CMAKE_CURRENT_LIST_DIR}/../../tests/queries/0_stateless" REALPATH)
    target_compile_definitions(ProtobufDelimitedMessagesSerializer PRIVATE OUTPUT_DIR="${ProtobufDelimitedMessagesSerializer_OutputDir}")
endif()
