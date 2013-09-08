set (SRCS
	SampleGuiPlugin2.cpp
	SampleGuiPlugin2Exports.cpp)
set (HEADERS
	SampleGuiPlugin2.h)
	
set(LIBRARY_NAME SampleGuiPlugin2)

if(WIN32)
	set(SRCS ${SRCS} ${LIBRARY_NAME}.def)
	set(PREPROCESSOR_DEFINITIONS ${PREPROCESSOR_DEFINITIONS};/D_USRDLL;/D__STDC_CONSTANT_MACROS)
	set(LINK_DIRECTORIES 
		${PROJECT_ROOT_DIR}/wxGuiPluginBase/${OS_BASE_NAME}${LIB_SUFFIX}/$(ConfigurationName))
	set(DEMO_LIBS wxGuiPluginBase.lib)
endif(WIN32)

set(SRCS ${SRCS} ${HEADERS} 
	${PROJECT_ROOT_DIR}/include/stdwx.h 
	${PROJECT_ROOT_DIR}/include/stdwx.cpp)

add_definitions(${PREPROCESSOR_DEFINITIONS})

include_directories(${INCLUDE_DIRECTORIES} ${BASE_INCLUDE_DIRECTORIES} 
	${PROJECT_ROOT_DIR}/wxGuiPluginBase)
	
link_directories(${LINK_DIRECTORIES})

add_library(${LIBRARY_NAME} SHARED ${SRCS})

set(DLL_DIR bin)
set(TARGET_LOCATION ${PROJECT_SOURCE_DIR}/${DLL_DIR}/${CMAKE_CFG_INTDIR}/plugins/gui)
set_target_properties(${LIBRARY_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${TARGET_LOCATION})

target_link_libraries(${LIBRARY_NAME} ${DEMO_LIBS} ${wxWidgets_LIBRARIES})

add_dependencies(${LIBRARY_NAME} wxGuiPluginBase)

set_precompiled_header(${LIBRARY_NAME} ${PROJECT_ROOT_DIR}/include/stdwx.h ${PROJECT_ROOT_DIR}/include/stdwx.cpp)