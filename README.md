Big thanks to Mitsurugi_w, Darksoft, and Brizzo of Arcade Projects for finally allowing this to be published.

- written by hostile, with supporting information from elguapo

<p align="center">
<img src="https://github.com/ArcadeHustle/X3_USB_softmod/blob/master/walsdawg.jpeg"><img src="https://github.com/ArcadeHustle/X3_USB_softmod/blob/master/darksoft.jpeg">
</p>

<p align="center">
  <img src="https://github.com/ArcadeHustle/X3_USB_softmod/blob/master/arcadeprojects.jpeg"><img src="https://github.com/ArcadeHustle/X3_USB_softmod/blob/master/brizzo.jpeg">
</p>

# Stage One:
"アーケード版『ボーダーブレイク』の今後について" (The future of the arcade version of “Border Break”)<br>
As of 2019-06-06 the arcade version of BorderBreak will be no more than a memory - http://borderbreak.com/news/1186

<p align="center">
  <img src="http://borderbreak.com/content/common/xu4X1X1kaH2Z5RQ">
</p>

If you don't speak Japanese the key portions of the text that are relevant to this document are:

(translated) 
"Hello. This is Aoki, producer of the 'BORDER BREAK' series. Thank you very much for playing the arcade version of 'Border Break'. 
An arcade version that has been in operation for 9 years since September 9, 2009. The service has ended on September 9, 2019. 
'Border Break' has been judged(?) due to various circumstances. However, the main reason is the deterioration of the hardware due to 
the ten years. In addition to the deterioration of the cavity(?) itself over time, there are many problems that are difficult to 
respond to in the future, such as the cost of manufacturing and supplying replacement parts and the discontinuation of IC card 
manufacturing. Another reason is that it has become difficult to provide you with a satisfying battle environment. While many 
people are still playing the arcade version, it is very painful to have reached such an announcement, but I hope that the last 10 
years of glory will be met."

The full text is archived here<br>
https://pastebin.com/raw/XpkMXQgw<br>
https://translate.google.com/translate?sl=ja&tl=en&u=https%3A%2F%2Fpastebin.com%2Fraw%2FXpkMXQgw

Additional text relevant to this document can be found below: 

Exemptions to Prohibition against Circumvention of Technological Measures Protecting Copyrighted Works – Seventh 
Triennial Section 1201 Final Rule, Effective October 28, 2018 https://library.osu.edu/document-registry/docs/1027/stream 
"Video games in the form of computer programs, where outside server support has been discontinued, to allow individual 
play and preservation by an eligible library, archive, or museum"

https://library.osu.edu/site/copyright/2019/03/20/2018-dmca-section-1201-exemptions-announced/ "Video games in the 
form of computer programs, lawfully acquired as complete games 37 CFR §201.40(b)(12)" "For personal, local gameplay; 
or To allow preservation in a playable format..."

Please note that the following text is considered "for purposes of good-faith security research".

For now some of this information will be further gatekept. This write up will absolutly however give you all the access 
you need to backup and preserve your RingEdge hardware featuring BorderBreak. Please note that this preservation may apply
to other devices in the Ring* family such as RingEdge2, and RingWide. 

Please remember the wise words of Mitsurugi_w "The info itself is not new or special. It's all over the web anyways" 

# Stage Two:

For a long time the details of how Ring* devices are duplicated has been a closely guarded, and heavily traded / paid for
secret. With the first decade of deployment coming to a close, it is also time to close off this "Internet Money Maker". 
As hardware begins to fail, the threat of required preservation looms. 

The tool 'hdparm' can be used to query and help provision new disk drives for use in Ring* platforms. Below is the identifying
detail from two Ring* Solid State Disk drives. 

## Original drive label:
RingEdge MDA-E0005
GBDisk RS2 32GB

Controller - TDK GBDriver RS2 W5AB0067<br>
https://product.tdk.com/info/en/catalog/datasheets/ew_015_rs2.pdf

```
$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
        Model Number:       GBDriver RS2                            
        Serial Number:      TSS-G32C420000012732
        Firmware Revision:  rs2.a000
```

## Original drive label:
RingEdge MDA-E0007A
GBDisk RS3 32GB 

Controller - TDK GBDriver RS3 W5AB0084<br>
https://product.tdk.com/info/en/catalog/datasheets/ew_018_rs3.pdf

```
$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
        Model Number:       GBDriver RS3                            
        Serial Number:      TSS-G32C410001011219
        Firmware Revision:  rs3.b000
```

