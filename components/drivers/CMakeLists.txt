set(com_drivers_SRCS "")

set(com_drivers_INCS
    ${CMAKE_CURRENT_LIST_DIR}/include ${CMAKE_CURRENT_LIST_DIR}/include/drivers
    ${CMAKE_CURRENT_LIST_DIR}/include/ipc)

if(DEFINED RT_USING_AUDIO)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/audio/audio.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/audio/audio_pipe.c)
  list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/audio)
endif()

if(DEFINED RT_USING_CAN)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/can/can.c)
endif()

if(DEFINED RT_USING_CPUTIME)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/cputime/cputime.c)

  if(DEFINED RT_USING_CPUTIME_CORTEXM)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/cputime/cputime_cortexm.c)
  endif()

endif()

if(DEFINED RT_USING_RT_USING_HWCRYPTO)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/hwcrypto/hwcrypto.c)
  # TODO
endif()

if(DEFINED RT_USING_HWTIMER)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/hwtimer/hwtimer.c)
endif()

if(DEFINED RT_USING_I2C)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/i2c/i2c_core.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/i2c/i2c_dev.c)

  if(DEFINED RT_USING_I2C_BITOPS)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/i2c/i2c-bit-opt.c)
  endif()

endif()

if(DEFINED RT_USING_PIN)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/misc/pin.c)
endif()

if(DEFINED RT_USING_ADC)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/misc/adc.c)
endif()

if(DEFINED RT_USING_PWM)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/misc/rt_drv_pwm.c)
endif()

# if(DEFINED RT_USING_PLUSE_ENCODER)
#   list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/misc/pluse_encoder.c)

# endif()

# if(DEFINED RT_USING_INPUT_CAPTURE)
#   list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/misc/rt_inputcapture.c)
# endif()

if(DEFINED RT_USING_MTD_NOR)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/mtd/mtd_nor.c)
endif()

if(DEFINED RT_USING_MTD_NAND)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/mtd/mtd_nand.c)
endif()

if(DEFINED RT_USING_PM)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/pm/pm.c)
endif()

if(DEFINED RT_USING_RTC)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/rtc/rtc.c)

  if(DEFINED RT_USING_ALARM)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/rtc/alarm.c)
  endif()

  if(DEFINED RT_USING_SOFT_RTC)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/rtc/soft_rtc.c)
  endif()

endif()

if(DEFINED RT_USING_SDIO)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sdio/block_dev.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sdio/mmcsd_core.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sdio/sd.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sdio/sdio.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sdio/mmc.c)
endif()

if(DEFINED RT_USING_SENSOR)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sensor/sensor.c)
  if(DEFINED RT_USING_SENSOR_CMD)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/sensor/sensor_cmd.c)
  endif()
  list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/sensor)
endif()

if(DEFINED RT_USING_SERIAL)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/serial/serial.c)
endif()

if(DEFINED RT_USING_RTC)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/rtc/rtc.c)
endif()

if(DEFINED RT_USING_SPI)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/spi_core.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/spi_dev.c)

  if(DEFINED RT_USING_QSPI)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/pspi_core.c)
  endif()

  if(DEFINED RT_USING_SPI_WIFI)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi_wifi_rw009.c)
  endif()

  if(DEFINED RT_USING_ENC28J60)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/en28j60.c)
  endif()

  if(DEFINED RT_USING_SPI_MSD)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/spi_msd.c)
  endif()

  if(DEFINED RT_USING_SFUD)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/spi_flash_sfud.c)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/spi/sfud/src/sfud.c)
    list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/spi/sfud/inc)
    if(DEFINED RT_SFUD_USING_SFDP)
      list(APPEND com_drivers_SRCS
           ${CMAKE_CURRENT_LIST_DIR}/spi/sfud/src/sfud_sfdp.c)
    endif()
    # TODO swich gcc or keil
  endif()
endif()

if(DEFINED RT_USING_DEVICE_IPC)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/completion.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/ringblk_buf.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/ringbuffer.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/waitqueue.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/workqueue.c)
  if(DEFINED RT_USING_HEAP)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/dataqueue.c)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/src/pipe.c)
  endif()
endif()

if(DEFINED RT_USING_TOUCH)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/touch/touch.c)
  list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/touch)
endif()

# TODO usb device

if(DEFINED RT_USING_USB_HOST)

  list(APPEND com_drivers_SRCS
       ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/core/core.c)
  list(APPEND com_drivers_SRCS
       ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/core/driver.c)
  list(APPEND com_drivers_SRCS
       ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/core/usbhost.c)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/core/hub.c)
  list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/include)

  if(DEFINED RT_USBH_ADK)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/adk.c
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/adkapp.c)
  endif()

  if(DEFINED RT_USBH_MSTOREGE)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/mass.c
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/udisk.c)
  endif()
  
  if(DEFINED RT_USBH_HID)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/hid.c)
  endif()

  if(DEFINED RT_USBH_HID_MOUSE)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/umouse.c)
  endif()

  if(DEFINED RT_USBH_HID_KEYBOARD)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/usb/usbhost/class/ukbd.c)
  endif()

endif()

if(DEFINED RT_USING_WDT)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/watchdog/watchdog.c)
endif()

if(DEFINED RT_USING_WIFI)
  list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_dev.c)
  list(APPEND com_drivers_INCS ${CMAKE_CURRENT_LIST_DIR}/wifi)
  if(DEFINED RT_WLAN_MANAGE_ENABLE)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_mgnt.c)
  endif()

  if(DEFINED RT_WLAN_MSH_CMD_ENABLE)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_cmd.c)
  endif()

  if(DEFINED RT_WLAN_PROT_ENABLE)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_prot.c)
  endif()

  if(DEFINED RT_WLAN_PROT_LWIP_ENABLE)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_lwip.c)
  endif()

  if(DEFINED RT_WLAN_CFG_ENABLE)
    list(APPEND com_drivers_SRCS ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_cfg.c)
  endif()

  if(DEFINED RT_WLAN_WORK_THREAD_ENABLE)
    list(APPEND com_drivers_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/wifi/wlan_workqueue.c)
  endif()

endif()

set(com_drivers_SRCS
    ${com_drivers_SRCS}
    CACHE INTERNAL "")
set(com_drivers_INCS
    ${com_drivers_INCS}
    CACHE INTERNAL "")
