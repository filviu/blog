---
title: BIOS Beep POST Codes
author: silviu
type: post
date: 2010-09-11T08:26:02+00:00
url: /2010/09/11/bios-beep-post-codes/
dsq_thread_id:
  - 329541769
categories:
  - old
tags:
  - temp_on

---
Ever found yourself standing next to a PC that won't boot and emits all kinds of short or long beeps. Me too. Here's a list of what these beeps _might_ mean.

Please note that because motherboard manufacturers often modify the code bought from these companies the beeps might mean something else.

### AWARD

<table border="1">
  <tr>
    <td>
      <strong>Beeps</strong>
    </td>
    
    <td>
      <strong>Error Message</strong>
    </td>
    
    <td>
      <strong>Description</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      1long, 2 short
    </td>
    
    <td>
      Video adapter error
    </td>
    
    <td>
      Either video adapter is bad or is not seated properly. Also, check to ensure the monitor cable is connected properly.
    </td>
  </tr>
  
  <tr>
    <td>
      Repeating (endless loop)
    </td>
    
    <td>
      Memory error
    </td>
    
    <td>
      Check for improperly seated or missing memory.
    </td>
  </tr>
  
  <tr>
    <td>
      1long, 3short
    </td>
    
    <td>
      No video card or bad video RAM
    </td>
    
    <td>
      Reseat or replace the video card.
    </td>
  </tr>
  
  <tr>
    <td>
      High frequency beeeps while running
    </td>
    
    <td>
      Overheated CPU
    </td>
    
    <td>
      Check the CPU fan for proper operation. Check the case for proper air flow.
    </td>
  </tr>
  
  <tr>
    <td>
      Repeating High/Low
    </td>
    
    <td>
      CPU
    </td>
    
    <td>
      Either the CPU is not seated properly or the CPU is damaged. May also be due to excess heat. Check the CPU fan or BIOS settings for proper fan speed.
    </td>
  </tr>
</table>

### AMI BIOS

<table border="1">
  <tr>
    <th>
      Beep Code
    </th>
    
    <th>
      Descriptions
    </th>
  </tr>
  
  <tr>
    <td>
      1 short
    </td>
    
    <td>
      DRAM refresh failure
    </td>
  </tr>
  
  <tr>
    <td>
      2 short
    </td>
    
    <td>
      Parity circuit failure
    </td>
  </tr>
  
  <tr>
    <td>
      3 short
    </td>
    
    <td>
      Base 64K RAM failure
    </td>
  </tr>
  
  <tr>
    <td>
      4 short
    </td>
    
    <td>
      System timer failure
    </td>
  </tr>
  
  <tr>
    <td>
      5 short
    </td>
    
    <td>
      Process failure
    </td>
  </tr>
  
  <tr>
    <td>
      6 short
    </td>
    
    <td>
      Keyboard controller Gate A20 error
    </td>
  </tr>
  
  <tr>
    <td>
      7 short
    </td>
    
    <td>
      Virtual mode exception error
    </td>
  </tr>
  
  <tr>
    <td>
      8 short
    </td>
    
    <td>
      Display memory Read/Write test failure
    </td>
  </tr>
  
  <tr>
    <td>
      9 short
    </td>
    
    <td>
      ROM BIOS checksum failure
    </td>
  </tr>
  
  <tr>
    <td>
      10 short
    </td>
    
    <td>
      CMOS shutdown Read/Write error
    </td>
  </tr>
  
  <tr>
    <td>
      11 short
    </td>
    
    <td>
      Cache Memory error
    </td>
  </tr>
  
  <tr>
    <td>
      1 long, 3 short
    </td>
    
    <td>
      Conventional/Extended memory failure
    </td>
  </tr>
  
  <tr>
    <td>
      1 long, 8 short
    </td>
    
    <td>
      Display/Retrace test failed
    </td>
  </tr>
</table>

### WINBIOS

