cmake_minimum_required(VERSION 3.22)
project(a)
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})
find_package(Python REQUIRED COMPONENTS Interpreter)

# On Windows, Python_SITELIB returns \. Let's convert it to /.
cmake_path(CONVERT "${Python_SITELIB}" TO_CMAKE_PATH_LIST Python_SITELIB NORMALIZE)

if(TARGET Python::Interpreter)
    get_target_property(python_interpreter Python::Interpreter LOCATION)
    if(WIN32)
        cmake_path(CONVERT "${python_interpreter}" TO_CMAKE_PATH_LIST python_interpreter NORMALIZE)
    endif()
    set(python_interpreter_found true)
else()
    set(python_interpreter_found false)
endif()

message(STATUS "   Python::Interpreter      : ${python_interpreter_found}")
message(STATUS "     => location property   : ${python_interpreter}")
message(STATUS "   Python_FOUND             : ${Python_FOUND}")
message(STATUS "   Python_EXECUTABLE        : ${Python_EXECUTABLE}")
message(STATUS "   Python_VERSION           : ${Python_VERSION}")
message(STATUS "   Python_SITELIB           : ${Python_SITELIB}")
message(STATUS "   Python_INCLUDE_DIRS      : ${Python_INCLUDE_DIRS}")
message(STATUS "   Python_LIBRARIES         : ${Python_LIBRARIES}")
message(STATUS "   Python_SOABI             : ${Python_SOABI}")
message(STATUS "   Python_NumPy_FOUND       : ${Python_NumPy_FOUND}")
message(STATUS "   Python_NumPy_VERSION     : ${Python_NumPy_VERSION}")
message(STATUS "   Python_NumPy_INCLUDE_DIRS: ${Python_NumPy_INCLUDE_DIRS}")

find_package(Pytest REQUIRED)

