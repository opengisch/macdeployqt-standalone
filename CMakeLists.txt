cmake_minimum_required(VERSION 3.16)
project(macdeployqt-standalone)

find_library(FW_CORE_FOUNDATION CoreFoundation)
add_executable(macdeployqt-standalone macdeployqt/main.cpp shared/shared.cpp)

find_package(Qt6 COMPONENTS Core)
target_link_libraries(macdeployqt-standalone PRIVATE Qt::Core ${FW_CORE_FOUNDATION})

set_target_properties(macdeployqt-standalone PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)

install(TARGETS macdeployqt-standalone
    RUNTIME DESTINATION bin
)
