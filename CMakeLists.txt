#
# project: fips-parson
#
if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup(PROJECT fips-parson)
endif()

fips_begin_lib(parson)
    fips_include_directories(parson)
    fips_dir(parson)
    fips_files(parson.c parson.h)
fips_end_lib()

if (NOT FIPS_IMPORT)
    fips_begin_app(parson_tests cmdline)
        fips_dir(parson)
        fips_files(
            tests.c
        )
        fips_deps(parson)
    fips_end_app()

    fips_finish()
endif()
