cmake_minimum_required(VERSION 3.13)
project(stb)

set(headers
    stb_connected_components.h
    stb_divide.h
    stb_dxt.h
    stb_easy_font.h
    stb_herringbone_wang_tile.h
    stb_image_resize.h
    stb_image_write.h
    stb_image.h
    stb_perlin.h
    stb_rect_pack.h
    stb_truetype.h
    stb_voxel_render.h
    stb.h
)

set(sources 
    jam/stb_divide.cpp
    jam/stb_dxt.cpp
    jam/stb_image_resize.cpp
    jam/stb_image_write.cpp
    jam/stb_image.cpp
    jam/stb_perlin.cpp
    jam/stb_rect_pack.cpp
    jam/stb_truetype.cpp
)

foreach(f ${headers})
    configure_file(${f} "include-fwd/stb/${f}" COPYONLY)
endforeach()

add_library(stb
    STATIC ${headers} ${sources}
)
target_include_directories(stb 
    PUBLIC ${CMAKE_CURRENT_BINARY_DIR}/include-fwd
)
