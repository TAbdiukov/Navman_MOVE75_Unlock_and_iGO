# Navman_MOVE75_Unlock_and_iGO
Unlock Navman MOVE75 and install iGO on it

## Known issues

1. **[worked-around]** iGO does not run from the first time. 

	* MortScript workaround applied

2. **[replaced]** The device does NOT work with [PowerM](http://4pna.com/showthread.php?t=9092) . Fails at the line 216. No known fix, but MortScr workaround applied.

3. **[worked-around through PowerOff]** The device will NOT sleep (suspend, hibernate) properly, as the device will fail to jump back into iGO. This is because iGO is being launched from MortScript, which the system does NOT go after sleep as required for the proper functioning.
	
	* Therefore, step 3 is required to mitigate the issue.

	* MortScript workaround for PowerOff applied


## How to unlock a stock device
`cd` to Program Files -> Navman . Then either 
1. Replace AppStartupSec.exe with Total Commander (`AppStartupSec.exe.tc`) , or
2. Modify appstartupsec.ini to run your apps

## How to run iGo on this device
This device **extraordinarily** does not allow running iGO, so  to work around this issue, MortScript was employed

This is likely the Navman's vendor restriction

To work around the issue
1. Copy all files to the device
2. Copy iGo packages to `(device root)\IGO\` . So iGo must be in `(device root)\IGO\Navi.exe`
3. Append your `(device root)\IGO\sys.txt` with data from `(device root)\IGO\sys_required_params.txt`
	
	This step is required to mitigate bugs


## Startup sequences comparison

* Normal startup: Bootloader -> ??? -> AppStartupSec.exe -> (multiple applications including) Navman
* Quick unlock: Bootloader -> ??? -> ~~AppStartupSec.exe~~ Total Commander
* Unlocked startup (this repo): Bootloader -> ??? -> AppStartupSec.exe -> (multiple applications including) ~~Navman~~ MortScript Autorun -> MortScript (custom autorun.mscr) -> modified iGo initialisation sequence -> iGo

## Credits
* jbeep.wav - [taken on Freesound (no copyright)](https://freesound.org/people/jodybruchon/sounds/459460/)

## Other
### PortTool v9
```
===PortTool Log v. 1, 0, 0, 9 === 
PortTool execution path : \My Flash Disk\PortTool.exe 
CPU : ARM rev.3 
Path to navi :  
USB : [Async/Flash card/CardReader] 
UUID in About : [yes/no] 
Internet : [yes/no] 
RAM : total: 108 Mb, avail: 93 Mb 
UUID : 16 byte: 31 30 30 30 30 30 30 30 - 30 30 37 36 64 66 35 62 (31303030303030303030373664663562) 
Screen : 480x272 16 bit 
OS Version : 6 
Battery status : Critical 
Battery percent : 14 
wininet.dll : yes 
OEM info : 'MStar Semiconductor' 40 byte: 4D 00 53 00 74 00 61 00 72 00 20 00 53 00 65 00 6D 00 69 00 63 00 6F 00 6E 00 64 00 75 00 63 00 74 00 6F 00 72 00 00 00  
THUMB : yes 
FlashCards 
  name : My Flash Disk 
  name : NandBlk 
  Disk size : 3680.37 Mb 3859144704 bytes 
  Mapping : AVR Write: 1333 KB/s
	    AVR Read: 552 KB/s 
  Mapping time : 18 sec, 100 % 
  
GPS: 
  Port : COM0: 
  Rate : 57600
 
  Port : COM2: 
  Rate : 57600
 
  Port : COM3: 
  Rate : 57600
 
String test : Ok 
System date/time :   (1:57:56 AM, 1/1/2014) 
================== 
```