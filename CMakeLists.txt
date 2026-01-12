set(SPINE_SRCS)
file(GLOB SPINE_SRCS
	include/spine/*.h
	src/spine/*.cpp
)

add_library(spine
    ${SPINE_SRCS}
)

target_include_directories(spine PUBLIC include)

if(MSVC)
	add_compile_options($<$<PLATFORM_ID:Windows>:/MP${Biogears_BUILD_PARALLEL_LEVEL}>)
	target_compile_options(spine PRIVATE
		$<$<PLATFORM_ID:Windows>:/MP${Biogears_BUILD_PARALLEL_LEVEL}>
	)
endif()
