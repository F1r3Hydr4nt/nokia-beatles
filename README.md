|  | Nokia 2720 Flip (beatles) |
| --- | --- |
| Released | 5 September 2019 |
| Model | TA-1175, TA-1173, TA-1170, TA-1168 |
| ***Specifications*** |     |
| SoC | Qualcomm MSM8905 Snapdragon 205 (2 x 1.1Ghz Cortex-A7) |
| RAM | 512MB LPDDR2/3 |
| GPU | Adreno 304 |
| Storage | 4GB (+ up to 32GB microSDHC card) |
| Network | - 2G GSM<br>- 3G UMTS<br>- 4G LTE (Cat4)<br>    + EU: band 1, 3, 5, 7, 8, 20<br>    + MENA, APAC, GCR: band 1, 3, 5, 7, 8, 20, 28, 38, 39, 40, 41<br>- VoLTE & VoWiFi support<br>- Single or Dual SIM (Nano-SIM, dual standby) |
| Screen | Main: 320 x 240 (143 PPI), 2.8 inches QVGA TFT LCD<br>External: 240 x 240, 1.3 inches TFT LCD |
| Bluetooth | 4.1, A2DP, LE |
| Wi-Fi | 802.11b/g/n, Hotspot |
| Peripherals | GPS |
| Camera | Rear: 2MP, LED flash |
| Dimensions<br>(H x W x D) | Open: 192.7 x 54.5 x 11.6 (mm) – 7.59 x 2.15 x 0.46 (in)<br>Closed: 104.8 x 54.5 x 18.7 (mm) |
| Weight | 118g (4.16oz) |
| Battery | Removable Li-Ion 1500mAh (BL-6A) |
| Specials | TBD |
| ***KaiOS info*** |  |
| Version | KaiOS 2.5.2, upgradable to KaiOS 2.5.2.2 |
| Build number | (TA-1170) 21.00.17.01, 22.00.17.01, 30.00.17.05, 40.00.17.02 |

To sideload and debug third-party applications, follow the guide at [Development/WebIDE on BananaHackers Wiki](https://wiki.bananahackers.net/en/development/webide).

## Tips and tricks

- To take a screenshot, press both `*` and `#` keys.
- On the home screen, hold down a number key (1-9) to set up and activate Speeddial.

## Known issues

### KaiOS-specific

- Text messages don't automatically convert to MMS in group chats. You'll have to add a message subject or file attachment before sending to manually do so, otherwise your message will be sent separately to each individual in the thread.
- Predictive typing mode doesn't last between inputs, meaning if you switch between input boxes, it'll return to the normal T9 mode.
- You cannot change message notification tone or alarm tone on the phone outside the defaults provided. This is because both are not managed by the system, but by the Messages and Clock app themselves. To change them, you'll have to use ADB to pull the apps from `/system/b2g/webapps`, extract, edit the audio files and repackage the apps, then push them back under `/data/local/webapps` and edit the `basePath` in `/data/local/webapps/webapps.json` to reflect the change (see [BananaHackers' guide](https://ivan-hc.github.io/bananahackers/clock-alarms.html#h.unmy3yif91xs) for instructions)
- Built-in email, calendar and contact syncing function with Google account may completely fail at times. Use IMAP and import contacts instead.
- Speaking of calendar, if you manage to sync your Google account with the phone, only the calendar *with your email address as its name* will sync.
- Apps like Contacts and Music are written in performance-intensive React and therefore render significantly slow if you store lots of contact entries and audio files.
- Of course, missing features.

## Secret codes

- `*#*#33284*#*#`: Toggle debugging mode, allow the phone to be accessed with ADB and DevTools.
- `*#06#`: Display the IMEI(s).
- `*#0000#`: Display device information, such as firmware version, build date, model number, variant and CUID.

## Special boot modes

- Recovery mode: With the device powered off, hold both `Power/End call` and `Volume up` keys, or type `adb reboot recovery` when connected to a computer. Allows you to factory reset the device by wiping /data and /cache, view boot and kernel logs, and install patches from `adb sideload` interface or SD card.
- EDL mode: With the device powered off, hold the `Power/End call` and both side volume keys, or type `adb reboot edl` when connected to a computer. Boots into a black screen, allows you to read and write partitions in low-level with proprietary Qualcomm tools. Remove the battery to exit.

EDL loader for this phone can be found on BananaHackers' [EDL archive site](https://edl.bananahackers.net/loaders/2720.mbn) with hardware ID 0x009600e100420029.