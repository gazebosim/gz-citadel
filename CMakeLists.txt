cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-citadel VERSION 1.0.2)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 2.9 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
ign_configure_project()

# all list of citadel packages

ign_find_package(ignition-common3 REQUIRED VERSION 3.14)
ign_find_package(ignition-fuel_tools4 REQUIRED VERSION 4.4)
ign_find_package(ignition-gazebo3 REQUIRED VERSION 3.12)
ign_find_package(ignition-gui3 REQUIRED VERSION 3.8)
ign_find_package(ignition-launch2 REQUIRED VERSION 2.2.2)
ign_find_package(ignition-math6 REQUIRED VERSION 6.9.2)
ign_find_package(ignition-msgs5 REQUIRED VERSION 5.8.1)
ign_find_package(ignition-physics2 REQUIRED VERSION 2.5)
ign_find_package(ignition-plugin1 REQUIRED VERSION 1.2.1)
ign_find_package(ignition-rendering3 REQUIRED VERSION 3.6)
ign_find_package(ignition-sensors3 REQUIRED VERSION 3.3)
ign_find_package(ignition-transport8 REQUIRED VERSION 8.2.1)
ign_find_package(sdformat9 REQUIRED VERSION 9.7.0)

if(build_warnings)
  set(all_warnings " CONFIGURATION WARNINGS:")
  foreach (msg ${build_warnings})
    ign_string_append(all_warnings " -- ${msg}" DELIM "\n")
  endforeach ()
  message(WARNING "${all_warnings}")
endif (build_warnings)

if(build_errors)
  message(SEND_ERROR "-- BUILD ERRORS: These must be resolved before compiling.")
  foreach(msg ${build_errors})
    message(SEND_ERROR "-- ${msg}")
  endforeach()
  message(SEND_ERROR "-- END BUILD ERRORS\n")

  set(error_str "Errors encountered in build. Please see BUILD ERRORS above.")

  message(FATAL_ERROR "${error_str}")

endif()

install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
