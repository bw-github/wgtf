CMAKE_MINIMUM_REQUIRED( VERSION 3.1.1 )
PROJECT( plg_reflection_test )

INCLUDE( WGToolsCoreProject )

REMOVE_DEFINITIONS( /WX )
ADD_DEFINITIONS( -D_CRT_SECURE_NO_WARNINGS )

# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

SET( METADATA_SRCS
	metadata/test_class.mpp
)
SOURCE_GROUP( "MetaData" FILES ${METADATA_SRCS} )

SET( ALL_SRCS
	plg_reflection_test.cpp
	test_class.cpp
	test_class.hpp
)
SOURCE_GROUP( "" FILES ${ALL_SRCS} )


BW_BLOB_SOURCES( BLOB_SRCS
	${ALL_SRCS}
	${METADATA_SRCS}
)
BW_ADD_TOOL_PLUGIN( plg_reflection_test SHARED
	${BLOB_SRCS}
)


BW_TARGET_LINK_LIBRARIES( plg_reflection_test PRIVATE
	core_generic_plugin
	core_reflection
)

BW_PROJECT_CATEGORY( plg_reflection_test "Plugins" )
