This is a multi-threaded multi-pool FPGA and ASIC miner for bitcoin fully updated and fixed for Windows 10.

This code is provided entirely free. Building for windows: native WIN32/64 build instructions: see Readme.txt

NOTE: This code is licensed under the GPLv3. This means that the source to any
modifications you make to this code MUST be provided by law if you distribute
modified binaries.

EXECUTIVE SUMMARY ON USAGE:

Single pool:

cgminer -o http://pool:port -u username -p password

Multiple pools:

cgminer -o http://pool1:port -u pool1username -p pool1password -o http://pool2:port -u pool2usernmae -p pool2password

Single pool with a standard http proxy:

cgminer -o "http:proxy:port|http://pool:port" -u username -p password

Single pool with a socks5 proxy:

cgminer -o "socks5:proxy:port|http://pool:port" -u username -p password

Single pool with stratum protocol support:

cgminer -o stratum+tcp://pool:port -u username -p password

Solo mining to local bitcoind:

cgminer -o http://localhost:8332 -u username -p password --btc-address 15qSxP1SQcUX3o4nhkfdbgyoWEFMomJ4rZ

The list of proxy types are:
 http:    standard http 1.1 proxy
 http0:   http 1.0 proxy
 socks4:  socks4 proxy
 socks5:  socks5 proxy
 socks4a: socks4a proxy
 socks5h: socks5 proxy using a hostname

If you compile cgminer with a version of CURL before 7.19.4 then some of the above will
not be available. All are available since CURL version 7.19.4

If you specify the --socks-proxy option to cgminer, it will only be applied to all pools
that don't specify their own proxy setting like above


After saving configuration from the menu, you do not need to give cgminer any
arguments and it will load your configuration.

Any configuration file may also contain a single
	"include" : "filename"
to recursively include another configuration file.
Writing the configuration will save all settings from all files in the output.

It is actually easiest to build a windows binary using cross compilation tools
provided by "mxe" available at http://mxe.cc/ (use the 32 bit one!)
Once you have followed the instructions for building mxe:
	export PATH=(path/to/mxe)/usr/bin/:$PATH
	CFLAGS="-O2 -Wall -W -march=i686" ./configure --host=i686-pc-mingw32 <options>
	make
---
Usage instructions:  Run "cgminer --help" to see options:

Usage: cgminer [-DdElmpPQqUsTouOchnV]

