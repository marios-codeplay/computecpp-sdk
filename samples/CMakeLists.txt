if(MSVC)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /W4")
  set_property(GLOBAL PROPERTY USE_FOLDERS ON)
else()
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")
endif()

# Loop over subdirectories for samples, looking for CMakeLists
file(GLOB _ALL_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*)
foreach(_FILE ${_ALL_FILES})
  if (IS_DIRECTORY ${_FILE})
    if (EXISTS ${_FILE}/CMakeLists.txt)
     add_subdirectory(${_FILE})
    endif()
  endif()
endforeach()