<table border="1">
  <tr>
    <th>
      Beeps
    </th>
    
    <th>
      Error Message
    </th>
    
    <th>
      Description
    </th>
    
    <th>
      Resolution
    </th>
  </tr>
  
  <tr>
    <td>
      1
    </td>
    
    <td>
      Refresh Failure
    </td>
    
    <td>
      The memory refresh circuitry is faulty.
    </td>
    
    <td>
      Reseat the memory SIMMs. If the system still beeps, replace the memory.
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      Parity Error
    </td>
    
    <td>
      Parity error in the base memory (the first 64 KB block) of memory.
    </td>
    
    <td>
      Reseat the memory SIMMs. If the system still beeps, replace the memory.
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      Base 64 KB Memory Failure
    </td>
    
    <td>
      Memory failure in first 64 KB.
    </td>
    
    <td>
      Reseat the memory SIMMs. If the system still beeps, replace the memory.
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      Timer Not Operational
    </td>
    
    <td>
      A memory failure in the first 64 KB of memory, or Timer 1 is not functioning.
    </td>
    
    <td>
      The motherboard must be replaced.
    </td>
  </tr>
  
  <tr>
    <td>
      5
    </td>
    
    <td>
      Processor error 8042 - Gate A20 Failure
    </td>
    
    <td>
      The CPU generated an error.
    </td>
    
    <td>
      The motherboard must be replaced.
    </td>
  </tr>
  
  <tr>
    <td>
      6
    </td>
    
    <td>
      8042 - Gate A20 Failure Processor Exception Interrupt Error
    </td>
    
    <td>
      Cannot switch to protected mode.
    </td>
    
    <td>
      Try a different keyboard, or replace the keyboard fuse, if the keyboard has one.
    </td>
  </tr>
  
  <tr>
    <td>
      7
    </td>
    
    <td>
      Processor Exception Interrupt Error
    </td>
    
    <td>
      The CPU on the CPU Card generated an exception interrupt.
    </td>
    
    <td>
      The motherboard must be replaced.
    </td>
  </tr>
  
  <tr>
    <td>
      8
    </td>
    
    <td>
      Display Memory Read/Write Error
    </td>
    
    <td>
      The system video adapter is either missing or its memory is faulty. This is not a fatal error.
    </td>
    
    <td>
      There is a memory error on the video adapter. Replace the video adapter, or the RAM on the video adapter.
    </td>
  </tr>
  
  <tr>
    <td>
      9
    </td>
    
    <td>
      ROM Checksum Error
    </td>
    
    <td>
      The ROM checksum value does not match the value encoded in WINBIOS.
    </td>
    
    <td>
      The BIOS ROM chip is bad. The system probably needs a new BIOS ROM chip.
    </td>
  </tr>
  
  <tr>
    <td>
      10
    </td>
    
    <td>
      CMOS Shutdown Register Read/Write Error
    </td>
    
    <td>
      The shutdown register for CMOS RAM has failed.
    </td>
    
    <td>
      The motherboard must be replaced.
    </td>
  </tr>
  
  <tr>
    <td>
      11
    </td>
    
    <td>
      Cache memory bad - do not enable cache
    </td>
    
    <td>
      The cache memory test failed. Cache memory is disabled. Do not press Ctrl/Alt/Shift <+> to enable cache memory.
    </td>
    
    <td>
      The motherboard must be replaced.
    </td>
  </tr>
</table>

### IBM BIOS

The following are IBM BIOS Beep Codes that can occur. However because of the wide variety of models shipping with this BIOS the beep codes may vary.

