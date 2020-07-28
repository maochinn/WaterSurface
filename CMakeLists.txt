cmake_minimum_required(VERSION 2.8)

project(WaterSurface)
set(SRC_DIR ${PROJECT_SOURCE_DIR}/src/)
set(INCLUDE_DIR ${PROJECT_SOURCE_DIR}/include/)
set(LIB_DIR ${PROJECT_SOURCE_DIR}/lib/)

include_directories(${INCLUDE_DIR})
include_directories(${SRC_DIR})
include_directories(${INCLUDE_DIR}glad4.6/include/)
include_directories(${INCLUDE_DIR}glm-0.9.8.5/glm/)

add_Definitions("-D_XKEYCHECK_H")

add_executable(WaterSurface
    ${SRC_DIR}CallBacks.h
    ${SRC_DIR}ControlPoint.h
    ${SRC_DIR}Object.h
    ${SRC_DIR}Track.h
    ${SRC_DIR}TrainView.h
    ${SRC_DIR}TrainWindow.h

    ${SRC_DIR}main.cpp
    ${SRC_DIR}CallBacks.cpp
    ${SRC_DIR}ControlPoint.cpp
    ${SRC_DIR}Track.cpp
    ${SRC_DIR}TrainView.cpp
    ${SRC_DIR}TrainWindow.cpp

    ${SRC_DIR}RenderUtilities/BufferObject.h
    ${SRC_DIR}RenderUtilities/Shader.h
    ${SRC_DIR}RenderUtilities/Texture.h
    
    ${INCLUDE_DIR}glad4.6/src/glad.c
)

add_library(Utilities 
    ${SRC_DIR}Utilities/3DUtils.h
    ${SRC_DIR}Utilities/ArcBallCam.h
    ${SRC_DIR}Utilities/Pnt3f.h
    ${SRC_DIR}Utilities/3DUtils.cpp
    ${SRC_DIR}Utilities/ArcBallCam.cpp
    ${SRC_DIR}Utilities/Pnt3f.cpp)

target_link_libraries(WaterSurface debug 
    ${LIB_DIR}Debug/fltk_formsd.lib 
    ${LIB_DIR}Debug/fltk_gld.lib
    ${LIB_DIR}Debug/fltk_imagesd.lib
    ${LIB_DIR}Debug/fltk_jpegd.lib
    ${LIB_DIR}Debug/fltk_pngd.lib
    ${LIB_DIR}Debug/fltk_zd.lib
    ${LIB_DIR}Debug/fltkd.lib
    ${LIB_DIR}Debug/opencv_world341d.lib)

target_link_libraries(WaterSurface optimized 
    ${LIB_DIR}Release/fltk_forms.lib
    ${LIB_DIR}Release/fltk_gl.lib
    ${LIB_DIR}Release/fltk_images.lib
    ${LIB_DIR}Release/fltk_jpeg.lib
    ${LIB_DIR}Release/fltk_png.lib
    ${LIB_DIR}Release/fltk_z.lib
    ${LIB_DIR}Release/opencv_world341.lib)

target_link_libraries(WaterSurface 
    ${LIB_DIR}OpenGL32.lib
    ${LIB_DIR}glu32.lib)

target_link_libraries(WaterSurface Utilities)
    