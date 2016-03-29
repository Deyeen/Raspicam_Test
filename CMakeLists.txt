# cmake needs this line
cmake_minimum_required(VERSION 2.8)
set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};/usr/local/lib/cmake")
set( CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}" ${CMAKE_MODULE_PATH} )

# Define project name
project(rpi_exposure)

# Find OpenCV, you may need to set OpenCV_DIR variable
# to the absolute path to the directory containing OpenCVConfig.cmake file
# via the command line or GUI
find_package(OpenCV REQUIRED)
find_package(aruco REQUIRED)
find_package(raspicam REQUIRED)


# If the package has been found, several variables will
# be set, you can find the full list with descriptions
# in the OpenCVConfig.cmake file.
# Print some message showing some of them
message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

if(CMAKE_VERSION VERSION_LESS "2.8.11")
  # Add OpenCV headers location to your include paths
  include_directories(${OpenCV_INCLUDE_DIRS})
endif()

# Declare the executable target built from your sources
add_executable(raspicam_cv_test raspicam_cv_test.cpp) 
add_executable(raspicam_test raspicam_test.cpp) 

# Link your application with OpenCV libraries
target_link_libraries(raspicam_cv_test ${OpenCV_LIBS})
target_link_libraries(raspicam_cv_test libaruco.so)
target_link_libraries (raspicam_cv_test ${raspicam_LIBS})
target_link_libraries (raspicam_cv_test ${raspicam_CV_LIBS})
target_link_libraries(raspicam_test ${OpenCV_LIBS})
target_link_libraries(raspicam_test libaruco.so)
target_link_libraries (raspicam_test ${raspicam_LIBS}) 


 
