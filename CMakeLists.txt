
cmake_minimum_required(VERSION 2.8)
project(camcv)
#OPENCV
find_package(OpenCV REQUIRED)
SET(COMPILE_DEFINITIONS -Werror)

include_directories(~/opt/vc/host_applications/linux/libs/bcm_host/include)
include_directories(~/opt/vc/interface/vcos)
include_directories(~/opt/vc)
include_directories(~/opt/vc/interface/vcos/pthreads)
include_directories(~/opt/vc/interface/vmcs_host/linux)

add_executable(camcv RaspiCamControl.c RaspiCLI.c RaspiPreview.c camcv_vid0.c)

target_link_libraries(camcv ~/opt/vc/build/lib/libmmal_core.so ~/opt/vc/build/lib/libmmal_util.so ~/opt/vc/build/lib/libmmal_vc_client.so ~/opt/vc/build/lib/libvcos.so ~/opt/vc/build/lib/libbcm_host.so ${OpenCV_LIBS})