<table border="1">
  <tr>
    <th>
      Beep Code
    </th>
    
    <th>
      Descriptions
    </th>
  </tr>
  
  <tr>
    <td>
      No Beeps
    </td>
    
    <td>
      No Power, Loose Card, or Short.
    </td>
  </tr>
  
  <tr>
    <td>
      1 Short Beep
    </td>
    
    <td>
      Normal POST, computer is ok.
    </td>
  </tr>
  
  <tr>
    <td>
      2 Short Beep
    </td>
    
    <td>
      POST error, review screen for error code.
    </td>
  </tr>
  
  <tr>
    <td>
      Continuous Beep
    </td>
    
    <td>
      No Power, Loose Card, or Short.
    </td>
  </tr>
  
  <tr>
    <td>
      Repeating Short Beep
    </td>
    
    <td>
      No Power, Loose Card, or Short.
    </td>
  </tr>
  
  <tr>
    <td>
      One Long and one Short Beep
    </td>
    
    <td>
      Motherboard issue.
    </td>
  </tr>
  
  <tr>
    <td>
      One Long and Two short Beeps
    </td>
    
    <td>
      Video (Mono/CGA Display Circuitry) issue.
    </td>
  </tr>
  
  <tr>
    <td>
      One Long and Three Short Beeps.
    </td>
    
    <td>
      Video (EGA) Display Circuitry.
    </td>
  </tr>
  
  <tr>
    <td>
      Three Long Beeps
    </td>
    
    <td>
      Keyboard / Keyboard card error.
    </td>
  </tr>
  
  <tr>
    <td>
      One Beep, Blank or Incorrect Display
    </td>
    
    <td>
      Video Display Circuitry.
    </td>
  </tr>
</table>

### MACINTOSH STARTUP TONES

<table border="1">
  <tr>
    <th>
      TONES
    </th>
    
    <th>
      ERROR
    </th>
  </tr>
  
  <tr>
    <td>
      Error Tone. (two sets of different tones)
    </td>
    
    <td>
      Problem with logic board or SCSI bus.
    </td>
  </tr>
  
  <tr>
    <td>
      Startup tone, drive spins, no video
    </td>
    
    <td>
      Problem with video controller.
    </td>
  </tr>
  
  <tr>
    <td>
      Powers on, no tone.
    </td>
    
    <td>
      Logic board problem.
    </td>
  </tr>
  
  <tr>
    <td>
      High Tone, four higher tones.
    </td>
    
    <td>
      Problem with SIMM.
    </td>
  </tr>
</table>

### PHOENIX BIOS

PHOENIX BIOS Q3.07 OR 4.X

