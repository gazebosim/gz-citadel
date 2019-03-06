cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-acropolis VERSION 1.0.0)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 2.0.0 REQUIRED)

#============================================================================
# Configure the project
#============================================================================
ign_configure_project()

# all list of acropolis packages

ign_find_package(ignition-common3 REQUIRED)
ign_find_package(ignition-fuel_tools3 REQUIRED)
ign_find_package(ignition-gazebo0 REQUIRED)
ign_find_package(ignition-gui1 REQUIRED)
ign_find_package(ignition-launch0 REQUIRED)
ign_find_package(ignition-math6 REQUIRED)
ign_find_package(ignition-msgs3 REQUIRED)
ign_find_package(ignition-plugin1 REQUIRED)
ign_find_package(ignition-physics1 REQUIRED)
ign_find_package(ignition-sensors1 REQUIRED)
ign_find_package(ignition-tools REQUIRED)
ign_find_package(ignition-transport6 REQUIRED)


install(DIRECTORY gazebodistro DESTINATION ${IGN_DATA_INSTALL_DIR})
