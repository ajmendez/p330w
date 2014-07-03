p330w
=====

ZyXel P330W wireless router debug




* Serial Connection: J4 contains a serial connection.
* # python -m serial.tools.miniterm  /dev/tty.usbserial-A100OZXL 38400
  * 3.3V
  * TX
  * RX
  * GND -- Closest to the RTL8186


Device Info
-----------

    # cd /proc
    # cat cpuinfo 
    system type             : Philips Nino
    processor               : 0
    cpu model               : R3000 V0.0
    BogoMIPS                : 178.99
    wait instruction        : no
    microsecond timers      : no
    tlb_entries             : 64
    extra interrupt vector  : no
    hardware watchpoint     : no
    VCED exceptions         : not available
    VCEI exceptions         : not available
    ll emulations           : 299
    sc emulations           : 299
    # 
    # cat meminfo 
            total:    used:    free:  shared: buffers:  cached:
    Mem:  14741504  8224768  6516736        0   643072  3244032
    Swap:        0        0        0
    MemTotal:        14396 kB
    MemFree:          6364 kB
    MemShared:           0 kB
    Buffers:           628 kB
    Cached:           3168 kB
    SwapCached:          0 kB
    Active:           1656 kB
    Inactive:         3396 kB
    HighTotal:           0 kB
    HighFree:            0 kB
    LowTotal:        14396 kB
    LowFree:          6364 kB
    SwapTotal:           0 kB
    SwapFree:            0 kB



Boot Up
--------

