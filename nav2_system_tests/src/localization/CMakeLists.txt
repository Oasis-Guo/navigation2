ament_add_gtest_executable(test_localization_node
  test_localization_node.cpp
)
ament_target_dependencies(test_localization_node
  ${dependencies}
)


ament_add_test(test_localization
  GENERATE_RESULT_FOR_RETURN_CODE_ZERO
  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/test_localization_launch.py"
  TIMEOUT 20
  ENV
    TEST_MAP=${PROJECT_SOURCE_DIR}/maps/map_circular.yaml
    TEST_EXECUTABLE=$<TARGET_FILE:test_localization_node>
    TEST_WORLD=${PROJECT_SOURCE_DIR}/worlds/turtlebot3_ros2_demo.world
    GAZEBO_MODEL_PATH=${PROJECT_SOURCE_DIR}/models
)
