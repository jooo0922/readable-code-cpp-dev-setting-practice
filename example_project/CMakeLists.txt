# 필요한 CMake 최소 버전 명시
cmake_minimium_required(VERSION 3.11)

# 프로젝트 관련 변수 생성
set(PACKAGE_NAME READABLE_CODE-CPP-CORE_DEVELOPMENT_ENVIRONMENT_SETTING)
set(PACKAGE_VERSION 1.0.1)

# 프로젝트 이름, 버전, 언어 지정
project(${PACKAGE_NAME} VERSION ${PACKAGE_VERSION} LANGUAGES CXX)

# CMake 내장변수 설정
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# CPack 관련 내장변수 설정
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})

# CPack 모듈 로드
include(CPack)

# 파일 경로 관련 변수 생성
set(${PACKAGE_NAME}_PATH ${CMAKE_CURRENT_SOURCE_DIR})
set(${PACKAGE_NAME}_SOURCE_PATH "${${PACKAGE_NAME}_PATH}/src")

# STATUS 모드로 메시지 출력 (메시지 앞에 -- 이 붙어서 강조 표시됨)
message(STATUS "PACKAGE_NAME: ${PACKAGE_NAME}")
message(STATUS "PACKAGE_VERSION: ${PACKAGE_VERSION}")
message(STATUS "${PACKAGE_NAME}_PATH: ${${PACKAGE_NAME}_PATH}")
message(STATUS "${PACKAGE_NAME}_SOURCE_PATH: ${${PACKAGE_NAME}_SOURCE_PATH}")

# 타겟 프로그램 정의
add_executable(${PACKAGE_NAME}_MAIN src/main.cpp)

# 타겟을 컴파일할 때 사용할 컴파일 옵션을 지정
target_compile_options(${PACKAGE_NAME}_MAIN PRIVATE 
  -Wall -Wextra -Wpedantic -Werror
)

