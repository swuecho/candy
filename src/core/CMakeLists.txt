aux_source_directory(. DIR_LIB_SRCS)
add_library(core STATIC ${DIR_LIB_SRCS})

set_target_properties(core PROPERTIES CXX_STANDARD 20)

find_package(PkgConfig REQUIRED)
pkg_check_modules(DEPS REQUIRED fmt spdlog)

add_definitions(${DEPS_CFLAGS})
include_directories(${DEPS_INCLUDEDIR})
target_link_libraries(core PRIVATE ${DEPS_LIBRARIES})

target_link_libraries(core PRIVATE websocket)
target_link_libraries(core PRIVATE tun)
target_link_libraries(core PRIVATE peer)
