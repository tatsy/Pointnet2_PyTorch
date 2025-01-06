target_include_directories(${BUILD_TARGET} PUBLIC
  ${PYTHON_INCLUDE_DIRS}
  ${CUDA_INCLUDE_DIRS}
  ${TORCH_INCLUDE_DIRS}
  ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_sources(${BUILD_TARGET} PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}/bindings.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/ball_query_gpu.cu
  ${CMAKE_CURRENT_SOURCE_DIR}/src/ball_query.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/group_points_gpu.cu
  ${CMAKE_CURRENT_SOURCE_DIR}/src/group_points.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/interpolate_gpu.cu
  ${CMAKE_CURRENT_SOURCE_DIR}/src/interpolate.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/sampling_gpu.cu
  ${CMAKE_CURRENT_SOURCE_DIR}/src/sampling.cpp
)
