# get the main sources
file(GLOB SRCS RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} src/*.cpp src/*.h)
source_group("" FILES ${SRCS})

# get platform specific sources
if (WIN32)
    set(PLAT_DIR Win32)
else()
    set(PLAT_DIR Posix)
endif(WIN32)
file(GLOB PLAT_SRCS RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} src/${PLAT_DIR}/*.cpp src/${PLAT_DIR}/*.h)
source_group(${PLAT_DIR} FILES ${PLAT_SRCS})

# create the lib
add_library(UnitTestPP STATIC ${SRCS} ${PLAT_SRCS})
set_target_properties(UnitTestPP PROPERTIES OUTPUT_NAME UnitTest++)
include_directories(src)

