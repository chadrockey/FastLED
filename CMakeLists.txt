# FastLED
# https://github.com/FastLED/FastLED
# MIT License

project(FastLED)

cmake_minimum_required(VERSION 3.5)

set(FastLED_SRCS
  src/bitswap.cpp
  src/colorpalettes.cpp
  src/colorutils.cpp
  src/FastLED.cpp
  src/five_bit_hd_gamma.cpp
  src/hsv2rgb.cpp
  src/lib8tion.cpp
  src/noise.cpp
  src/platforms.cpp
  src/power_mgt.cpp
  src/unix_helpers.cpp
  src/wiring.cpp
  )


include_directories(src)

add_library(fastled ${FastLED_SRCS})

add_executable(fastled_demo examples/LinuxDemo/LinuxDemo.cpp)
target_link_libraries(fastled_demo fastled)

install(TARGETS fastled DESTINATION lib)
install(DIRECTORY src/ DESTINATION include FILES_MATCHING PATTERN "*.h")
install(DIRECTORY src/lib8tion/ DESTINATION include/lib8tion FILES_MATCHING PATTERN "*.h")
install(DIRECTORY src/platforms DESTINATION include/platforms FILES_MATCHING PATTERN "*.h")

install(TARGETS fastled_demo DESTINATION bin)
