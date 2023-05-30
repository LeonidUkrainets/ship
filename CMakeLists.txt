cmake_minimum_required(VERSION 3.16)

project(project36ship VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

qt_add_executable(appproject36ship
    main.cpp
)

qt_add_qml_module(appproject36ship
    URI project36ship
    VERSION 1.0
    QML_FILES Main.qml Page.qml
    RESOURCES ship.png
)

set_target_properties(appproject36ship PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appproject36ship
    PRIVATE Qt6::Quick
)

install(TARGETS appproject36ship
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
