# This is gonna instruct cmake how we want to generate our project file

# specify the minimum version for cmake that is required for our project
cmake_minimum_required (VERSION 3.5)

# set the project name
project (HelloWorld_Linux)

# setup some general variables that are needed
# basically what we did here is we specified that we want the basic CXX flags for compilation
# i.e. we want all warnings enabled as well as erros
# and use c++14 version as our C++ standard code.
# (Doesn't really matter for a Hello World project)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}" -Wall -Werror -std=c++14)

# so the CMakeLists.txt is inside the parent directory and below we specify where is our source directory
# so basically from the current one to the /src/
# where our source .cpp files will be stored
set (source_dir "${PROJECT_SOURCE_DIR}/src/")

# Now that we basically set our variables (aka FLAGS)
# we need to tell the compiler which files to compile

# inside the source directory compile everything that ends with .cpp
file (GLOB source_files "${source_dir}/*.cpp")

# if we had an include directory for .h files we would also have to set that up

# and now we need to add our executable
add_executable (HelloWorld ${source_files})
