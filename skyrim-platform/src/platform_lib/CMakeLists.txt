if(MSVC)
    include(${CMAKE_SOURCE_DIR}/cmake/apply_default_settings.cmake)

    file(GLOB_RECURSE sources "${CMAKE_CURRENT_SOURCE_DIR}/*.h" "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")
    add_library(platform_lib STATIC ${sources})
    target_link_libraries(platform_lib PUBLIC viet)
    target_include_directories(platform_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
    target_include_directories(platform_lib PUBLIC "${CMAKE_SOURCE_DIR}/1js")
    target_include_directories(platform_lib PUBLIC "${SKYRIM_PLATFORM_SOURCE_DIR}/src/third_party")

    find_package(unofficial-node-addon-api REQUIRED)
    target_link_libraries(platform_lib PUBLIC unofficial::node-addon-api::node-addon-api)

    apply_default_settings(TARGETS platform_lib)
endif()
