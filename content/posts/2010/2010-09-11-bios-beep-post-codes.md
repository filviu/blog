---
title: BIOS Beep POST Codes
author: silviu
type: post
date: 2010-09-11T08:26:02+00:00
url: /2010/09/11/bios-beep-post-codes/
categories:
  - old
tags:
  - temp_on

---
Ever found yourself standing next to a PC that won't boot and emits all kinds of short or long beeps. Me too. Here's a list of what these beeps _might_ mean.

Please note that because motherboard manufacturers often modify the code bought from these companies the beeps might mean something else.

### AWARD


|  Beeps  |  Error Message  |  Description  |
| --- | --- | --- |
|  1long, 2 short  |  Video adapter error  |  Either video adapter is bad or is not seated properly. Also, check to ensure the monitor cable is connected properly.  |
|  Repeating (endless loop)  |  Memory error  |  Check for improperly seated or missing memory.  |
|  1long, 3short  |  No video card or bad video RAM  |  Reseat or replace the video card.  |
|  High frequency beeeps while running  |  Overheated CPU  |  Check the CPU fan for proper operation. Check the case for proper air flow.  |
|  Repeating High/Low  |  CPU  |  Either the CPU is not seated properly or the CPU is damaged. May also be due to excess heat. Check the CPU fan or BIOS settings for proper fan speed.  |


### AMI BIOS

|  Beep Code  |  Descriptions  |
| --- | --- |
|  1 short  |  DRAM refresh failure  |
|  2 short  |  Parity circuit failure  |
|  3 short  |  Base 64K RAM failure  |
|  4 short  |  System timer failure  |
|  5 short  |  Process failure  |
|  6 short  |  Keyboard controller Gate A20 error  |
|  7 short  |  Virtual mode exception error  |
|  8 short  |  Display memory Read/Write test failure  |
|  9 short  |  ROM BIOS checksum failure  |
|  10 short  |  CMOS shutdown Read/Write error  |
|  11 short  |  Cache Memory error  |
|  1 long, 3 short  |  Conventional/Extended memory failure  |
|  1 long, 8 short  |  Display/Retrace test failed  |

### WINBIOS


|  Beeps  |  Error Message  |  Description  |  Resolution  |
| --- | --- | --- | --- |
|  1  |  Refresh Failure  |  The memory refresh circuitry is faulty.  |  Reseat the memory SIMMs. If the system still beeps, replace the memory.  |
|  2  |  Parity Error  |  Parity error in the base memory (the first 64 KB block) of memory.  |  Reseat the memory SIMMs. If the system still beeps, replace the memory.  |
|  3  |  Base 64 KB Memory Failure  |  Memory failure in first 64 KB.  |  Reseat the memory SIMMs. If the system still beeps, replace the memory.  |
|  4  |  Timer Not Operational  |  A memory failure in the first 64 KB of memory, or Timer 1 is not functioning.  |  The motherboard must be replaced.  |
|  5  |  Processor error 8042 - Gate A20 Failure  |  The CPU generated an error.  |  The motherboard must be replaced.  |
|  6  |  8042 - Gate A20 Failure Processor Exception Interrupt Error  |  Cannot switch to protected mode.  |  Try a different keyboard, or replace the keyboard fuse, if the keyboard has one.  |
|  7  |  Processor Exception Interrupt Error  |  The CPU on the CPU Card generated an exception interrupt.  |  The motherboard must be replaced.  |
|  8  |  Display Memory Read/Write Error  |  The system video adapter is either missing or its memory is faulty. This is not a fatal error.  |  There is a memory error on the video adapter. Replace the video adapter, or the RAM on the video adapter.  |
|  9  |  ROM Checksum Error  |  The ROM checksum value does not match the value encoded in WINBIOS.  |  The BIOS ROM chip is bad. The system probably needs a new BIOS ROM chip.  |
|  10  |  CMOS Shutdown Register Read/Write Error  |  The shutdown register for CMOS RAM has failed.  |  The motherboard must be replaced.  |
|  11  |  Cache memory bad - do not enable cache  |  The cache memory test failed. Cache memory is disabled. Do not press Ctrl/Alt/Shift <+> to enable cache memory.  |  The motherboard must be replaced.  |



### IBM BIOS

The following are IBM BIOS Beep Codes that can occur. However because of the wide variety of models shipping with this BIOS the beep codes may vary.