If you wish to archive, or replace your original drive you can search for used TDK GBDriver disks, or alternately you can provision 
certain drives to be identical to a GBDriver disk. MP (Mass Production) tools are used to configure SDD drive paramaters. Finding 
the MPTools for any given drive can be a difficult task, although many tools are archived at https://www.usbdev.ru or http://www.upantool.com
Once you have obtained the proper MPTool, you can change the Model Number, and Serial number of the drive. In somecases you can also 
change the Firmware Revision. 

If you still have no clue what an MPTool is, please contact Darksoft or Mitsurugi_w on Arcade Projects forum and ask for help with the RingEdge
SSD softmod. https://www.arcade-projects.com/forums/index.php?board/73-sega-ringedge-ringwide-and-nu/

Two SSD controllers brands known to frequently have their MPTools *leaked* are JMicron and Silicon Motion. Jmicron JMF6xx series are known to be 
usable however we have instead chosen to make use of SMI (Silicon Motion) based drives. It should be noted that cloned Ring* SSD drives have been 
seen sold on eBay using JMicron JMF605 and JMF607 controller based drives in the past. http://www.jmicron.com/PDF/brief/jmf607.pdf
One example of a known working JMF based drive is the KingSpec SSD: KSD-SA25.7-XXXMJ 

Below is an example of a known working donor drive that can be provisioned to appear as the *required* TDK GBDriver model. 

## Donor drive label:
32GB Transcend<br>
TS32GSSD370S<br>
Buy: https://www.amazon.com/gp/product/B00VX82PJC/

Controller - Silicon Motion SM2246EN<br>
http://www.siliconmotion.com/A3.2_Partnumber_Detail.php?sn=7

```
$ sudo hdparm -I /dev/sdb | less

/dev/sdb:

ATA device, with non-removable media
        Model Number:       TS32GSSD370S                            
        Serial Number:      F006000137          
        Firmware Revision:  P1225CH1
```

SM2246 Secondary MP Tool Q0321A from USBDev.ru can be used to provision the example drive on a Windows machine.
https://www.usbdev.ru/files/smi/secondarymp/

Check "Update Serial Number"<br>
Serial Number should be set to "Normal SN"<br>
SN Length "20"<br>
Serial Mask "TSS-"<br>
Begin Serial "TSS-G0fuckAdarksoft1"<br>
End Serial "TSS-G0fuckAdarksoft2"<br>
Check "Update Model Name"<br>
Model Name "GBDriver RS2"<br>
Vendor Specific "TRANSCEND"<br>
<br>
It is really important to use the Serial "TSS-G0fuckAdarksoft1" in order to bypass the drive checks. Other serials
may work, but this pattern is known to work with RingEdge and RingWide devices. 

<p align="center">
<img src="https://github.com/ArcadeHustle/RingEdge_SSD_Softmod/blob/master/MPToolWrite.PNG">
</p>

SM2246EN should be selected in the right corner, click Start. 

Once complete you should see the following
<p align="center">
<img src="https://github.com/ArcadeHustle/RingEdge_SSD_Softmod/blob/master/MPToolSuccess.PNG">
</p>

Please note, if the drive is locked, you won't see it in the MPTool!

You can plug the drive into your Linux machine and verity the serial number and model information after your attempt.  
```
$ dmesg 
[870162.954165] usb 1-1: new high-speed USB device number 36 using xhci_hcd
[870163.106302] usb 1-1: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[870163.106311] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[870163.106316] usb 1-1: Product: ASM105x
[870163.106321] usb 1-1: Manufacturer: ASMT
[870163.106325] usb 1-1: SerialNumber: TSS-G0fuckAdarksoft1
[870163.111979] scsi host1: uas
[870163.113837] scsi 1:0:0:0: Direct-Access     GBDriver  RS2             0    PQ: 0 ANSI: 6
```

```
$ sudo hdparm -I /dev/sdb 

/dev/sdb:

ATA device, with non-removable media
        Model Number:       GBDriver RS2
        Serial Number:      TSS-G0fuckAdarksoft1
        Firmware Revision:  P1225CH1
```
If you attempt to change the "Vendor Specific" section you may see an error in the Firmware Revision. 

```
/dev/sdb:

ATA device, with non-removable media
        Model Number:       GBDriver RS2
        Serial Number:      TSS-G000fuckAdarksof
        Firmware Revision:  y CID H
```

The "y CID" appears to be a bug in the MPTool, although on Ring* it does not seem to pose a problem.  

# Final Boss:

The last step involves being able to lock and unlock the drive. If you are doing this over USB it 
is really important to be using device that is known to work. Below are some known good and bad devices. 
One very common generic SATA adapter is on the known bad list. JM20337 is used in many SATA -> USB adapters! 

