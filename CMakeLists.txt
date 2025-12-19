cmake_minimum_required(VERSION 3.18)
project(kwin-effects-yaml)

set(KF_MIN_VERSION "6.0")
set(QT_MIN_VERSION "6.6")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(ECM ${KF_MIN_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH
    ${CMAKE_MODULE_PATH}
    ${ECM_MODULE_PATH}
    ${ECM_KDE_MODULE_DIR}
    ${CMAKE_SOURCE_DIR}/cmake
    ${CMAKE_SOURCE_DIR}/cmake/Modules
)

include(FeatureSummary)
include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)

find_package(Qt6 REQUIRED COMPONENTS
    Core
    Gui
)

find_package(KF6 ${KF_MIN_VERSION} REQUIRED COMPONENTS
    Config
    ConfigWidgets
    CoreAddons
    WindowSystem
)

find_package(KWinEffects REQUIRED COMPONENTS
    kwin_effects
    kwin_opengl
)

find_package(KWinDBusInterface CONFIG REQUIRED)

find_package(epoxy REQUIRED)

add_subdirectory(src)

feature_summary(WHAT ALL)