Output of the serial device on the  serial monitor.
Most of this data is also included on the web log page.

    UART1 output test ok
    Uart init
    mfid=000000c2 devid=00002249
    Found 1 x 2M flash memory
    
    ---RealTek(RTL8186)at 2005.09.14-18:49+0800 version 1.3b [32bit](180MHz)
    no sys signature at 00010000!
    Jump to image start=0x80300000...
    
    UART1 output test ok
    Uart init
    mfid=000000c2 devid=00002249
    Found 1 x 2M flash memory
    
    ---RealTek(RTL8186)at 2005.09.14-18:49+0800 version 1.3b [32bit](180MHz)
    no sys signature at 00010000!
    Jump to image start=0x80300000...
    display on
    entering boot loader, turning on display
    decompressing kernel:
    Uncompressing Linux... done, booting the kernel.
    done decompressing kernel.
    early printk enabled 
    Determined physical RAM map:
     memory: 01000000 @ 00000000 (usable)
    On node 0 totalpages: 4096
    zone(0): 4096 pages.
    zone(1): 0 pages.
    zone(2): 0 pages.
    Kernel command line: root=/dev/mtdblock1 console=0 single
    Calibrating delay loop... 178.99 BogoMIPS
    Memory: 14344k/16384k available (1491k kernel code, 2040k reserved, 92k data, 52k init, 0k highmem)
    Dentry-cache hash table entries: 2048 (order: 2, 16384 bytes)
    Inode-cache hash table entries: 1024 (order: 1, 8192 bytes)
    Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
    Buffer-cache hash table entries: 1024 (order: 0, 4096 bytes)
    Page-cache hash table entries: 4096 (order: 2, 16384 bytes)
    check_wait... unavailable.
    POSIX conformance testing by UNIFIX
    Linux NET4.0 for Linux 2.4
    Based upon Swansea University Computer Society NET3.039
    Initializing RT netlink socket
    Starting kswapd
    squashfs: version 3.1 (2006/08/19) Phillip Lougher
    Serial driver version 6.02 (2003-03-12) with no serial options enabled
    ttyS00 at 0x00c3 (irq = 3) is a rtl_uart1
    state->flags=00000000
    Realtek GPIO Driver for Flash Reload Default
    block: 64 slots per queue, batch=16
    SLIP: version 0.8.4-NET3.019-NEWTTY (dynamic channels, max=256).
    CSLIP: code copyright 1989 Regents of the University of California.
    PPP generic driver version 2.4.1
    MPPE/MPPC encryption/compression module registered
    RealTek E-Flash System Driver. (C) 2002 RealTek Corp.
    Found 1 x 2M Byte MXIC MX29LV160CB at 0xbe000000
    Creating 2 MTD partitions on "DiskOnChip Millennium":
    0x00000000-0x00100000 : "boot+cfg+linux"
    0x00100000-0x00200000 : "root fs"
    RTL8185 driver version 1.14 (2007-04-03)
    8186NIC Ethernet driver v0.0.8-abc (July 30, 2007)
    eth0: RTL8186-NIC at 0xbd200000, 00:01:02:03:04:05, IRQ 4
    eth1: RTL8186-NIC at 0xbd300000, 04:05:06:07:08:09, IRQ 5
    fast_nat v1.3i-abc
    NET4: Linux TCP/IP 1.0 for NET4.0
    IP Protocols: ICMP, UDP, TCP, IGMP
    IP: routing cache hash table of 512 buckets, 4Kbytes
    TCP: Hash tables configured (established 1024 bind 2048)
    Linux IP multicast router 0.06 plus PIM-SM
    ip_conntrack version 2.1 (128 buckets, 1024 max) - 312 bytes per conntrack
    ip_nat_h323: cannot initialize the module!
    ip_nat_ftp: error registering helper for port 21
    ip_tables: (C) 2000-2002 Netfilter core team
    NET4: Unix domain sockets 1.0/SMP for Linux NET4.0.
    NET4: Ethernet Bridge 008 for NET4.0
    VFS: Mounted root (squashfs filesystem) readonly.
    Freeing unused kernel memory: 52k freed
    mount /proc file system ok!
    mount /var  file system ok!
    serial console detected.  Disabling virtual terminals.
    init started:  BusyBox v1.00-pre8 (2008.07.18-08:18+0000) multi-call binary
    
    
    BusyBox v1.00-pre8 (2008.07.18-08:18+0000) Built-in shell (msh)
    Enter 'help' for a list of built-in commands.
    
    38
     
    
    39
    mac_bit = 69
    Arthur Chow : (init.sh) echo 0 > /var/WanIpReady
    Initialize wlan0 interface
    setup for WiFi test...
    wifi_specific=0
    Setup LNA ...
    disable LNA
    Setup NDS ...
    ENABLE basic
    Setup BRIDGE interface
    SIOCGIFFLAGS: No such device
    bridge br0 doesn't exist; can't delete it
    Setup bridge...
    device eth0 entered promiscuous mode
    eth0:phy is 8305
    SIOCDELRT: No such process
    device eth1 entered promiscuous mode
    eth1:phy is 8305
    SIOCDELRT: No such process
    Update DDNS Info...
    br0: port 2(eth1) entering listening state
    br0: port 1(eth0) entering listening state
    br0: port 2(eth1) entering learning state
    br0: port 2(eth1) entering forwarding state
    br0: topology change detected, propagating
    br0: port 1(eth0) entering learning state
    br0: port 1(eth0) entering forwarding state
    br0: topology change detected, propagating
    SIOCDELRT: No such process
    SIOCDELRT: No such process
    WAN up as 0x3100
    Setup WAN interface
    start DNS Relay Daemon
    DNS OK
    WAN up as 0x3100
    Check Alive !!
    udhcp client (v0.9.9-pre) started
    The state is 0 
    SIOCDELRT: No such process
    miniigd (v1.00)
    SIOCDELRT: No such process
    udhcp server (v0.9.9-pre) started
    >>>>>>>>>After firewall : [wlanapp.sh start  wlan0 br0]
    killall: ntp.sh: no process killed
    SERVER_INDEX is 1
    cat: /tmp/index_bit: No such file or directory
    Start NTP_ZYXEL daemon
    Auto-Discovery (ver 1.01) 
    autoconf: not found
    1155
    1156
    # auth uses obsolete (PF_INET,SOCK_PACKET)
    IEEE 802.1x (WPA) daemon, version 1.7f
