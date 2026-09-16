file(GLOB_RECURSE ENGINE_SOURCES
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.h"
)
add_library(Luminare STATIC ${ENGINE_SOURCES})

set_target_properties(Luminare PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin/$<CONFIG>-${CMAKE_SYSTEM_NAME}-x64/Luminare"
)

target_include_directories(Luminare
	PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_precompile_headers(Luminare PRIVATE src/lmn_pch.h)

if(MSVC)
	target_compile_options(Luminare PRIVATE /utf-8)
endif()

target_compile_definitions(Luminare
	PUBLIC
		$<$<CONFIG:Debug>:		LMN_DEBUG>
		$<$<CONFIG:Release>:	LMN_RELEASE>
		$<$<CONFIG:Dist>:		LMN_DIST>
)