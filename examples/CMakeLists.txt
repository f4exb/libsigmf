if (WIN32)
    set(DEMANGLE_LIBS Dbghelp)
else()
    # On Linux, libstdc++ is used which we don't need to explictly link
    set(DEMANGLE_LIBS "")
endif()

# This is the bare minimum to use libsigmf along with some example usage patterns
add_executable(example_record_with_variadic_dataclass
        example_record_with_variadic_dataclass.cpp)
target_link_libraries(example_record_with_variadic_dataclass libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_record_with_variadic_dataclass PRIVATE ${CMAKE_BINARY_DIR}/include)

add_executable(example_record_with_multiple_namespaces example_record_with_multiple_namespaces.cpp)
target_link_libraries(example_record_with_multiple_namespaces libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_record_with_multiple_namespaces PRIVATE ${CMAKE_BINARY_DIR}/include)

add_executable(example_record_multirecordings example_record_multirecordings.cpp)
target_link_libraries(example_record_multirecordings libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_record_multirecordings PRIVATE ${CMAKE_BINARY_DIR}/include)

add_executable(example_record_sdrangel example_record_sdrangel.cpp)
target_link_libraries(example_record_sdrangel libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_record_sdrangel PRIVATE ${CMAKE_BINARY_DIR}/include)

add_executable(example_sigmf_json_roundtrip example_sigmf_json_roundtrip.cpp)
target_link_libraries(example_sigmf_json_roundtrip libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_sigmf_json_roundtrip PRIVATE ${CMAKE_BINARY_DIR}/include)

add_executable(example_reading_sigmf_file example_reading_sigmf_file.cpp)
target_link_libraries(example_reading_sigmf_file libsigmf ${DEMANGLE_LIBS})
target_include_directories(example_reading_sigmf_file PRIVATE ${CMAKE_BINARY_DIR}/include)

add_test(NAME simple_variadic_sigmf_to_json
        COMMAND example_record_with_variadic_dataclass)
add_test(NAME simple_variadic_2ns_sigmf_to_json
        COMMAND example_record_with_multiple_namespaces)


# This demonstrates some of the features of flatbuffers we use internally to libsigmf. This is primaryily useful to
# experiment / understand the libsigmf internals on concrete flatbuffers types outside of the heavily templated
# VariadicDataClass


# add_executable(flatbuffer_patterns flatbuffer_patterns.cpp)
# target_link_libraries(flatbuffer_patterns libsigmf ${DEMANGLE_LIBS})
# target_include_directories(flatbuffer_patterns PRIVATE ${CMAKE_BINARY_DIR})
