cmake_minimum_required(VERSION 3.1)

project(MyProject VERSION 1.0
                  DESCRIPTION "Very nice project"
                  LANGUAGES CXX)

# variables
set(MY_VARIABLE "john")
set(MY_LIST "one" "two" "three")
set(MY_LIST2 "one;two")

# output to stdout
message("MY_VARIABLE is ${MY_VARIABLE}")
message("MY_LIST is ${MY_LIST}")

# if
set(DO_WORK true)
if(DO_WORK)
  message("doing work ... DO_WORK = ${DO_WORK}")
else()
    message("not doing work ...")
endif()

# function
function(get_message MESSAGE)
    message( "MESSAGE is ${MESSAGE}, followed by ${ARGV}")
    # this is how you return a value from a function
    set(${MESSAGE} "hello from my_func" PARENT_SCOPE)
endfunction()

# call function.  output is stored in `MESSAGE`
get_message(MESSAGE)
message("MESSAGE: ${MESSAGE}")

# find package.  this makes the GIT_ variables available
find_package(Git QUIET)
message("GIT_EXECUTABLE: ${GIT_EXECUTABLE}")

# find program
find_program(PROGRAM NAMES curl)
message("PROGRAM: ${PROGRAM}")

# files
file(GLOB FILES *.*)
message("FILES: ${FILES}")

# loop over list
foreach(FILE ${FILES})
    message("FILE: ${FILE}")
endforeach()

# get file path of first file in FILES list
list(GET FILES 0 FILE_PATH)
message("FILE_PATH: ${FILE_PATH}")
get_filename_component(DIR ${FILE_PATH} DIRECTORY)
message("DIR: ${DIR}")

# execute process
execute_process(COMMAND ls
                OUTPUT_VARIABLE LS_OUTPUT
                OUTPUT_STRIP_TRAILING_WHITESPACE)

message("LS_OUTPUT: ${LS_OUTPUT}")

# convert newline delimited values to a list "item1;item2;..."
string(REGEX REPLACE "\n" ";" LS_OUTPUT "${LS_OUTPUT}")

# loop over list
foreach(FILE ${LS_OUTPUT})
    message("FILE: ${FILE}")
endforeach()
