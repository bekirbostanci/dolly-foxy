cmake_minimum_required(VERSION 3.5)
project(dolly_description)


# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()


install(
  DIRECTORY
    meshes
    rviz
    urdf
  DESTINATION
    share/${PROJECT_NAME}/
)



ament_package()
