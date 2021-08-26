set(net_SRCS "")
set(net_INCS "")

set(lwipcore_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/init.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/def.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/dns.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/inet_chksum.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ip.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/memp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/netif.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/pbuf.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/raw.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/stats.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/sys.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/tcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/tcp_in.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/tcp_out.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/timeouts.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/udp.c)

set(lwipcore_altcp_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/altcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/altcp_alloc.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/altcp_tcp.c)

set(lwipcore4_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/autoip.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/dhcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/etharp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/icmp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/igmp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/ip4_frag.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/ip4.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv4/ip4_addr.c)

set(lwipcore6_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/dhcp6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/ethip6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/icmp6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/inet6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/ip6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/ip6_addr.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/ip6_frag.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/mld6.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/core/ipv6/nd6.c)

# 1. APIFILES: The files which implement the sequential and socket APIs.
set(lwipapi_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/api_lib.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/api_msg.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/err.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/if_api.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/netbuf.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/netdb.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/netifapi.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/sockets.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/api/tcpip.c)

# 1. Files implementing various generic network interface functions
set(lwipnetif_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ethernet.c
                   ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ethernetif.c)

# 3.1 Files implementing an IEEE 802.1D bridge by using a multilayer netif
# approach
set(lwipnetif_bridgeif_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/bridgeif.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/bridgeif_fdb.c)

# 3.2 A generic implementation of the SLIP (Serial Line IP) protocol.
set(lwipnetif_slipif_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/slipif.c)

# 1. 6LoWPAN
set(lwipsixlowpan_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/lowpan6.c)

# 4.1 A 6LoWPAN over Bluetooth Low Energy (BLE) implementation as netif,
# according to RFC-7668.
set(lwipsixlowpan_ble_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/lowpan6_ble.c)

# 4.2 Common 6LowPAN routines for IPv6.
set(lwipsixlowpan_ipv6_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/lowpan6_common.c)

# 4.3 A netif implementing the ZigBee Encapsulation Protocol (ZEP).
set(lwipsixlowpan_zep_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/zepif.c)

# 1. PPP
set(lwipppp_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/auth.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/ccp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/chap-md5.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/chap_ms.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/chap-new.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/demand.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/eap.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/ecp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/eui64.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/fsm.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/ipcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/ipv6cp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/lcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/magic.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/mppe.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/multilink.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/ppp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/pppapi.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/pppcrypt.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/pppoe.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/pppol2tp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/pppos.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/upap.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/utils.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/vj.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/polarssl/arc4.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/polarssl/des.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/polarssl/md4.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/polarssl/md5.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp/polarssl/sha1.c)

# 1. SNMPv3 agent
set(lwipsnmp_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_asn1.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_core.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_icmp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_interfaces.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_ip.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_snmp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_system.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_tcp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_mib2_udp.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_snmpv2_framework.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_snmpv2_usm.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_msg.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmpv3.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_netconn.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_pbuf_stream.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_raw.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_scalar.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_table.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_threadsync.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmp_traps.c)

# 1. HTTP server + client
set(lwiphttp_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/http/altcp_proxyconnect.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/http/fs.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/http/http_client.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/http/httpd.c)

# 1. MAKEFSDATA HTTP server host utility
set(lwipmakefsdata_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/http/makefsdata/makefsdata.c)

# 1. IPERF server
set(lwipiperf_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/lwiperf/lwiperf.c)

# 1. SMTP client
set(lwipsmtp_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/smtp/smtp.c)

# 1. SNTP client
set(lwipsntp_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/sntp/sntp.c)

# 1. MDNS responder
set(lwipmdns_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/mdns/mdns.c)

# 1. NetBIOS name server
set(lwipnetbios_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/netbiosns/netbiosns.c)

# 1. TFTP server files
set(lwiptftp_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/tftp/tftp_server.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/tftp/tftp_port.c)

# 1. MQTT client files
set(lwipmqtt_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/mqtt/mqtt.c)

# 1. ARM MBEDTLS related files of lwIP rep
set(lwipmbedtls_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/altcp_tls/altcp_tls_mbedtls.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/altcp_tls/altcp_tls_mbedtls_mem.c
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp/snmpv3_mbedtls.c)

