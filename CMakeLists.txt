cmake_minimum_required(VERSION 3.8)
project(GKLIB_PROJ LANGUAGES C)

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

set(CMAKE_C_STANDARD 11)

file(GLOB sources ${PROJECT_SOURCE_DIR}/src/*.c)
file(GLOB headers ${PROJECT_SOURCE_DIR}/include/*.h)

add_library(GKlib ${sources} ${headers})
target_include_directories(GKlib PUBLIC ${PROJECT_SOURCE_DIR}/include)

if (ENABLE_TESTING)
  enable_testing()
  add_subdirectory(tests)
endif()

install(TARGETS GKlib DESTINATION lib)                                           
install(FILES ${headers} DESTINATION include) 
