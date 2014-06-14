#/////////////////////////////////////////////////////////////////////////////
#
# PyGeo
#
#/////////////////////////////////////////////////////////////////////////////

cmake_minimum_required(VERSION 2.8)
project(gaia)

include(FindPythonInterp)
find_package(PythonInterp 2.7)
set(PYVER ${PYTHON_VERSION_MAJOR}.${PYTHON_VERSION_MINOR})

#/////////////////////////////////////////////////////////////////////////////
#
# PyGeo options
#
#/////////////////////////////////////////////////////////////////////////////
set(BUILD_TESTING OFF CACHE BOOL "Enable testing")

#/////////////////////////////////////////////////////////////////////////////
#
# Internal variables
#
#/////////////////////////////////////////////////////////////////////////////
set(PYGEO_DEPLOY_DIR "${CMAKE_CURRENT_BINARY_DIR}/deploy"
    CACHE PATH "PATH to deployment directory")

if (NOT PYGEO_BUILD_BASE)
  set(PYGEO_BUILD_BASE "${${PROJECT_NAME}_BINARY_DIR}")
endif()

# Install PyGeo
add_custom_target(gaia ALL
  COMMAND "${PYTHON_EXECUTABLE}" setup.py build --build-base "${PYGEO_BUILD_BASE}" install
          --prefix="${PYGEO_DEPLOY_DIR}"
  WORKING_DIRECTORY "${gaia_SOURCE_DIR}"
)

#/////////////////////////////////////////////////////////////////////////////
#
# Add pieces for testing if enabled
#
#/////////////////////////////////////////////////////////////////////////////

# Testing
if (BUILD_TESTING)
  include(CTest)
  enable_testing()
endif()