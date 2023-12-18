cmake_minimum_required(VERSION 3.10)

project(ffigen_app_library VERSION 0.0.1 LANGUAGES C)

add_library(ffigen_app SHARED
  duktape.c                     # Modify
)

set_target_properties(ffigen_app PROPERTIES
  PUBLIC_HEADER duktape.h       # Modify
  PRIVATE_HEADER duk_config.h   # Add
  OUTPUT_NAME "ffigen_app"      # Add
)

# Add from here...
if (WIN32)
set_target_properties(ffigen_app PROPERTIES
  WINDOWS_EXPORT_ALL_SYMBOLS ON
)
endif (WIN32)
# ... to here.

target_compile_definitions(ffigen_app PUBLIC DART_SHARED_LIB)
