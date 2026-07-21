# Recovery
## Android Recovery
`adb reboot recovery`
or
VOL+ and POWER, HOLD until the Pico logo appears.

Once `No Command` appears:  
HOLD the POWER button and press the VOL+ button once, release the POWER button.
## Android Bootloader
`adb reboot bootloader`  
or  
VOL- and POWER, HOLD until the Pico logo appears.
## EDL
With Qualcomm SOC's bricked devices can be recovered, or devices can otherwise downgraded by using EDL (Emergency Download mode).  
https://en.wikipedia.org/wiki/Qualcomm_EDL_mode
### Warnings

> [!CAUTION]
> **BACK UP** your partitions.
> 
> Do **NOT** flash incorrect firmware to the XBL partition.  
> Do **NOT** flash incorrect firmware to the ABL partition unless you have a Deep Flash cable.
> 
> Messing up your partition data can cause your device to **BRICK** or softbrick!

- If you flash wrong firmware to the ABL:  
  You will need a Deep Flash cable, or a cable to short `GND` and `D+`. Hold VOL- when shorting whilst booting to get back into EDL.
### Downgrading
With EDL you can downgrade to any Pico OS version.  
This process will require you to wipe your data.

Requirements:
- A working firehose.
- The Qualcomm Flash Image Loader (QFIL) or other flashing tool.
- The Qualcomm USB drivers.
- A backup from an older OS.

There are two known working firehoses for Pico devices:
- `prog_firehose_lite.elf`
- `prog_firehose_ddr.elf`
	- This firehose will first initialize DDR4 RAM   
	(do not use on the Pro / Enterprise variants with DDR5 RAM)  
These firehoses were leaked with the Neo3 `4.6.10.81.10` OS.

1. To enter EDL, boot into Android, plug in the Pico to your computer, and on a command line enter `adb reboot EDL`
2. The device will boot into EDL mode.
3. In QFIL, select `Flat build` as the build type.
4. Select the firehose.
	If QFIL times out, then you are using an incorrect firehose.
5. Set `Storage Type` in the bottom right corner to `UFS`.
6. Go to `Tools > Partition Manager`, press OK and wait.
7. Flash the 
	- `(LUN 0) super` 
	- `(LUN 4) boot` and `(LUN 4) bootbak`
	- `(LUN 4) dtbo` and `(LUN 4) dtbobak`
	- `(LUN 4) vbmeta` and `(LUN 4) vbmetabak`  
	…partitions with your downgraded version.
8. Hold the POWER button and VOL+ until the Pico logo appears  
   (Holding POWER for 10 seconds will exit EDL mode)
9. Your screen will show `No Command`.
10. Hold the POWER button and press the VOL+ button once, then release the POWER button.
11. Select factory reset, and wait for the device to reboot.
## Partitions

