set(dfs_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/src/dfs.c
    ${CMAKE_CURRENT_LIST_DIR}/src/dfs_file.c
    ${CMAKE_CURRENT_LIST_DIR}/src/dfs_fs.c
    ${CMAKE_CURRENT_LIST_DIR}/src/dfs_posix.c
)
set(dfs_INCS ${CMAKE_CURRENT_LIST_DIR}/include
             # CACHE INTERNAL ""
)

file(GLOB dfs_elm_SRCS ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/*.c)

if(DEFINED RT_DFS_ELM_USE_LFN)
  if(DEFINED RT_DFS_ELM_CODE_PAGE_FILE)
    list(APPEND dfs_elm_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/file.c)
  else()
    if(${RT_DFS_ELM_CODE_PAGE} STREQUAL 932)
      list(APPEND dfs_elm_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/cc932.c)
    elseif(${RT_DFS_ELM_CODE_PAGE} STREQUAL 936)
      list(APPEND dfs_elm_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/cc936.c)
    elseif(${RT_DFS_ELM_CODE_PAGE} STREQUAL 949)
      list(APPEND dfs_elm_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/cc949.c)
    elseif(${RT_DFS_ELM_CODE_PAGE} STREQUAL 950)
      list(APPEND dfs_elm_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/cc950.c)
    else(if (${RT_DFS_ELM_CODE_PAGE} STREQUAL 950))
      list(APPEND dfs_elm_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/filesystems/elmfat/option/ccsbcs.c)
    endif()
  endif()
endif()
  
if(DEFINED RT_USING_DFS_ELMFAT)
  list(APPEND dfs_SRCS ${dfs_elm_SRCS})
  list(APPEND dfs_INCS ${CMAKE_CURRENT_LIST_DIR}/elmfat)
endif()

if(DEFINED RT_USING_POSIX)
  list(APPEND dfs_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/poll.c
       ${CMAKE_CURRENT_LIST_DIR}/src/select.c)
endif()

if(DEFINED RT_USING_DFS AND DEFINED RT_USING_DFS_DEVFS)
  list(APPEND dfs_SRCS ${CMAKE_CURRENT_LIST_DIR}/filesystems/devfs/devfs.c)
  list(APPEND dfs_INCS ${CMAKE_CURRENT_LIST_DIR}/filesystems/devfs)
endif()

# if(DEFINED RT_USING_DFS) list(APPEND components_SRCS ${dfs_SRCS}) list(APPEND
# components_INCS ${dfs_INCS}) endif()
set(dfs_SRCS
    ${dfs_SRCS}
    CACHE INTERNAL "")
set(dfs_INCS
    ${dfs_INCS}
    CACHE INTERNAL "")

# message(STATUS "dfs inc ${dfs_INCS}")
