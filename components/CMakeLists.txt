add_subdirectory(cplusplus)
add_subdirectory(dfs)
add_subdirectory(drivers)
add_subdirectory(finsh)
add_subdirectory(libc)
add_subdirectory(net)
add_subdirectory(utilities)

set(COM_DIR ${CMAKE_CURRENT_LIST_DIR})

# add_library(finsh ${finsh_SRCS}) target_include_directories(finsh PUBLIC
# ${COM_DIR}/finsh ${rt_DIR}/include rt-thread_INCS)

set(GLOB_RECURSE libc_SRCS ./lib/*.c)
# message(${libc_SRCS})

set(components_SRCS
    ${utilities_SRCS} ${com_drivers_SRCS} ${libc_SRCS} ${net_SRCS}
    # CACHE INTERNAL ""
)

set(components_INCS
    ${utilities_INCS} ${com_drivers_INCS} ${libc_INCS} ${net_INCS}
    # CACHE INTERNAL ""
)

if(DEFINED RT_USING_DFS)
  list(APPEND components_SRCS ${dfs_SRCS})
  list(APPEND components_INCS ${dfs_INCS})
endif()
if(DEFINED RT_USING_FINSH)
  list(APPEND components_SRCS ${finsh_SRCS})
  list(APPEND components_INCS ${finsh_INCS})
endif()

set(components_SRCS
    ${components_SRCS}
    CACHE INTERNAL "")
set(components_INCS
    ${components_INCS}
    CACHE INTERNAL "")

# message(STATUS "component utilis src ${utilities_SRCS}") message(STATUS
# "components src ${components_SRCS}") message(STATUS "components inc
# ${components_INCS}")
# message(STATUS "componets driver src ${com_drivers_SRCS}")
# message(STATUS "componets dfs src ${dfs_SRCS}")