# 1. ping
set(lwipping_SRCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/ping/ping.c)

set(lwip_SRCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/arch/sys_arch.c
    ${lwipcore_SRCS}
    ${lwipcore_altcp_SRCS}
    ${lwipapi_SRCS}
    ${lwipnetif_SRCS}
    ${lwipsixlowpan_SRCS}
    ${lwipcore4_SRCS}
    # CACHE INTERNAL ""
)

# rm mem.c

set(lwip_INCS
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/include
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/arch/include
    ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/include/netif
    # CACHE INTERNAL ""
)

if(NOT DEFINED RT_USING_SAL)
  # message("RT_USING_SAL")
  list(APPEND lwip_INCS
       ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/include/posix)
  # message("${HAL_SRCS}")
endif()
if(DEFINED RT_LWIP_SNMP)
  # message("RT_LWIP_SNMP")
  list(APPEND lwip_SRCS ${lwipsnmp_SRCS})
  list(APPEND lwip_INCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/apps/snmp)
endif()
if(DEFINED RT_LWIP_PPP)
  # message("RT_LWIP_PPP")
  list(APPEND lwip_SRCS ${lwipppp_SRCS})
  list(APPEND lwip_INCS ${CMAKE_CURRENT_LIST_DIR}/lwip-2.0.2/src/netif/ppp)
endif()
if(DEFINED RT_USING_LWIP_IPV6)
  # message("RT_USING_LWIP_IPV6")
  list(APPEND lwip_SRCS ${lwipcore6_SRCS})

endif()
if(DEFINED RT_LWIP_USING_PING)
  # message("RT_LWIP_USING_PING")
  list(APPEND lwip_SRCS ${lwipping_SRCS})

endif()

if(DEFINED RT_USING_LWIP OR DEFINED RT_USING_LWIP202)
  list(APPEND net_SRCS ${lwip_SRCS})
  list(APPEND net_INCS ${lwip_INCS})
endif()

if(DEFINED RT_USING_NETDEV) # TODO gcc
  file(GLOB netdev_SRCS ${CMAKE_CURRENT_LIST_DIR}/netdev/src/*.c)

  list(APPEND net_SRCS ${netdev_SRCS})
  list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/netdev/include)
  list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/netdev/include/arpa)

endif()

if(DEFINED RT_USING_SAL)

  list(APPEND net_SRCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/src/sal_socket.c)
  list(APPEND net_SRCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/socket/net_netdb.c)
  list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/include)
  list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/include/socket)
  if(DEFINED SAL_USING_LWIP)
    list(APPEND net_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/sal_socket/impl/af_inet_lwip.c)
  endif()

  if(DEFINED SAL_USING_AT)
    list(APPEND net_SRCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/impl/af_inet_at.c)

  endif()

  if(DEFINED SAL_USING_LWIP OR DEFINED SAL_USING_AT)
    list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/impl)

  endif()

  if(DEFINED SAL_USING_TLS)
    list(APPEND net_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/sal_socket/impl/proto_mbedtls.c)

  endif()

  if(DEFINED SAL_USING_POSIX)
    list(APPEND net_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/sal_socket/socket/net_sockets.c)    
    list(APPEND net_SRCS
         ${CMAKE_CURRENT_LIST_DIR}/sal_socket/dfs_net/dfs_net.c)

    list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/include/dfs_net)
    
    if(NOT DEFINED HAVE_SYS_SELECT_H)
      list(APPEND net_INCS
           ${CMAKE_CURRENT_LIST_DIR}/sal_socket/include/dfs_net/sys_select)
    endif()

  endif()

  if(DEFINED HAVE_SYS_SELECT_H)
    list(APPEND net_INCS ${CMAKE_CURRENT_LIST_DIR}/sal_socket/include/socket/sys_socket)
    # message(STATUS "net incs ${net_INCS}")
  endif()

endif()


set(net_SRCS
    ${net_SRCS}
    CACHE INTERNAL "")
set(net_INCS
    ${net_INCS}
    CACHE INTERNAL "")

# message(STATUS "net incs ${net_INCS}")    
# message(STATUS "net srcs ${net_SRCS}")    

