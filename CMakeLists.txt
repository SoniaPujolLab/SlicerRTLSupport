# This is the CMake file for the RTLSupport module

cmake_minimum_required(VERSION 3.16.3...3.19.7 FATAL_ERROR)

project(RTLSupport)

#-----------------------------------------------------------------------------
# Extension meta-information
set(EXTENSION_HOMEPAGE "https://www.slicer.org/wiki/Documentation/Nightly/Extensions/RTLSupport")
set(EXTENSION_CONTRIBUTORS "Mohamed Alalli Bilal")
set(EXTENSION_DESCRIPTION "Adds RTL (Right-to-Left) support to 3D Slicer")
set(EXTENSION_CATEGORY "Utilities")
set(EXTENSION_STATUS "Beta")
set(EXTENSION_DEPENDS "")
set(EXTENSION_ICONURL "https://raw.githubusercontent.com/Slicer/ExtensionsIndex/master/Extensions/RTLSupport/icon.png")

#-----------------------------------------------------------------------------
# Extension dependencies
find_package(Slicer REQUIRED)
include(${Slicer_USE_FILE})

#-----------------------------------------------------------------------------
# Configure and include extension point settings
set(EXTENSION_NAME ${PROJECT_NAME})
set(MODULE_NAME ${EXTENSION_NAME})
set(MODULE_TITLE "RTL Support")
set(MODULE_CATEGORY "Utilities")

#-----------------------------------------------------------------------------
# Set the module type to SCRIPTED
set(MODULE_TYPE SCRIPTED)

# Set the module source file
set(MODULE_SRCS
  ${MODULE_NAME}.py
  )

# Set the module icon
set(MODULE_ICON "${MODULE_NAME}.png")

#-----------------------------------------------------------------------------
# Add module
add_slicer_scripted_module(
  ${MODULE_NAME}
  SCRIPT ${MODULE_SRCS}
  ICON ${MODULE_ICON}
  TITLE ${MODULE_TITLE}
  CATEGORY ${MODULE_CATEGORY}
  STATUS ${EXTENSION_STATUS}
  )

#-----------------------------------------------------------------------------
# Install the module
install(
  FILES ${MODULE_SRCS}
  DESTINATION ${Slicer_QTSCRIPTEDMODULES_BIN_DIR}/${MODULE_NAME}
  )

# Install the icon
install(
  FILES ${CMAKE_CURRENT_SOURCE_DIR}/${MODULE_ICON}
  DESTINATION ${Slicer_QTSCRIPTEDMODULES_SHARE_DIR}/${MODULE_NAME}
  )
