cmake_minimum_required(VERSION 3.5)
project(libjsonutils VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)  
set(CMAKE_CXX_STANDARD_REQUIRED ON) 
set(CMAKE_CXX_EXTENSIONS OFF)  

add_subdirectory(black-lib)
add_subdirectory(white-lib)

##############################################
# Installation instructions

include(GNUInstallDirs)
set(INSTALL_CONFIGDIR ${CMAKE_INSTALL_LIBDIR}/cmake/ColorsLib)

install(TARGETS white black
    EXPORT colorslib-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(EXPORT colorslib-targets
    FILE ColorsLibTargets.cmake
  NAMESPACE ColorsLib::
  DESTINATION ${INSTALL_CONFIGDIR}
)
 

##############################################
# Exporting from the build tree

export(EXPORT colorslib-targets 
       FILE ${CMAKE_CURRENT_BINARY_DIR}/ColorsLibTargets.cmake 
       NAMESPACE ColorsLib::)

#Register package in user's package registry
export(PACKAGE ColorsLib)