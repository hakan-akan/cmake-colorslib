add_library(white 
src/white.cpp)

add_library(ColorsLib::White ALIAS white)

target_include_directories(white 
   PUBLIC 
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)
