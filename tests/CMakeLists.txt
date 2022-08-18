# for each .c file in the directory
file(GLOB test_files *.c)
foreach(filename ${test_files})		

  # make an executable named after the source file
  get_filename_component(testname ${filename} NAME_WE)
  add_executable(${testname} ${filename})
  add_test(${testname} ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${testname})		

  # and link it against GKlib
  target_link_libraries(${testname} PUBLIC GKlib)

endforeach(filename ${test_files})

# Install a subset of them
install(TARGETS csrcnv RUNTIME DESTINATION bin)
