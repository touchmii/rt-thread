add_subdirectory(components)
set(rt_DIR ${CMAKE_CURRENT_LIST_DIR})
set(rt-thread_SRCS
    ${rt_DIR}/src/clock.c
    ${rt_DIR}/src/cpu.c
    ${rt_DIR}/src/idle.c
    ${rt_DIR}/src/ipc.c
    ${rt_DIR}/src/irq.c
    ${rt_DIR}/src/kservice.c
    ${rt_DIR}/src/object.c
    ${rt_DIR}/src/scheduler.c
    ${rt_DIR}/src/signal.c
    ${rt_DIR}/src/thread.c
    ${rt_DIR}/src/timer.c 
)

if (DEFINED RT_USING_COMPONENTS_INIT)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/components.c)
endif()
if (DEFINED RT_USING_MODULE)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/module.c)
endif()
if (DEFINED RT_USING_HEAP OR DEFINED RT_USING_SMALL_MEM)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/mem.c)
endif()
if (DEFINED RT_USING_HEAP OR DEFINED RT_USING_SLAB)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/slab.c)
endif()
if (DEFINED RT_USING_MEMPOOL)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/mempool.c)
endif()
if (DEFINED RT_USING_MEMHEAP)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/memheap.c)
    if (NOT DEFINED RT_USING_MEMHEAP_AS_HEAP)
      list(APPEND rt-thread_SRCS ${rt_DIR}/src/mem.c)
    endif()
endif()    
if (DEFINED RT_USING_DEVICE)
  list(APPEND rt-thread_SRCS ${rt_DIR}/src/device.c)
endif()

set(cortex-m4_SRCS ${rt_DIR}/libcpu/arm/cortex-m4/cpuport.c)
set(cortex-m4_ASM ${rt_DIR}/libcpu/arm/cortex-m4/context_gcc.S)

list(APPEND rt-thread_SRCS ${cortex-m4_SRCS} ${cortex-m4_ASM}
     # ${finsh_SRCS} ${libc_SRCS}
     ${components_SRCS})

set(rt-thread_INCS ${rt_DIR}/include ${rt_DIR}/include/libc
                   # CACHE INTERNAL ""
)
list(APPEND rt-thread_INCS ${components_INCS})
set(rt-thread_SRCS
    ${rt-thread_SRCS}
    CACHE INTERNAL "")
set(rt-thread_INCS
    ${rt-thread_INCS}
    CACHE INTERNAL "")
# message("rt-thread src ${rt-thread_SRCS}")
# message("rt-thread inc ${rt-thread_INCS}")
# message("rt-thread components inc ${components_INCS}") message("lwip src
# ${lwip_SRCS}") message("lwip inc ${lwip_INCS}")