## Works:
https://amazon.com/Thermaltake-Externa…ng-N0028USU/dp/B0012Z3MKW<br>
https://www.amazon.com/StarTech-com-10Gbps-Adapter-Cable-Drives/dp/B00XLAZODE
```
ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
ID 13fd:0840 Initio Corporation INIC-1618L SATA - 
ID 7825:a2a4 - Kingwin unknown model.  
```
## Fails:
```
ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge - Kingwin USI-2535
```
You will need access to a patched version of HDParm in order to unlock the drive, and the previously leaked ATA password:
```
7242525ABA526A5AEA726278CA42DA4A2A223A2A0A221A2A6A027A0A5CCE4A0A
```
https://web.archive.org/web/20180918072136/http://gakman.forumactif.com/t72-ringedge-ringwide

Armed with this information you can unlock the original drive and clone it. 
```
# echo -e "\x72\x42\x52\x5A\xBA\x52\x6A\x5A\xEA\x72\x62\x78\xCA\x42\xDA\x4A\x2A\x22\x3A\x2A\x0A\x22\x1A\x2A\x6A\x02\x7A\x0A\x5C\xCE\x4A\x0A" > file
```
You can download the hdparm patch from here: https://sourceforge.net/p/hdparm/feature-requests/14/<br>
"#14 Add ability to specify non-ASCII security passwords"<br>
Specifically you need https://sourceforge.net/p/hdparm/feature-requests/_discuss/thread/a242a074/1760/attachment/security_file_diff.txt

The HDParm source should be pulled from github. 
```
# git clone https://github.com/Distrotech/hdparm.git; cd hdparm
Cloning into 'hdparm'...
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 66 (delta 0), reused 0 (delta 0), pack-reused 65
Unpacking objects: 100% (66/66), done.
Checking connectivity... done.
```

Patch and build the source code. 
```
# cat security_file_diff.txt | patch -p1
patching file hdparm.c
Hunk #1 succeeded at 133 (offset 3 lines).
Hunk #2 succeeded at 794 (offset 5 lines).
Hunk #3 succeeded at 1531 with fuzz 2 (offset 15 lines).
Hunk #4 succeeded at 2447 (offset 15 lines).
Hunk #5 succeeded at 2462 (offset 15 lines).
Hunk #6 succeeded at 2571 (offset 15 lines).
```

```
# make
cc -O2 -W -Wall -Wbad-function-cast -Wcast-align -Wpointer-arith -Wcast-qual -Wshadow -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -fkeep-inline-functions -Wwrite-strings -Waggregate-return -Wnested-externs -Wtrigraphs -c -o hdparm.o hdparm.c
cc -s -o hdparm hdparm.o identify.o sgio.o sysfs.o geom.o fallocate.o fibmap.o fwdownload.o dvdspeed.o wdidle3.o
strip hdparm
```

Now you can use the ATA password that was written to a file previously. 
```
# xxd file 
00000000: 7242 525a ba52 6a5a ea72 6278 ca42 da4a  rBRZ.RjZ.rbx.B.J
00000010: 2a22 3a2a 0a22 1a2a 6a02 7a0a 5cce 4a0a  *":*.".*j.z.\.J.
00000020: 0a  
```

```
# cat lock.sh 
./hdparm --user-master u --security-set-pass-from-file file /dev/sdb

# cat unlock.sh 
./hdparm --user-master u --security-unlock-from-file file /dev/sdb

# cat disable.sh 
./hdparm --user-master u --security-disable-from-file file /dev/sdb
```

Once the drive is unlocked it can be properly copied. 

```
# ./unlock.sh 
Read 32 bytes from "file".

/dev/sdb:
 Issuing SECURITY_UNLOCK command, password="[read from file]", user=user

# dd of=../ringedge_drive_image.img  if=/dev/sdb bs=1M status=progress
```

Now replace the original drive with the new drive, write the cloned data, and lock the drive back  

```
# dd if=../ringedge_drive_image.img  of=/dev/sdb bs=1M status=progress

# ./lock.sh 
Read 32 bytes from "file".

/dev/sdb:
 Issuing SECURITY_SET_PASS command, password="[read from file]", user=user, mode=high

```

Please note: You will STILL need to have the proper security key in order to play the cloned drive. 

Have fun! Be safe! We will be back with more soon.

Official video tutorial for the RingEdge SSD softmod by Mitsu (as usual!) can be found here: https://www.youtube.com/watch?v=l0nq1pQXX90