Options for both config file and command line:
--anu-freq <arg>    Set AntminerU1/2 frequency in MHz, range 125-500 (default: 250.0)
--api-allow <arg>   Allow API access only to the given list of [G:]IP[/Prefix] addresses[/subnets]
--api-description <arg> Description placed in the API status header, default: cgminer version
--api-groups <arg>  API one letter groups G:cmd:cmd[,P:cmd:*...] defining the cmds a groups can use
--api-listen        Enable API, default: disabled
--api-mcast         Enable API Multicast listener, default: disabled
--api-mcast-addr <arg> API Multicast listen address
--api-mcast-code <arg> Code expected in the API Multicast message, don't use '-'
--api-mcast-des <arg> Description appended to the API Multicast reply, default: ''
--api-mcast-port <arg> API Multicast listen port (default: 4028)
--api-network       Allow API (if enabled) to listen on/for any address, default: only 127.0.0.1
--api-port <arg>    Port number of miner API (default: 4028)
--au3-freq <arg>    Set AntminerU3 frequency in MHz, range 100-250 (default: 225.0)
--au3-volt <arg>    Set AntminerU3 voltage in mv, range 725-850, 0 to not set (default: 775)
--avalon-auto       Adjust avalon overclock frequency dynamically for best hashrate
--avalon-cutoff <arg> Set avalon overheat cut off temperature (default: 60)
--avalon-fan <arg>  Set fanspeed percentage for avalon, single value or range (default: 20-100)
--avalon-freq <arg> Set frequency range for avalon-auto, single value or range
--avalon-options <arg> Set avalon options baud:miners:asic:timeout:freq:tech
--avalon-temp <arg> Set avalon target temperature (default: 50)
--avalon2-freq      Set frequency range for Avalon2, single value or range
--avalon2-voltage   Set Avalon2 core voltage, in millivolts
--avalon2-fan       Set Avalon2 target fan speed
--avalon2-cutoff <arg> Set Avalon2 overheat cut off temperature (default: 88)
--avalon2-fixed-speed Set Avalon2 fan to fixed speed
--avalon4-automatic-voltage Automatic adjust voltage base on module DH
--avalon4-voltage   Set Avalon4 core voltage, in millivolts, step: 125
--avalon4-freq      Set frequency for Avalon4, 1 to 3 values, example: 445:385:370
--avalon4-fan       Set Avalon4 target fan speed range
--avalon4-temp <arg> Set Avalon4 target temperature (default: 42)
--avalon4-cutoff <arg> Set Avalon4 overheat cut off temperature (default: 65)
--avalon4-polling-delay <arg> Set Avalon4 polling delay value (ms) (default: 20)
--avalon4-ntime-offset <arg> Set Avalon4 MM ntime rolling max offset (default: 4)
--avalon4-aucspeed <arg> Set Avalon4 AUC IIC bus speed (default: 400000)
--avalon4-aucxdelay <arg> Set Avalon4 AUC IIC xfer read delay, 4800 ~= 1ms (default: 9600)
--avalon4-miningmode <arg> Set Avalon4 mining mode(0:custom, 1:eco, 2:normal, 3:turbo (default: 0)
--avalon4-freezesafe Make Avalon4 running as a radiator when stratum server failed
--avalon4-ntcb <arg> Set Avalon4 MM NTC B value (default: 3450)
--avalon4-freq-min <arg> Set minimum frequency for Avalon4 (default: 100)
--avalon4-freq-max <arg> Set maximum frequency for Avalon4 (default: 1000)
--avalon4-noncecheck-off Disable A3218 inside nonce check function
--avalon4-smart-speed <arg> Set smart speed, range 0-3. 0 means Disable (default: 2)
--avalon4-speed-bingo <arg> Set A3218 speed bingo for smart speed mode 1 (default: 255)
--avalon4-speed-error <arg> Set A3218 speed error for smart speed mode 1 (default: 3)
--avalon4-least-pll <arg> Set least pll check threshold for smart speed mode 2 (default: 768)
--avalon4-most-pll <arg> Set most pll check threshold for smart speed mode 2 (default: 256)
--avalon7-voltage   Set Avalon7 default core voltage, in millivolts, step: 78
--avalon7-voltage-level Set Avalon7 default level of core voltage, range:[0, 15], step: 1
--avalon7-voltage-offset Set Avalon7 default offset of core voltage, range:[-2, 1], step: 1
--avalon7-freq      Set Avalon7 default frequency, range:[24, 1404], step: 12, example: 500
--avalon7-freq-sel <arg> Set Avalon7 default frequency select, range:[0, 5], step: 1, example: 3 (default: 0)
--avalon7-fan       Set Avalon7 target fan speed, range:[0, 100], step: 1, example: 0-100
--avalon7-temp <arg> Set Avalon7 target temperature, range:[0, 100] (default: 99)
--avalon7-polling-delay <arg> Set Avalon7 polling delay value (ms) (default: 20)
--avalon7-aucspeed <arg> Set AUC3 IIC bus speed (default: 400000)
--avalon7-aucxdelay <arg> Set AUC3 IIC xfer read delay, 4800 ~= 1ms (default: 19200)
--avalon7-smart-speed <arg> Set Avalon7 smart speed, range 0-1. 0 means Disable (default: 1)
--avalon7-th-pass <arg> Set A3212 th pass value (default: 162)
--avalon7-th-fail <arg> Set A3212 th fail value (default: 10921)
--avalon7-th-init <arg> Set A3212 th init value (default: 32767)
--avalon7-th-ms <arg> Set A3212 th ms value (default: 1)
--avalon7-th-timeout <arg> Set A3212 th timeout value (default: 0)
--avalon7-iic-detect Enable Avalon7 detect through iic controller
--avalon7-freqadj-time <arg> Set Avalon7 check interval when run in AVA7_FREQ_TEMPADJ_MODE (default: 60)
--avalon7-delta-temp <arg> Set Avalon7 delta temperature when reset freq in AVA7_FREQ_TEMPADJ_MODE (default: 0)
--avalon7-delta-freq <arg> Set Avalon7 delta freq when adjust freq in AVA7_FREQ_TEMPADJ_MODE (default: 100)
--avalon7-freqadj-temp <arg> Set Avalon7 check temperature when run into AVA7_FREQ_TEMPADJ_MODE (default: 104)
--avalon7-nonce-mask <arg> Set A3212 nonce mask, range 24-32. (default: 31)
--no-avalon7-asic-debug Disable A3212 debug.
--avalon8-voltage-level Set Avalon8 default level of core voltage, range:[0, 15], step: 1
--avalon8-voltage-level-offset Set Avalon8 default offset of core voltage level, range:[-2, 1], step: 1
--avalon8-freq      Set Avalon8 default frequency, range:[25, 1200], step: 25, example: 800
--avalon8-freq-sel <arg> Set Avalon8 default frequency select, range:[0, 3], step: 1, example: 3 (default: 3)
--avalon8-fan       Set Avalon8 target fan speed, range:[0, 100], step: 1, example: 0-100
--avalon8-temp <arg> Set Avalon8 target temperature, range:[0, 100] (default: 90)
--avalon8-polling-delay <arg> Set Avalon8 polling delay value (ms) (default: 20)
--avalon8-aucspeed <arg> Set AUC3 IIC bus speed (default: 400000)
--avalon8-aucxdelay <arg> Set AUC3 IIC xfer read delay, 4800 ~= 1ms (default: 19200)
--avalon8-smart-speed <arg> Set Avalon8 smart speed, range 0-1. 0 means Disable (default: 1)
--avalon8-th-pass <arg> Set A3210 th pass value (default: -1)
--avalon8-th-fail <arg> Set A3210 th fail value (default: -1)
--avalon8-th-init <arg> Set A3210 th init value (default: 32767)
--avalon8-th-ms <arg> Set A3210 th ms value (default: 5)
--avalon8-th-timeout <arg> Set A3210 th timeout value (default: 4294967295)
--avalon8-th-add <arg> Set A3210 th add value (default: 1)
--avalon8-iic-detect Enable Avalon8 detect through iic controller
--avalon8-nonce-mask <arg> Set A3210 nonce mask, range 24-32. (default: -1)
--avalon8-nonce-check <arg> Set A3210 nonce check, range 0-1. (default: 1)
--avalon8-roll-enable <arg> Set A3210 roll enable, range 0-1. (default: 1)
--avalon8-mux-l2h <arg> Set Avalon8 mux l2h, range 0-2. (default: 0)
--avalon8-mux-h2l <arg> Set Avalon8 mux h2l, range 0-1. (default: 1)
--avalon8-h2ltime0-spd <arg> Set Avalon8 h2ltime0 spd, range 0-255. (default: 3)
--avalon8-spdlow <arg> Set Avalon8 spdlow, range 0-3. (default: -1)
--avalon8-spdhigh <arg> Set Avalon8 spdhigh, range 0-3. (default: 3)
--avalon8-cinfo-asic Set Avalon8 cinfo asic index, range:[0, 25], step: 1
--avalon8-pid-p <arg> Set Avalon8 pid-p, range 0-9999. (default: 2)
--avalon8-pid-i <arg> Set Avalon8 pid-i, range 0-9999. (default: 5)
--avalon8-pid-d <arg> Set Avalon8 pid-d, range 0-9999. (default: 0)
--bab-options <arg> Set BaB options max:def:min down:hz:delay:trf
--balance           Change multipool strategy from failover to even share balance
--benchfile <arg>   Run cgminer in benchmark mode using a work file - produces no shares
--benchfile-display Display each benchfile nonce found
--benchmark         Run cgminer in benchmark mode - produces no shares
--bet-clk <arg>     Set clockspeed of ASICMINER Tube/Prisma to (arg+1)*10MHz (default: 23)
--bfl-range         Use nonce range on bitforce devices if supported
--bflsc-overheat <arg> Set overheat temperature where BFLSC devices throttle, 0 to disable (default: 85)
--bitburner-fury-voltage <arg> Set BitBurner Fury core voltage, in millivolts
--bitburner-fury-options <arg> Override avalon-options for BitBurner Fury boards baud:miners:asic:timeout:freq
--bitburner-voltage <arg> Set BitBurner (Avalon) core voltage, in millivolts
--bitmain-auto      Adjust bitmain overclock frequency dynamically for best hashrate
--bitmain-cutoff <arg> Set bitmain overheat cut off temperature
--bitmain-fan <arg> Set fanspeed percentage for bitmain, single value or range (default: 20-100)
--bitmain-freq <arg> Set bitmain freq options timeout:freq:regdata
--bitmain-hwerror   Set bitmain device detect hardware error
--bitmain-options <arg> Set bitmain options baud:miners:asic:timeout:freq:regdata
--bitmain-temp <arg> Set bitmain target temperature
--bitmain-workdelay <arg> Set bitmain work delay (ms) 0-100
--bitmain-voltage <arg> Set bitmain voltage - S2/S3 only
--bitmain-dev <arg> Set bitmain device - S2 only
--bitmainbeeper     Set bitmain beeper ringing
--bitmaintempoverctrl Set bitmain stop runing when temprerature is over 80 degree Celsius
--bxf-bits <arg>    Set max BXF/HXF bits for overclocking (default: 54)
--bxf-temp-target <arg> Set target temperature for BXF/HXF devices (default: 82)
--bxm-bits <arg>    Set BXM bits for overclocking (default: 54)
--btc-address <arg> Set bitcoin target address when solo mining to bitcoind
--btc-sig <arg>     Set signature to add to coinbase when solo mining (optional)
--compac-freq <arg> Set GekkoScience Compac frequency in MHz, range 100-500 (default: 150.0)
--compact           Use compact display without per device statistics
--debug|-D          Enable debug output
--decode            Decode 2nd pool stratum coinbase transactions (1st must be bitcoind) and exit
--disable-rejecting Automatically disable pools that continually reject shares
--dragonmint-t1-options <arg> Dragonmint T1 options ref_clk_khz:sys_clk_khz:spi_clk_khz:override_chip_num
--T1efficient       Tune Dragonmint T1 per chain voltage and frequency for optimal efficiency
--T1noauto          Disable Dragonmint T1 per chain auto voltage and frequency tuning
--T1performance     Tune Dragonmint T1 per chain voltage and frequency for maximum performance
--T1fantarget <arg> Throttle T1 frequency to keep fan less than target fan speed (default: 100)
--T1Pll1 <arg>      Set PLL Clock 1 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll2 <arg>      Set PLL Clock 2 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll3 <arg>      Set PLL Clock 3 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll4 <arg>      Set PLL Clock 4 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll5 <arg>      Set PLL Clock 5 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll6 <arg>      Set PLL Clock 6 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll7 <arg>      Set PLL Clock 7 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Pll8 <arg>      Set PLL Clock 8 in Dragonmint T1 broad 1 chip (-1: 1000MHz, >0:Lookup PLL table) (default: 1332)
--T1Volt1 <arg>     Dragonmint T1 set voltage 1 - VID overrides if set (390-425) (default: 404)
--T1Volt2 <arg>     Dragonmint T1 set voltage 2 - VID overrides if set (390-425) (default: 404)
--T1Volt3 <arg>     Dragonmint T1 set voltage 3 - VID overrides if set (390-425) (default: 404)
--T1Volt4 <arg>     Dragonmint T1 set voltage 4 - VID overrides if set (390-425) (default: 404)
--T1Volt5 <arg>     Dragonmint T1 set voltage 5 - VID overrides if set (390-425) (default: 404)
--T1Volt6 <arg>     Dragonmint T1 set voltage 6 - VID overrides if set (390-425) (default: 404)
--T1Volt7 <arg>     Dragonmint T1 set voltage 7 - VID overrides if set (390-425) (default: 404)
--T1Volt8 <arg>     Dragonmint T1 set voltage 8 - VID overrides if set (390-425) (default: 404)
--T1VID1 <arg>      Dragonmint T1 set VID 1 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID2 <arg>      Dragonmint T1 set VID 2 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID3 <arg>      Dragonmint T1 set VID 3 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID4 <arg>      Dragonmint T1 set VID 4 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID5 <arg>      Dragonmint T1 set VID 5 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID6 <arg>      Dragonmint T1 set VID 6 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID7 <arg>      Dragonmint T1 set VID 7 in noauto - Overrides voltage if set (1-31) (default: 0)
--T1VID8 <arg>      Dragonmint T1 set VID 8 in noauto - Overrides voltage if set (1-31) (default: 0)
--drillbit-options <arg> Set drillbit options <int|ext>:clock[:clock_divider][:voltage]
--expiry|-E <arg>   Upper bound on how many seconds after getting work we consider a share from it stale (default: 120)
--failover-only     Don't leak work to backup pools when primary pool is lagging
--fix-protocol      Do not redirect to stratum protocol from GBT
--hfa-hash-clock <arg> Set hashfast clock speed (default: 550)
--hfa-fail-drop <arg> Set how many MHz to drop clockspeed each failure on an overlocked hashfast device (default: 10)
--hfa-fan <arg>     Set fanspeed percentage for hashfast, single value or range (default: 10-85)
--hfa-name <arg>    Set a unique name for a single hashfast device specified with --usb or the first device found
--hfa-noshed        Disable hashfast dynamic core disabling feature
--hfa-options <arg> Set hashfast options name:clock (comma separated)
--hfa-temp-overheat <arg> Set the hashfast overheat throttling temperature (default: 95)
--hfa-temp-target <arg> Set the hashfast target temperature (0 to disable) (default: 88)
--hro-freq          Set the hashratio clock frequency (default: 280)
--hotplug <arg>     Seconds between hotplug checks (0 means never check)
--klondike-options <arg> Set klondike options clock:temptarget
--load-balance      Change multipool strategy from failover to quota based balance
--log|-l <arg>      Interval in seconds between log output (default: 5)
--lowmem            Minimise caching of shares for low memory applications
--minion-chipreport <arg> Seconds to report chip 5min hashrate, range 0-100 (default: 0=disabled)
--minion-freq <arg> Set minion chip frequencies in MHz, single value or comma list, range 100-1400 (default: 1200)
--minion-freqchange Millisecond total time to do frequency changes (default: 1000)
--minion-freqpercent Percentage to use when starting up a chip (default: 70%)
--minion-idlecount  Report when IdleCount is >0 or changes
--minion-ledcount   Turn off led when more than this many chips below the ledlimit (default: 0)
--minion-ledlimit   Turn off led when chips GHs are below this (default: 90)
--minion-noautofreq Disable automatic frequency adjustment
--minion-overheat   Enable directly halting any chip when the status exceeds 100C
--minion-spidelay   Add a delay in microseconds after each SPI I/O
--minion-spireset   SPI regular reset: iNNN for I/O count or sNNN for seconds - 0 means none
--minion-spisleep   Sleep time in milliseconds when doing an SPI reset
--minion-temp <arg> Set minion chip temperature threshold, single value or comma list, range 120-160 (default: 135C)
--monitor|-m <arg>  Use custom pipe cmd for output messages
--nfu-bits <arg>    Set nanofury bits for overclocking, range 32-63 (default: 50)
--net-delay         Impose small delays in networking to not overload slow routers
--no-submit-stale   Don't submit shares if they are detected as stale
--osm-led-mode <arg> Set LED mode for OneStringMiner devices (default: 4)
--pass|-p <arg>     Password for bitcoin JSON-RPC server
--per-device-stats  Force verbose mode and output per-device statistics
--protocol-dump|-P  Verbose dump of protocol-level activities
--queue|-Q <arg>    Minimum number of work items to have queued (0+) (default: 1)
--quiet|-q          Disable logging output, display status and errors
--quota|-U <arg>    quota;URL combination for server with load-balance strategy quotas
--real-quiet        Disable all output
--rock-freq <arg>   Set RockMiner frequency in MHz, range 200-400 (default: 270)
--rotate <arg>      Change multipool strategy from failover to regularly rotate at N minutes (default: 0)
--round-robin       Change multipool strategy from failover to round robin on failure
--scan-time|-s <arg> Upper bound on time spent scanning current work, in seconds (default: -1)
--sched-start <arg> Set a time of day in HH:MM to start mining (a once off without a stop time)
--sched-stop <arg>  Set a time of day in HH:MM to stop mining (will quit without a start time)
--sharelog <arg>    Append share log to file
--shares <arg>      Quit after mining N shares (default: unlimited)
--socks-proxy <arg> Set socks4 proxy (host:port)
--suggest-diff <arg> Suggest miner difficulty for pool to user (default: none)
--syslog            Use system log for output messages (default: standard error)
--temp-cutoff <arg> Temperature where a device will be automatically disabled, one value or comma separated list (default: 95)
--text-only|-T      Disable ncurses formatted screen output
--url|-o <arg>      URL for bitcoin JSON-RPC server
--usb <arg>         USB device selection
--user|-u <arg>     Username for bitcoin JSON-RPC server
--userpass|-O <arg> Username:Password pair for bitcoin JSON-RPC server
--verbose           Log verbose output to stderr as well as status output
--widescreen        Use extra wide display without toggling
--worktime          Display extra work time debug information
Options for command line only:
--config|-c <arg>   Load a JSON-format configuration file
See example.conf for an example configuration.
--default-config <arg> Specify the filename of the default config file
Loaded at start and used when saving without a name.
--help|-h           Print this message
--ndevs|-n          Display all USB devices and exit
--version|-V        Display version and exit


Silent USB device (ASIC and FPGA) options:

--icarus-options <arg> Set specific FPGA board configurations - one set of values for all or comma separated
--icarus-timing <arg> Set how the Icarus timing is calculated - one setting/value for all or comma separated
--usb-dump          (See FPGA-README)

See FGPA-README or ASIC-README for more information regarding these.

SETTING UP USB DEVICES

WINDOWS:

On windows, the direct USB support requires the installation of a WinUSB
driver (NOT the ftdi_sio driver), and attach it to the chosen USB device.
When configuring your device, plug it in and wait for windows to attempt to
install a driver on its own. It may think it has succeeded or failed but wait
for it to finish regardless. This is NOT the driver you want installed. At this
point you need to associate your device with the WinUSB driver. The easiest
way to do this is to use the zadig utility which you must right click on and
run as administrator. Then once you plug in your device you can choose the
"list all devices" from the "option" menu and you should be able to see the
device as something like: "BitFORCE SHA256 SC". Choose the install or replace
driver option and select WinUSB. You can either google for zadig or download
it from the cgminer directory in the DOWNLOADS link above.

When you first switch a device over to WinUSB with zadig and it shows that
correctly on the left of the zadig window, but it still gives permission
errors, you may need to unplug the USB miner and then plug it back in. Some
users may need to reboot at this point.
Advanced USB options:

The --usb option can restrict how many USB devices are found:

  --usb 1:2,1:3,1:4,1:*
or
  --usb BAS:1,BFL:1,MMQ:0,ICA:0,KLN:0
or
  --usb :10

You can only use one of the above 3

The first version
  --usb 1:2,1:3,1:4,1:*
allows you to select which devices to mine on with a list of USB
 bus_number:device_address
All other USB devices will be ignored
Hotplug will also only look at the devices matching the list specified and
find nothing new if they are all in use
You can specify just the USB bus_number to find all devices like 1:*
which means any devices on USB bus_number 1
This is useful if you unplug a device then plug it back in the same port,
it usually reappears with the same bus_number but a different device_address

You can see the list of all USB devices on linux with 'sudo lsusb'
Cgminer will list the recognised USB devices

with the '-n' option or the
'--usb-dump 0' option
The '--usb-dump N' option with a value of N greater than 0 will dump a lot
of details about each recognised USB device
If you wish to see all USB devices, include the --usb-list-all option

The second version
  --usb BAS:1,BFL:1,MMQ:0,ICA:0,KLN:0
allows you to specify how many devices to choose based on each device
driver cgminer has - the current USB drivers are:
AVA, BAS, BFL, BF1, DRB, HFA, ICA, KLN and MMQ.

N.B. you can only specify which device driver to limit, not the type of
each device, e.g. with BAS:n you can limit how many BFL ASIC devices will
be checked, but you cannot limit the number of each type of BFL ASIC

Also note that the MMQ count is the number of MMQ backplanes you have
not the number of MMQ FPGAs

The third version
  --usb :10
means only use a maximum of 10 devices of any supported USB devices
Once cgminer has 10 devices it will not configure any more and hotplug will
not scan for any more
If one of the 10 devices stops working, hotplug - if enabled, as is default
- will scan normally again until it has 10 devices

  --usb :0 will disable all USB I/O other than to initialise libusb

# -cgminer2022
