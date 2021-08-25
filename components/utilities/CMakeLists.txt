set(utilities_SRCS ""
                   # CACHE INTERNAL ""
)
set(utilities_INCS # ${CMAKE_CURRENT_LIST_DIR}/ulog
    ""
    # CACHE INTERNAL ""
)

file(GLOB utest_SRCS ./utest/*.c)
file(GLOB ymodem_SRCS ./ymodem/*.c)
file(GLOB zmodem_SRCS ./zmodem/*.c)

if(DEFINED ULOG_BACKEND_USING_CONSOLE)
  list(APPEND utilities_SRCS
       ${CMAKE_CURRENT_LIST_DIR}/ulog/backend/console_be.c)
endif()
if(DEFINED ULOG_USING_SYSLOG)
  list(APPEND utilities_SRCS ${CMAKE_CURRENT_LIST_DIR}/ulog/syslog/syslog.c)
  list(APPEND utilities_INCS ${CMAKE_CURRENT_LIST_DIR}/ulog/syslog)
endif()
if(DEFINED RT_USING_ULOG)
  list(APPEND utilities_SRCS ${CMAKE_CURRENT_LIST_DIR}/ulog/ulog.c)
  list(APPEND utilities_INCS ${CMAKE_CURRENT_LIST_DIR}/ulog)
endif()

if(DEFINED RT_USING_UTEST)
  list(APPEND utilities_SRCS ${CMAKE_CURRENT_LIST_DIR}/utest/utest.c)
  list(APPEND utilities_INCS ${CMAKE_CURRENT_LIST_DIR}/utest)
endif()
if(DEFINED RT_USING_RYM)
  list(APPEND utilities_SRCS ${CMAKE_CURRENT_LIST_DIR}/ymodem/ymodem.c)
  list(APPEND utilities_INCS ${CMAKE_CURRENT_LIST_DIR}/ymodem)
endif()
if(DEFINED RT_USING_DFS AND DEFINED YMODEM_USING_FILE_TRANSFER)
  list(APPEND utilities_SRCS ${CMAKE_CURRENT_LIST_DIR}/ymodem/ry_sy.c)
endif()
# if(DEFINED ) endif()

set(utilities_SRCS
    ${utilities_SRCS}
    CACHE INTERNAL "")
set(utilities_INCS
    ${utilities_INCS}
    CACHE INTERNAL "")

# message(STATUS "utilites src ${utilities_SRCS}")
