add_executable(Sandbox src/App.cpp)

target_link_libraries(Sandbox PRIVATE Luminare)

set_target_properties(Sandbox PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin/$<CONFIG>-${CMAKE_SYSTEM_NAME}-x64/Sandbox"
)

if(MSVC)
    target_compile_options(Sandbox PRIVATE /utf-8)
endif()