set(libc_SRCS "")
set(libc_INCS "")

if(DEFINED RT_USING_POSIX AND DEFINED RT_USING_POSIX_AIO)
  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/aio/posix_aio.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/aio)

endif()
if(DEFINED RT_USING_LIBC)
  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/common/time.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/aio)

endif()
if(DEFINED RT_USING_MINILIBC AND NOT DEFINED RT_USING_LIBC)
  file(GLOB minilic_SRCS ${CMAKE_CURRENT_LIST_DIR}/compilers/minilibc/*.c)

  list(APPEND libc_SRCS ${minilibc_SRCS})
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/compilers/minilibc/sys)

endif()

if(DEFINED RT_USING_LIBC) # TODO gcc
  file(GLOB newlibc_SRCS ${CMAKE_CURRENT_LIST_DIR}/compilers/newlib/*.c)

  list(APPEND libc_SRCS ${newlibc_SRCS})
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/compilers/newlib)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/compilers/newlib/sys)

endif()

if(DEFINED RT_USING_MODULE)
  file(GLOBAL libdll_SRCS ${CMAKE_CURRENT_LIST_DIR}/libdll/*.c)

  list(APPEND libc_SRCS ${libdll_SRCS}
       ${CMAKE_CURRENT_LIST_DIR}/libdll/arch/arm.c
       ${CMAKE_CURRENT_LIST_DIR}/libdll/arch.x86.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/libdll)

endif()

if(DEFINED RT_USING_DFS AND DEFINED RT_USING_POSIX_MMAP)

  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/mmap/posix_mmap.c)

endif()

if(DEFINED RT_USING_PTHREADS AND DEFINED RT_USING_LIBC)
  file(GLOB pthreads_SRCS ${CMAKE_CURRENT_LIST_DIR}/pthreads/*.c)

  list(APPEND libc_SRCS ${pthreads_SRCS})
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/pthreads)

endif()

if(DEFINED RT_USING_SIGNALS
   AND DEFINED RT_USING_PTHREADS
   AND DEFINED RT_USING_LIBC)

  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/signal/posix_signal.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/signal)

endif()

if(DEFINED RT_USING_POSIX_TERMIOS
   AND DEFINED RT_USING_POSIX
   AND DEFINED RT_USING_LIBC)

  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/termios/posix_termios.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/termios)

endif()

if(DEFINED RT_USING_PTHREADS)

  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/time/clock_time.c)
  list(APPEND libc_SRCS ${CMAKE_CURRENT_LIST_DIR}/time/posix_sleep.c)
  list(APPEND libc_INCS ${CMAKE_CURRENT_LIST_DIR}/time)

endif()

set(libc_SRCS
    ${libc_SRCS}
    CACHE INTERNAL "")
set(libc_INCS
    ${libc_INCS}
    CACHE INTERNAL "")