<table border="1">
  <tr>
    <th>
      Beep Code
    </th>
    
    <th>
      Descriptions / What to Check
    </th>
  </tr>
  
  <tr>
    <td>
      1-1-1-3
    </td>
    
    <td>
      Verify Real Mode.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-2-1
    </td>
    
    <td>
      Get CPU type.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-2-3
    </td>
    
    <td>
      Initialize system hardware.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-3-1
    </td>
    
    <td>
      Initialize chipset registers with initial POST values.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-3-2
    </td>
    
    <td>
      Set in POST flag.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-3-3
    </td>
    
    <td>
      Initialize CPU registers.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-4-1
    </td>
    
    <td>
      Initialize cache to initial POST values.
    </td>
  </tr>
  
  <tr>
    <td>
      1-1-4-3
    </td>
    
    <td>
      Initialize I/O.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-1-1
    </td>
    
    <td>
      Initialize Power Management.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-1-2
    </td>
    
    <td>
      Load alternate registers with initial POST values.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-1-3
    </td>
    
    <td>
      Jump to UserPatch0.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-2-1
    </td>
    
    <td>
      Initialize keyboard controller.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-2-3
    </td>
    
    <td>
      BIOS ROM checksum.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-3-1
    </td>
    
    <td>
      8254 timer initialization.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-3-3
    </td>
    
    <td>
      8237 DMA controller initialization.
    </td>
  </tr>
  
  <tr>
    <td>
      1-2-4-1
    </td>
    
    <td>
      Reset Programmable Interrupt Controller.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-1-1
    </td>
    
    <td>
      Test DRAM refresh.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-1-3
    </td>
    
    <td>
      Test 8742 Keyboard Controller.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-2-1
    </td>
    
    <td>
      Set ES segment to register to 4 GB.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-3-1
    </td>
    
    <td>
      28 Autosize DRAM.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-3-3
    </td>
    
    <td>
      Clear 512K base RAM.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-4-1
    </td>
    
    <td>
      Test 512 base address lines.
    </td>
  </tr>
  
  <tr>
    <td>
      1-3-4-3
    </td>
    
    <td>
      Test 512K base memory.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-1-3
    </td>
    
    <td>
      Test CPU bus-clock frequency.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-2-4
    </td>
    
    <td>
      Reinitialize the chipset.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-3-1
    </td>
    
    <td>
      Shadow system BIOS ROM.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-3-2
    </td>
    
    <td>
      Reinitialize the cache.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-3-3
    </td>
    
    <td>
      Autosize cache.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-4-1
    </td>
    
    <td>
      Configure advanced chipset registers.
    </td>
  </tr>
  
  <tr>
    <td>
      1-4-4-2
    </td>
    
    <td>
      Load alternate registers with CMOS values.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-1-1
    </td>
    
    <td>
      Set Initial CPU speed.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-1-3
    </td>
    
    <td>
      Initialize interrupt vectors.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-2-1
    </td>
    
    <td>
      Initialize BIOS interrupts.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-2-3
    </td>
    
    <td>
      Check ROM copyright notice.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-2-4
    </td>
    
    <td>
      Initialize manager for PCI Options ROMs.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-3-1
    </td>
    
    <td>
      Check video configuration against CMOS.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-3-2
    </td>
    
    <td>
      Initialize PCI bus and devices.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-3-3
    </td>
    
    <td>
      Initialize all video adapters in system.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-4-1
    </td>
    
    <td>
      Shadow video BIOS ROM.
    </td>
  </tr>
  
  <tr>
    <td>
      2-1-4-3
    </td>
    
    <td>
      Display copyright notice.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-1-1
    </td>
    
    <td>
      Display CPU type and speed.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-1-3
    </td>
    
    <td>
      Test keyboard.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-2-1
    </td>
    
    <td>
      Set key click if enabled.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-2-3
    </td>
    
    <td>
      56 Enable keyboard.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-3-1
    </td>
    
    <td>
      Test for unexpected interrupts.
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-3-3
    </td>
    
    <td>
      Display prompt "Press F2 to enter SETUP".
    </td>
  </tr>
  
  <tr>
    <td>
      2-2-4-1
    </td>
    
    <td>
      Test RAM between 512 and 640k.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-1-1
    </td>
    
    <td>
      Test expanded memory.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-1-3
    </td>
    
    <td>
      Test extended memory address lines.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-2-1
    </td>
    
    <td>
      Jump to UserPatch1.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-2-3
    </td>
    
    <td>
      Configure advanced cache registers.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-3-1
    </td>
    
    <td>
      Enable external and CPU caches.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-3-3
    </td>
    
    <td>
      Display external cache size.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-4-1
    </td>
    
    <td>
      Display shadow message.
    </td>
  </tr>
  
  <tr>
    <td>
      2-3-4-3
    </td>
    
    <td>
      Display non-disposable segments.
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-1-1
    </td>
    
    <td>
      Display error messages.
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-1-3
    </td>
    
    <td>
      Check for configuration errors.
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-2-1
    </td>
    
    <td>
      Test real-time clock.
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-2-3
    </td>
    
    <td>
      Check for keyboard errors
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-4-1
    </td>
    
    <td>
      Set up hardware interrupts vectors.
    </td>
  </tr>
  
  <tr>
    <td>
      2-4-4-3
    </td>
    
    <td>
      Test coprocessor if present.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-1-1
    </td>
    
    <td>
      Disable onboard I/O ports.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-1-3
    </td>
    
    <td>
      Detect and install external RS232 ports.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-2-1
    </td>
    
    <td>
      Detect and install external parallel ports.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-2-3
    </td>
    
    <td>
      Re-initialize onboard I/O ports.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-3-1
    </td>
    
    <td>
      Initialize BIOS Data Area.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-3-3
    </td>
    
    <td>
      Initialize Extended BIOS Data Area.
    </td>
  </tr>
  
  <tr>
    <td>
      3-1-4-1
    </td>
    
    <td>
      Initialize floppy controller.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-1-1
    </td>
    
    <td>
      Initialize hard-disk controller.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-1-2
    </td>
    
    <td>
      Initialize local-bus hard-disk controller.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-1-3
    </td>
    
    <td>
      Jump to UserPatch2.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-2-1
    </td>
    
    <td>
      Disable A20 address line.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-2-3
    </td>
    
    <td>
      Clear huge ES segment register.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-3-1
    </td>
    
    <td>
      Search for option ROMs.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-3-3
    </td>
    
    <td>
      Shadow option ROMs.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-4-1
    </td>
    
    <td>
      Set up Power Management.
    </td>
  </tr>
  
  <tr>
    <td>
      3-2-4-3
    </td>
    
    <td>
      Enable hardware interrupts.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-1-1
    </td>
    
    <td>
      Set time of day.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-1-3
    </td>
    
    <td>
      Check key lock.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-3-1
    </td>
    
    <td>
      Erase F2 prompt.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-3-3
    </td>
    
    <td>
      Scan for F2 key stroke.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-4-1
    </td>
    
    <td>
      Enter SETUP.
    </td>
  </tr>
  
  <tr>
    <td>
      3-3-4-3
    </td>
    
    <td>
      Clear in-POST flag.
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-1-1
    </td>
    
    <td>
      Check for errors
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-1-3
    </td>
    
    <td>
      POST done-prepare to boot operating system.
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-2-1
    </td>
    
    <td>
      One beep.
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-2-3
    </td>
    
    <td>
      Check password (optional).
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-3-1
    </td>
    
    <td>
      Clear global descriptor table.
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-4-1
    </td>
    
    <td>
      Clear parity checkers.
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-4-3
    </td>
    
    <td>
      Clear screen (optional).
    </td>
  </tr>
  
  <tr>
    <td>
      3-4-4-4
    </td>
    
    <td>
      Check virus and backup reminders.
    </td>
  </tr>
  
  <tr>
    <td>
      4-1-1-1
    </td>
    
    <td>
      Try to boot with INT 19.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-1-1
    </td>
    
    <td>
      Interrupt handler error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-1-3
    </td>
    
    <td>
      Unknown interrupt error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-2-1
    </td>
    
    <td>
      Pending interrupt error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-2-3
    </td>
    
    <td>
      Initialize option ROM error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-3-1
    </td>
    
    <td>
      Shutdown error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-3-3
    </td>
    
    <td>
      Extended Block Move.
    </td>
  </tr>
  
  <tr>
    <td>
      4-2-4-1
    </td>
    
    <td>
      Shutdown 10 error.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-1-3
    </td>
    
    <td>
      Initialize the chipset.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-1-4
    </td>
    
    <td>
      Initialize refresh counter.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-2-1
    </td>
    
    <td>
      Check for Forced Flash.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-2-2
    </td>
    
    <td>
      Check HW status of ROM.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-2-3
    </td>
    
    <td>
      BIOS ROM is OK.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-2-4
    </td>
    
    <td>
      Do a complete RAM test.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-3-1
    </td>
    
    <td>
      Do OEM initialization.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-3-2
    </td>
    
    <td>
      Initialize interrupt controller.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-3-3
    </td>
    
    <td>
      Read in bootstrap code.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-3-4
    </td>
    
    <td>
      Initialize all vectors.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-4-1
    </td>
    
    <td>
      Boot the Flash program.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-4-2
    </td>
    
    <td>
      Initialize the boot device.
    </td>
  </tr>
  
  <tr>
    <td>
      4-3-4-3
    </td>
    
    <td>
      Boot code was read OK.
    </td>
  </tr>
</table>