| LUN | Label            | Start LBA           | LBA Number         | Notes                                                                          |
| --- | ---------------- | ------------------- | ------------------ | ------------------------------------------------------------------------------ |
| 0   | ssd              | 0x0000000000000006  | 0x0000000000000002 | Secure Software Download                                                       |
| 0   | persist          | 0x0000000000000008  | 0x0000000000002000 | Persisted configuration                                                        |
| 0   | cache            | 0x0000000000002008  | 0x000000000000A000 | Temporary files / logs                                                         |
| 0   | misc             | 0x000000000000A208  | 0x0000000000000100 | Flags for bootloader                                                           |
| 0   | keystore         | 0x000000000000A2108 | 0x0000000000000080 | Encryption keys, credentials and tokens                                        |
| 0   | frp              | 0x000000000000A2188 | 0x0000000000000080 | Factory Reset Protection                                                       |
| 0   | super            | 0x000000000000A2208 | 0x0000000000020000 | Sub-partitions                                                                 |
| 0   | recovery         | 0x000000000002A2208 | 0x0000000000006400 | OTA, recovery, emergency boot                                                  |
| 0   | vbmeta_system    | 0x000000000002A8608 | 0x0000000000000010 | Cryptographic signatures used by Android Verified Boot for partition integrity |
| 0   | vbmeta_systembak | 0x000000000002A8618 | 0x0000000000000010 | Backup                                                                         |
| 0   | metadata         | 0x000000000002A8628 | 0x0000000000001000 | Used by Android's storage framework                                            |
| 0   | vm-system        | 0x000000000002A9628 | 0x0000000000008000 | Qualcomm Hypervisor/VM                                                         |
| 0   | vm-systembak     | 0x000000000002B1628 | 0x0000000000008000 | Backup                                                                         |
| 0   | rawdump          | 0x000000000002B9628 | 0x0000000000008000 | Kernel crashes / RAM dumps                                                     |
| 0   | userdata         | 0x00000000002C1629  | 0x00000000073E51D2 | Internal storage                                                               |
| 1   | xbl              | 0x0000000000000006  | 0x0000000000000380 | eXtensible Boot Loader. Qualcomm bootloader.                                   |
| 1   | xbl_config       | 0x0000000000000386  | 0x0000000000000020 |                                                                                |
| 1   | last_parti       | 0x00000000000003A6  | 0x0000000000000455 | Marker for LUN end.                                                            |
| 2   | xblbak           | 0x0000000000000006  | 0x0000000000000380 |                                                                                |
| 2   | xbl_configbak    | 0x0000000000000386  | 0x0000000000000020 |                                                                                |
| 2   | last_parti       | 0x00000000000003A6  | 0x0000000000000455 | Marker for LUN end.                                                            |
| 4   | aop              | 0x0000000000000006  | 0x0000000000000080 | Always On Processor                                                            |
| 4   | tz               | 0x0000000000000086  | 0x0000000000000400 | TrustZone. Qualcomm secure environment.                                        |
| 4   | hyp              | 0x0000000000000486  | 0x0000000000000800 | Hypervisor                                                                     |
| 4   | modem            | 0x0000000000000C86  | 0x0000000000018B00 | Cellular firmware.                                                             |
| 4   | bluetooth        | 0x0000000000019786  | 0x0000000000000100 | Qualcomm Bluetooth Controller.                                                 |
| 4   | mdtpsecapp       | 0x0000000000019886  | 0x0000000000000400 | Environment for MDTP                                                           |
| 4   | mdtp             | 0x0000000000019C86  | 0x0000000000002000 | Module Data Theft Protection                                                   |
| 4   | abl              | 0x000000000001BC86  | 0x0000000000000100 | Android Bootloader                                                             |
| 4   | dsp              | 0x000000000001BD86  | 0x0000000000004000 | Digital Signal Processor                                                       |
| 4   | keymaster        | 0x000000000001FD86  | 0x0000000000000080 | Cryptographic operations for TrustZone                                         |
| 4   | boot             | 0x000000000001FE06  | 0x0000000000006000 | Android Linux Kernel Image.                                                    |
| 4   | cmnlib           | 0x0000000000025E06  | 0x0000000000000080 | Core libraries for TrustZone                                                   |
| 4   | cmnlib64         | 0x0000000000025E86  | 0x0000000000000080 | Core libraries for TrustZone                                                   |
| 4   | devcfg           | 0x0000000000025F06  | 0x0000000000000020 | Hardware configuration                                                         |
| 4   | qupfw            | 0x0000000000025F26  | 0x0000000000000014 | Qualcomm Universal Pheripheral block                                           |
| 4   | vbmeta           | 0x0000000000025F3A  | 0x0000000000000010 | Verified Boot Metadata                                                         |
| 4   | dtbo             | 0x0000000000025F4A  | 0x0000000000001800 | Device Tree Blob Overlay                                                       |
| 4   | uefisecapp       | 0x000000000002774A  | 0x0000000000000200 | EUFI Security Application                                                      |
| 4   | multiimgoem      | 0x000000000002794A  | 0x0000000000000008 | Configuration for multi boot (A/B slot switching)                              |
| 4   | multiimgqti      | 0x0000000000027952  | 0x0000000000000008 | S/A                                                                            |
| 4   | vm-linux         | 0x000000000002795A  | 0x0000000000002000 | Hypervisor guest image                                                         |
| 4   | featenabler      | 0x000000000002995A  | 0x0000000000000020 | Qualcomm feature license flags                                                 |
| 4   | imagefv          | 0x000000000002997A  | 0x0000000000000200 | EUFI firmware for boot drivers                                                 |
| 4   | aopbak           | 0x0000000000029B7A  | 0x0000000000000080 |                                                                                |
| 4   | tzbak            | 0x0000000000029BFA  | 0x0000000000000400 |                                                                                |
| 4   | hypbak           | 0x0000000000029FFA  | 0x0000000000000800 |                                                                                |
| 4   | modembak         | 0x000000000002A7FA  | 0x0000000000018B00 |                                                                                |
| 4   | bluetoothbak     | 0x00000000000432FA  | 0x0000000000000100 |                                                                                |
| 4   | mdtpsecappbak    | 0x00000000000433FA  | 0x0000000000000400 |                                                                                |
| 4   | mdtpbak          | 0x00000000000437FA  | 0x0000000000002000 |                                                                                |
| 4   | ablbak           | 0x00000000000457FA  | 0x0000000000000100 |                                                                                |
| 4   | dspbak           | 0x00000000000458FA  | 0x0000000000004000 |                                                                                |
| 4   | keymasterbak     | 0x00000000000498FA  | 0x0000000000000080 |                                                                                |
| 4   | bootbak          | 0x000000000004997A  | 0x0000000000006000 |                                                                                |
| 4   | cmnlibbak        | 0x000000000004F97A  | 0x0000000000000080 |                                                                                |
| 4   | cmnlib64bak      | 0x000000000004F9FA  | 0x0000000000000080 |                                                                                |
| 4   | devcfgbak        | 0x000000000004FA7A  | 0x0000000000000020 |                                                                                |
| 4   | qupfwbak         | 0x000000000004FA9A  | 0x0000000000000014 |                                                                                |
| 4   | vbmetabak        | 0x000000000004FAAE  | 0x0000000000000010 |                                                                                |
| 4   | dtbobak          | 0x000000000004FABE  | 0x0000000000001800 |                                                                                |
| 4   | uefisecappbak    | 0x00000000000512BE  | 0x0000000000000200 |                                                                                |
| 4   | multiimgoembak   | 0x00000000000514BE  | 0x0000000000000008 |                                                                                |
| 4   | multiimgqtibak   | 0x00000000000514C6  | 0x0000000000000008 |                                                                                |
| 4   | vm-linuxbak      | 0x00000000000514CE  | 0x0000000000002000 |                                                                                |
| 4   | featenablerbak   | 0x00000000000534CE  | 0x0000000000000020 |                                                                                |
| 4   | imagefvbak       | 0x00000000000534EE  | 0x0000000000000200 |                                                                                |
| 4   | dip              | 0x00000000000536EF  | 0x0000000000000100 | Device Integrity Policy                                                        |
| 4   | apdp             | 0x00000000000537EF  | 0x0000000000000040 | Application Processor Debug Policy                                             |
| 4   | msadp            | 0x000000000005382F  | 0x0000000000000040 | Modem Subsystem Debug Policy                                                   |
| 4   | spunvm           | 0x000000000005386F  | 0x0000000000002000 | Secure Processing Unit VM image                                                |
| 4   | logfs            | 0x0000000000055871  | 0x0000000000000800 | Logs for low-level systems                                                     |
| 4   | logdump          | 0x0000000000056071  | 0x0000000000004000 | Log and crash dumps                                                            |
| 4   | storsec          | 0x000000000005A071  | 0x0000000000000020 | Storage Security, used for Replay Protected Memory Block                       |
| 4   | uefivarstore     | 0x000000000005A091  | 0x0000000000000080 | Non-volatile EUFI variable states, boot, env variables                         |
| 4   | secdata          | 0x000000000005A111  | 0x0000000000000007 | Security policy metadata, anti-rollback counters, security flags               |
| 4   | vm-keystore      | 0x000000000005A118  | 0x0000000000000020 | Virtual Machine keystore                                                       |
| 4   | vm-data          | 0x000000000005A138  | 0x0000000000000400 | Virtual Machine data                                                           |
| 4   | last_parti       | 0x000000000005A538  | 0x0000000000025AC3 | Boundary of this LUN                                                           |
| 5   | ALIGN_TO_128K_2  | 0x0000000000000006  | 0x000000000000001A | Dummy alignment                                                                |
| 5   | modemst1         | 0x0000000000000020  | 0x0000000000000200 | Non-volatile RAM for cell modem config                                         |
| 5   | modemst2         | 0x00000000000000220 | 0x0000000000000200 | S/A                                                                            |
| 5   | fsg              | 0x0000000000000420  | 0x0000000000000200 | Modem Golden Copy (backup for modemst)                                         |
| 5   | fsc              | 0x0000000000000620  | 0x0000000000000020 | Modem Cookie Store                                                             |
| 5   | mdm1m9kefs3      | 0x0000000000000640  | 0x0000000000000200 | Modem Embedded File System. Modem configuration.                               |
| 5   | mdm1m9kefs1      | 0x0000000000000840  | 0x0000000000000200 | S/A                                                                            |
| 5   | mdm1m9kefs2      | 0x0000000000000A40  | 0x0000000000000200 | S/A                                                                            |
| 5   | last_parti       | 0x0000000000000C41  | 0x00000000000013BA | Boundary of this LUN                                                           |
