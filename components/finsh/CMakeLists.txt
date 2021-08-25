# file(GLOB finsh_SRCS ./finsh/*.c) list(REMOVE_ITEM ${finsh_SRCS}
# "./finsh/symbol.c$" "./finsh/msh_file.c$") list(APPEND ${finsh_SRCS}
# ${COM_DIR}finsh/symbol.c # ${COM_DIR}finsh/msh_file.c )

set(finsh_SRCS ${CMAKE_CURRENT_LIST_DIR}/shell.c
              ${CMAKE_CURRENT_LIST_DIR}/symbol.c
               ${CMAKE_CURRENT_LIST_DIR}/cmd.c)

set(fsh_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/finsh_compiler.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_error.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_heap.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_init.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_node.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_ops.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_parser.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_var.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_vm.c
    ${CMAKE_CURRENT_LIST_DIR}/finsh_token.c)

set(msh_SRCS ${CMAKE_CURRENT_LIST_DIR}/msh.c)

if(DEFINED RT_USING_DFS)
  list(APPEND msh_SRCS ${CMAKE_CURRENT_LIST_DIR}/msh_file.c)
endif()

# if(NOT DEFINED FINSH_USING_SYMTAB)
#   list(APPEND finsh_SRCS ${CMAKE_CURRENT_LIST_DIR}/symbol.c)
# endif()
if(DEFINED FINSH_USING_MSH)
  list(APPEND finsh_SRCS ${msh_SRCS})
endif()
if(NOT DEFINED FINSH_USING_MSH_ONLY)
  list(APPEND finsh_SRCS ${fsh_SRCS})
endif()

set(finsh_SRCS
    ${finsh_SRCS}
    CACHE INTERNAL "")
set(finsh_INCS
    ${CMAKE_CURRENT_LIST_DIR}
    CACHE INTERNAL "")
