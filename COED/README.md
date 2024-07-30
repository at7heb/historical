# The NOAA/ERL COED System

A group of us (see the paper for the names) did what I believe is first class work at NOAA to create the COED system.

## Introduction

The COED system was successful front-end computer network for NOAA's SDS-940 and its CDC-6600. As a front-end, it provided communications and editing capabilities.

The communications facilities were implemented first. At the time, NOAA used 3rd-party modems (meaning not rented from Mountain Bell, our telephone service provider) and DAAs (Data Access Arrangement), which were rented from Mountain Bell. Before COED, the 940 and the 6600 had separate banks of modems. COED allowed the modem banks to be combined. The 6600 asynchronous communications facilities were limited in support for (what was then considered) high speed terminal support -- 9600 bits/s. By offloading modem control and batching character data transfers, the COED system supported many high-speed computer terminals.

Acquiring the MODCOMP computers and other hardware used in COED was a lot of work. I had almost no involvement in that, but I remember Sky, Dave, and Mark spending enormous amounts of time to create the RFP, evaluate the responses, obtain the necessary funds, award the contract, execute and evaluate the system acceptance test, and then negotiate liquidated damages for the components that did not pass the acceptance test.

I remember that a line printer, essential for system test, went AWOL before it arrived. The manufacturer, rather than be held responsible for acceptance test delay or failure, shipped a printer to us via air-freight, which was probably outrageously expensive at the time. It seemed to the young and naive me that it almost took an act of congress to acquire the system hardware.

COED replaced the file sysem storage on the 940. The RAD, used for page swapping, remained with the 940. I'm not sure how much of the 6600's file system support was handled by COED.

## COED Capabilities Not Documented in the Paper

The Chrono-Log clock handling.

The Super Assembler (and link editor).

Auto restart after power failure.

### My COED involvement

I participated in the design meetins and decisions, as did all of us. I wrote MODCOMP code generators for a System Programm Language compiler, which we had obtained from the ONR in San Diego. I implemented the COED side COIN. I took over the 940's side of COIN when the developer left for another job. I worked with Dan DeChatelets to help him implement the 6600's side of COIN. I put together a system boot function, allowing one computer to supply the boot image to another computer.

During a significant time period, my work day started at 3 or 4 PM, when I went to the office to discuss progress, decisions, problems, and plans with my colleagues. I would leave for dinner and visiting friends, and return to NOAA at 8 or 10 PM, when I would prepare for a night of development, testing, and debugging. About midnight the operators would turn the machine room over to me, and I had full control of the CDC-6600, the SDS-940, and the MODCOMPs, booting them at will when I had updated a key operating system component. Around 5 or 5:30 AM I would start finishing up so that I could return the machine room to the operators. Sometimes I would make the decision to leave new software running; other times I left the operations software untouched. If I did make any changes, I would let the operators know and I also hang around until 8 or 9 AM, both to let the group know, and in case operations problems arose. I don't remember any, but perhaps my colleagues will.

I would try to get some sleep during the day, but my room in the poorly insulated house where I lived was on the south east corner of the house. It became unbearably hot in the summer. I remember telling Sky that I wasn't getting any sleep, and that I was about to return to an 8-5 schedule. A day or two later storms moved in and the daily high temperatures moderated. I then accused my colleagues of invoking deity/dieties to moderate the weather.

My contributions to COED ended in 1979, when I accepted an offer to work at Bell Labs. My involvement was drastically reduced in 1977 when I left Boulder to obtain study Electrical Engineering at the University of Minnesota.

I remember finding and fixing an intermittent 940 bug during my 1977-1978 Christmas vacation. Even though terminal communications was at the time provided by COED, there were both non-interrupt and interrupt level communications processing on the 940. All of you who have investigated such a bug know already that an operating system instruction had to be protected from interrupts during its execution. The trick was finding that instruction.

The bug affected a single user, and the procedure, before fixing the bug, to get that user's session back to normal, required starting DDT (the Dynamic Debugging Tool), loading the operating system's symbol table, mapping in the operating system's per-user state, and flipping a bit. It was easy, but required finding one of the few of us who knew what to do.

I believe this was the last bug corrected in the 940 operating system at NOAA in Boulder. After the correction, the system operators restarted the 940 on a monthly interval. Their procedures did not have a longer period for any of their actions. Barring power failures, restarts were not otherwise necessary.

The COED system operated with similar reliability.

### Repository Notes

This repository also includes a scanned image of the MODCOMP Classic marketing flyer. COED did not use the Classic. It had MODCOMP II and MODCOMP IV computers.

# Summary

COED was a lot of excellent work, executed over a reasonably short time by a small staff. We did not use formal development procedures. We did not have formal functional tests. The architects were the developers were the system testers were the operations staff.

We knew that message passing between COED and the SDS-940 and the CDC-6600, as well as within the COED network of 4 computers, would be a bottle neck, so we adopted a design philosophy of batching multiple operations into the COIN protocol for terminal control. The 940 COIN implementation would send the COIN operations message when either of these conditions was true:

* it was full
* it was "old" (by about ten milliseconds)--to keep performance high

## Afterwords

### Disclaimer

This represents my personal recollections of work on COED. I'm confident that I have made some mistakes. My colleagues may disagree, and I'll incorporate their corrections when and where appropriate.

### N. B

After I resigned from NOAA in 1979, I was employed by Bell Laboratories, as a software developer for the 5ESS. When I got to Bell Labs, I was amazed that acquiring a computer required getting management approval for the expenditure, getting a quote from the manufacturer for the proposed system, writing up a purchase order, which was also approved by the necessary management-probably two or three levels, waiting for delivery, and verifying delivery with purchasing so the invoice would be paid.

Bell Labs didn't use the RFP/proposal/evaluate/award/acceptance-test process. They didn't get cheated by their vendors.
