file(GLOB INTERFACE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")
add_library(imgui_interface SHARED ${INTERFACE_SOURCES})
target_include_directories(imgui_interface PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})