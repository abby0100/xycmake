# CMake 最低版本 2.8
cmake_minimum_required (VERSION 2.8)
# 项目 sample
project (sample)
# 设定编译器
SET (CMAKE_CXX_COMPILER "g++")
# 指定版本号
set (SAMPLE_VERSION_MAJOR 1)
set (SAMPLE_VERSION_MINOR 1)

# 配置文件
configure_file (
	"${PROJECT_SOURCE_DIR}/SampleConfig.h.in"
	"${PROJECT_SOURCE_DIR}/SampleConfig.h"
)


# 设置生成目录
SET (EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET (LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR/lib})
# 设置头文件目录
INCLUDE_DIRECTORIES (
	/usr/include
	/usr/local/include
	${PROJECT_SOURCE_DIR}
	${PROJECT_SOURCE_DIR}/include
)
# 设置链接目录
LINK_DIRECTORIES (
	/usr/lib
	/usr/local/lib
	${PROJECT_SOURCE_DIR}/lib
)

## 查找并添加当前目录.下的所有源文件
aux_source_directory (${PROJECT_SOURCE_DIR}/src SRC)
ADD_SUBDIRECTORY (${PROJECT_SOURCE_DIR}/src)
#ADD_SUBDIRECTORY (${PROJECT_SOURCE_DIR}/tests)
#ADD_SUBDIRECTORY (${PROJECT_SOURCE_DIR}/unittests)


# 生成目标 xysample
add_executable (xysample ${SRC})
# 添加链接库
target_link_libraries (xysample power)