|  Beep Code  |  Descriptions  |
| --- | --- |
|  No Beeps  |  No Power, Loose Card, or Short.  |
|  1 Short Beep  |  Normal POST, computer is ok.  |
|  2 Short Beep  |  POST error, review screen for error code.  |
|  Continuous Beep  |  No Power, Loose Card, or Short.  |
|  Repeating Short Beep  |  No Power, Loose Card, or Short.  |
|  One Long and one Short Beep  |  Motherboard issue.  |
|  One Long and Two short Beeps  |  Video (Mono/CGA Display Circuitry) issue.  |
|  One Long and Three Short Beeps.  |  Video (EGA) Display Circuitry.  |
|  Three Long Beeps  |  Keyboard / Keyboard card error.  |
|  One Beep, Blank or Incorrect Display  |  Video Display Circuitry.  |


### MACINTOSH STARTUP TONES

|  TONES  |  ERROR  |
| --- | --- |
|  Error Tone. (two sets of different tones)  |  Problem with logic board or SCSI bus.  |
|  Startup tone, drive spins, no video  |  Problem with video controller.  |
|  Powers on, no tone.  |  Logic board problem.  |
|  High Tone, four higher tones.  |  Problem with SIMM.  |



### PHOENIX BIOS

PHOENIX BIOS Q3.07 OR 4.X

