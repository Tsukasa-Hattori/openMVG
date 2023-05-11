
add_library(openMVG_camera INTERFACE)
set_property(TARGET openMVG_camera APPEND PROPERTY
  INTERFACE_INCLUDE_DIRECTORIES "$<INSTALL_INTERFACE:include>")

target_compile_features(openMVG_camera INTERFACE ${CXX11_FEATURES})
target_link_libraries(openMVG_camera INTERFACE openMVG_numeric ${cereal_TARGET} ${OPENMVG_LIBRARY_DEPENDENCIES})
install(TARGETS openMVG_camera EXPORT openMVG-targets)

add_test(openMVG Camera_Pinhole openMVG_camera)

add_test(openMVG Camera_Pinhole_Radial openMVG_camera)

add_test(openMVG Camera_Pinhole_Brown openMVG_camera)

add_test(openMVG Camera_Pinhole_Fisheye openMVG_camera)

add_test(openMVG Camera_Spherical openMVG_camera)

add_test(openMVG Camera_Subset_Parametrization openMVG_camera)

add_library(openMVG_camera_test INTERFACE)
target_link_libraries(openMVG_camera_test INTERFACE openMVG_camera)

add_test(openMVG Camera_IO "openMVG_camera_test;${STLPLUS_LIBRARY}")
