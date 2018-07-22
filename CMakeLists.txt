cmake_minimum_required(VERSION 3.2)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.1.tar.gz"
    SHA1 "51d2d6be411251c8de18c4ca20ef778880cf4cce"
)

project(libsodium-example)

hunter_add_package(libsodium)
find_package(libsodium CONFIG REQUIRED)

add_executable(simple simple.cpp)
target_link_libraries(simple PUBLIC libsodium::libsodium)

hunter_add_package(gauze)
find_package(gauze CONFIG REQUIRED)

enable_testing()
gauze_add_test(NAME simple COMMAND simple)
