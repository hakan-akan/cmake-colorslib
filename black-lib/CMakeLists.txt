
add_library(black 
src/black.cpp)

add_library(ColorsLib::Black ALIAS black)


target_include_directories(black 
   PUBLIC 
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)
