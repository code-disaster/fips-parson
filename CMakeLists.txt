#
# project: fips-parson
#
cmake_minimum_required(VERSION 2.8)

# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

fips_begin_lib(parson)
    
    include_directories(parson)

    fips_dir(parson)
    fips_files(parson.c parson.h)

fips_end_lib()

if (FIPS_WINDOWS)
    set_target_properties(parson PROPERTIES COMPILE_FLAGS "/wd4242 /wd4244 /wd4702")
endif()
