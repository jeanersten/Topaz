add_executable(Topaz
  "source/Topaz.cpp"

  "source/Topaz.h"
)

if(CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET Topaz PROPERTY CXX_STANDARD 20)
endif()

target_link_libraries(Topaz PRIVATE SDL3::SDL3)

add_custom_command(TARGET Topaz POST_BUILD
  COMMAND "${CMAKE_COMMAND}" -E copy $<TARGET_FILE:SDL3::SDL3-shared> $<TARGET_FILE_DIR:Topaz>
  VERBATIM
)
