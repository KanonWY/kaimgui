find_package(PkgConfig REQUIRED QUIET)

pkg_search_module(
    GL
    REQUIRED
    gl
    IMPORTED_TARGET
)

if(TARGET PkgConfig::GL)
    message(STATUS "FOUND PkgConfig::GL")
else()
    message(STATUS "NOT FOUND PkgConfig::GL")
endif()

pkg_search_module(
    GLFW3
    REQUIRED
    glfw3
    IMPORTED_TARGET
)

if(TARGET PkgConfig::GLFW3)
    message(STATUS "FOUND PkgConfig::GLFW3")
else()
    message(STATUS "NOT FOUND PkgConfig::GLFW3")
endif()

file(GLOB BACK_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

add_library(ka_imgui_core SHARED ${BACK_SOURCE})
target_link_libraries(ka_imgui_core imgui_interface PkgConfig::GL PkgConfig::GLFW3)
target_include_directories(ka_imgui_core PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})