|  Beep Code  |  Descriptions / What to Check  |
| --- | --- |
|  1-1-1-3  |  Verify Real Mode.  |
|  1-1-2-1  |  Get CPU type.  |
|  1-1-2-3  |  Initialize system hardware.  |
|  1-1-3-1  |  Initialize chipset registers with initial POST values.  |
|  1-1-3-2  |  Set in POST flag.  |
|  1-1-3-3  |  Initialize CPU registers.  |
|  1-1-4-1  |  Initialize cache to initial POST values.  |
|  1-1-4-3  |  Initialize I/O.  |
|  1-2-1-1  |  Initialize Power Management.  |
|  1-2-1-2  |  Load alternate registers with initial POST values.  |
|  1-2-1-3  |  Jump to UserPatch0.  |
|  1-2-2-1  |  Initialize keyboard controller.  |
|  1-2-2-3  |  BIOS ROM checksum.  |
|  1-2-3-1  |  8254 timer initialization.  |
|  1-2-3-3  |  8237 DMA controller initialization.  |
|  1-2-4-1  |  Reset Programmable Interrupt Controller.  |
|  1-3-1-1  |  Test DRAM refresh.  |
|  1-3-1-3  |  Test 8742 Keyboard Controller.  |
|  1-3-2-1  |  Set ES segment to register to 4 GB.  |
|  1-3-3-1  |  28 Autosize DRAM.  |
|  1-3-3-3  |  Clear 512K base RAM.  |
|  1-3-4-1  |  Test 512 base address lines.  |
|  1-3-4-3  |  Test 512K base memory.  |
|  1-4-1-3  |  Test CPU bus-clock frequency.  |
|  1-4-2-4  |  Reinitialize the chipset.  |
|  1-4-3-1  |  Shadow system BIOS ROM.  |
|  1-4-3-2  |  Reinitialize the cache.  |
|  1-4-3-3  |  Autosize cache.  |
|  1-4-4-1  |  Configure advanced chipset registers.  |
|  1-4-4-2  |  Load alternate registers with CMOS values.  |
|  2-1-1-1  |  Set Initial CPU speed.  |
|  2-1-1-3  |  Initialize interrupt vectors.  |
|  2-1-2-1  |  Initialize BIOS interrupts.  |
|  2-1-2-3  |  Check ROM copyright notice.  |
|  2-1-2-4  |  Initialize manager for PCI Options ROMs.  |
|  2-1-3-1  |  Check video configuration against CMOS.  |
|  2-1-3-2  |  Initialize PCI bus and devices.  |
|  2-1-3-3  |  Initialize all video adapters in system.  |
|  2-1-4-1  |  Shadow video BIOS ROM.  |
|  2-1-4-3  |  Display copyright notice.  |
|  2-2-1-1  |  Display CPU type and speed.  |
|  2-2-1-3  |  Test keyboard.  |
|  2-2-2-1  |  Set key click if enabled.  |
|  2-2-2-3  |  56 Enable keyboard.  |
|  2-2-3-1  |  Test for unexpected interrupts.  |
|  2-2-3-3  |  Display prompt "Press F2 to enter SETUP".  |
|  2-2-4-1  |  Test RAM between 512 and 640k.  |
|  2-3-1-1  |  Test expanded memory.  |
|  2-3-1-3  |  Test extended memory address lines.  |
|  2-3-2-1  |  Jump to UserPatch1.  |
|  2-3-2-3  |  Configure advanced cache registers.  |
|  2-3-3-1  |  Enable external and CPU caches.  |
|  2-3-3-3  |  Display external cache size.  |
|  2-3-4-1  |  Display shadow message.  |
|  2-3-4-3  |  Display non-disposable segments.  |
|  2-4-1-1  |  Display error messages.  |
|  2-4-1-3  |  Check for configuration errors.  |
|  2-4-2-1  |  Test real-time clock.  |
|  2-4-2-3  |  Check for keyboard errors  |
|  2-4-4-1  |  Set up hardware interrupts vectors.  |
|  2-4-4-3  |  Test coprocessor if present.  |
|  3-1-1-1  |  Disable onboard I/O ports.  |
|  3-1-1-3  |  Detect and install external RS232 ports.  |
|  3-1-2-1  |  Detect and install external parallel ports.  |
|  3-1-2-3  |  Re-initialize onboard I/O ports.  |
|  3-1-3-1  |  Initialize BIOS Data Area.  |
|  3-1-3-3  |  Initialize Extended BIOS Data Area.  |
|  3-1-4-1  |  Initialize floppy controller.  |
|  3-2-1-1  |  Initialize hard-disk controller.  |
|  3-2-1-2  |  Initialize local-bus hard-disk controller.  |
|  3-2-1-3  |  Jump to UserPatch2.  |
|  3-2-2-1  |  Disable A20 address line.  |
|  3-2-2-3  |  Clear huge ES segment register.  |
|  3-2-3-1  |  Search for option ROMs.  |
|  3-2-3-3  |  Shadow option ROMs.  |
|  3-2-4-1  |  Set up Power Management.  |
|  3-2-4-3  |  Enable hardware interrupts.  |
|  3-3-1-1  |  Set time of day.  |
|  3-3-1-3  |  Check key lock.  |
|  3-3-3-1  |  Erase F2 prompt.  |
|  3-3-3-3  |  Scan for F2 key stroke.  |
|  3-3-4-1  |  Enter SETUP.  |
|  3-3-4-3  |  Clear in-POST flag.  |
|  3-4-1-1  |  Check for errors  |
|  3-4-1-3  |  POST done-prepare to boot operating system.  |
|  3-4-2-1  |  One beep.  |
|  3-4-2-3  |  Check password (optional).  |
|  3-4-3-1  |  Clear global descriptor table.  |
|  3-4-4-1  |  Clear parity checkers.  |
|  3-4-4-3  |  Clear screen (optional).  |
|  3-4-4-4  |  Check virus and backup reminders.  |
|  4-1-1-1  |  Try to boot with INT 19.  |
|  4-2-1-1  |  Interrupt handler error.  |
|  4-2-1-3  |  Unknown interrupt error.  |
|  4-2-2-1  |  Pending interrupt error.  |
|  4-2-2-3  |  Initialize option ROM error.  |
|  4-2-3-1  |  Shutdown error.  |
|  4-2-3-3  |  Extended Block Move.  |
|  4-2-4-1  |  Shutdown 10 error.  |
|  4-3-1-3  |  Initialize the chipset.  |
|  4-3-1-4  |  Initialize refresh counter.  |
|  4-3-2-1  |  Check for Forced Flash.  |
|  4-3-2-2  |  Check HW status of ROM.  |
|  4-3-2-3  |  BIOS ROM is OK.  |
|  4-3-2-4  |  Do a complete RAM test.  |
|  4-3-3-1  |  Do OEM initialization.  |
|  4-3-3-2  |  Initialize interrupt controller.  |
|  4-3-3-3  |  Read in bootstrap code.  |
|  4-3-3-4  |  Initialize all vectors.  |
|  4-3-4-1  |  Boot the Flash program.  |
|  4-3-4-2  |  Initialize the boot device.  |
|  4-3-4-3  |  Boot code was read OK.  |