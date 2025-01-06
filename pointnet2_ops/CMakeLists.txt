
Python_add_library(${BUILD_TARGET})
target_compile_definitions(${BUILD_TARGET} PRIVATE TORCH_EXTENSION_NAME=${BUILD_TARGET})
add_subdirectory("_ext-src")

target_link_libraries(${BUILD_TARGET} PUBLIC
  pybind11::headers
  ${TORCH_LIBRARIES}
  ${TORCH_PYTHON_LIBRARY}
)

if (OPENMP_FOUND)
  target_link_libraries(${BUILD_TARGET} PRIVATE OpenMP::OpenMP_CXX)
endif()

set_target_properties(${BUILD_TARGET} PROPERTIES
  INTERPROCEDURAL_OPTIMIZATION ON
  CXX_VISIBILITY_PRESET "hidden")

target_compile_definitions(${BUILD_TARGET} PRIVATE VERSION_INFO=${PROJECT_VERSION})

pybind11_extension(${BUILD_TARGET})
pybind11_strip(${BUILD_TARGET})
