#########-----PROJECT SETTING-----#########
cmake_minimum_required(VERSION 3.28)
project(5bex VERSION 0.0.1 DESCRIPTION "BUILD")

set(CMAKE_CXX_STANDARD 26)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Generating compile_commands.json for clangd
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

#########-----  DEPENDENCIES -----#########
# find_package(Boost REQUIRED COMPONENTS system)
# find_package(raylib CONFIG REQUIRED)

#########-----TARGET SETTING-----#########
set(SOURCE_EXE main.cpp
    # file here
)
add_executable(${PROJECT_NAME} ${SOURCE_EXE})
set_target_properties(PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
#########-----    LINKS     -----#########
target_link_libraries( ${PROJECT_NAME}
    PRIVATE
        # ws2_32
        # mswsock
        # Boost::system
        raylib
        stdc++exp # for std::print
)

# FOR RAYLIB
if(WIN32)
    target_link_libraries( ${PROJECT_NAME} 
       PRIVATE 
          winmm 
          gdi32 
          opengl32
    )
endif()
########-----     MISC      -----#########
# set(USERS_FILE ".env")
# if(NOT "" STREQUAL "")
#     add_custom_command(
#         TARGET  
#         POST_BUILD 
#         COMMAND  -E copy_if_different "/" "$<TARGET_FILE_DIR:>/"
#     )
# endif()
