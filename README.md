### Make a bootable PDP-11/40 disk image to run KLDCP on SIMH.

```
;ON DISK, SECTORS 1 AND 10 DECIMAL
;ARE "HOME BLOCKS" WHICH CONTAIN PHYSICAL DISK ADDRESS AND NUMBER
;OF SECTORS OF THE DIRECTORY.  HOME BLOCKS AND DIR HAVE TO BE
;SET UP BY HAND.  THE DIRECTORY IS A FILE IN THE ITS FILE SYSTEM.
;SECTOR 0 CONTAINS A BOOT PROGRAM WHICH IS READ IN BY THE BOOT ROM
;WHEN THE DISK BUTTON IS PUSHED.  IT'S A PDP-11 PROGRAM.  IT READS
;IN THE "PRIMARY BOOTSTRAP" FROM A DISK ADDRESS HARD-WIRED INTO IT.
;THE PRIMARY BOOTSTRAP FINDS KLDCP IN THE DIRECTORY AND RUNS IT.
;TO CHANGE THE DISK SIZE, YOU MUST CHANGE SEVERAL ADDRESSES IN THE
;HOME BLOCKS AND IN THE SECTOR 0 BOOT PROGRAM.  OF COURSE YOU MUST
;ALSO CHANGE SEVERAL PDP10 PROGRAMS.

;THE FILE KLDCP;HOME BLOCKS CONTAINS A COPY OF SECTORS 0-15. OF THE DISK.
;THE FILE KLDCP;PRIMRY BOOT CONTAINS A COPY OF THE PRIMARY BOOTSTRAP.
;THESE ARE JUST REFERENCE COPIES, THEY AREN'T STORED IN THE ACTUAL
;SPECIAL DISK ADDRESSES WHERE THOSE THINGS GO.

;THERE IS ALSO AN INDEX FILE AND A BIT MAP, WHICH WE DON'T USE.
;THEY ARE SET UP TO BE UP IN THE MAINTENANCE CYLINDERS SOMEPLACE,
;TO MAKE KLDCP HAPPY, ALTHOUGH IT DOESN'T USE THEM EITHER.
;ALSO, THE FIRST 6 SECTORS OF CYLINDER 406 (DECIMAL)
;CONTAIN THE "PRIMARY BOOTSTRAP."  THIS HAS TO BE SET UP BY HAND.

;ALLOCATION OF CYLINDERS ON AN RP04:
;     0-405. ITS FILE SYSTEM
;	406. PRIMARY BOOTSTRAP, KLDCP NOT-USED FILES
;	407. DSKDMP BOOT AND SWAP AREA
;	408. NOT USED
;	409. NOT USED
;	410. DDT BOOT AND SWAP AREA

;FORMAT OF SECTOR 0:
; ONE PDP-11 WORD PER PDP-10 HALFWORD
; RH(20) IS THE CYLINDER NUMBER OF THE PRIMARY BOOTSTRAP
; IT'S ON HEAD 0, SECTORS 0-4
```
