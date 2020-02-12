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

# function
function(get_message MESSAGE)
    message( "MESSAGE is ${MESSAGE}, followed by ${ARGV}")
    set(${MESSAGE} "hello from my_func" PARENT_SCOPE)
endfunction()

get_message(MESSAGE)
message("MESSAGE: ${MESSAGE}")

# find package
find_package(Git QUIET)
message("GIT_EXECUTABLE: ${GIT_EXECUTABLE}")

# files
file(GLOB FILES *.*)
message("FILES: ${FILES}")
