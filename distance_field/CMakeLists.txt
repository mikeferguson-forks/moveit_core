set(MOVEIT_LIB_NAME moveit_distance_field)

add_library(${MOVEIT_LIB_NAME}
  src/distance_field.cpp
  src/propagation_distance_field.cpp
  src/find_internal_points.cpp
  )

target_link_libraries(${MOVEIT_LIB_NAME} ${catkin_LIBRARIES} ${console_bridge_LIBRARIES} ${urdfdom_LIBRARIES} ${urdfdom_headers_LIBRARIES} ${Boost_LIBRARIES})
add_dependencies(${MOVEIT_LIB_NAME} ${catkin_EXPORTED_TARGETS})

install(TARGETS ${MOVEIT_LIB_NAME}
  LIBRARY DESTINATION lib)

install(DIRECTORY include/
  DESTINATION include)

catkin_add_gtest(test_voxel_grid test/test_voxel_grid.cpp)
target_link_libraries(test_voxel_grid ${MOVEIT_LIB_NAME})

catkin_add_gtest(test_distance_field test/test_distance_field.cpp)
target_link_libraries(test_distance_field ${MOVEIT_LIB_NAME})
