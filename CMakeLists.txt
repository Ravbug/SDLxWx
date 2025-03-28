cmake_minimum_required(VERSION 3.16)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/$<CONFIGURATION>)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/$<CONFIGURATION>)

project(SDLxWx)

# SDL Stuff
add_subdirectory(SDL EXCLUDE_FROM_ALL)

# wxWidgets stuff
set(wxBUILD_SHARED OFF CACHE INTERNAL "")
add_subdirectory(wxWidgets EXCLUDE_FROM_ALL)

add_executable(${PROJECT_NAME} WIN32 main.cpp)
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_23)

# Link it all up
target_link_libraries(${PROJECT_NAME} PRIVATE wx::core wx::base SDL3::SDL3)

set_target_properties(${PROJECT_NAME} PROPERTIES
    MACOSX_BUNDLE TRUE
    XCODE_GENERATE_SCHEME TRUE
)

install(TARGETS ${PROJECT_NAME}
    BUNDLE  DESTINATION .
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT "${PROJECT_NAME}")
