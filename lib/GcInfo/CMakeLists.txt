get_filename_component(LLILC_INCLUDES ${CMAKE_CURRENT_SOURCE_DIR}/../../include ABSOLUTE)

include_directories(${LLILC_INCLUDES}/clr
                    ${LLILC_INCLUDES}/GcInfo
                    ${LLILC_INCLUDES}/Jit
                    ${LLILC_INCLUDES}/Pal)

if( WIN32 )
  set(CMAKE_CXX_FLAGS "-EHsc")
endif()
					
add_definitions(-DSTANDALONE_BUILD)
					
if(CLR_CMAKE_PLATFORM_UNIX)
    add_compile_options(-fPIC)
endif(CLR_CMAKE_PLATFORM_UNIX)

add_llilcjit_library(GcInfo
    STATIC
	${CORECLR_GCINFO}/gcinfoencoder.cpp
	GcInfoUtil.cpp
)
