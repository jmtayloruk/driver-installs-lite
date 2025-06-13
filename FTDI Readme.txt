The FTDI driver has a 16ms latency on the path from peripheral to computer. I established this after corresponding with Scott Hannahs on the darwin-drivers mailing list and subsequently off-list. 

This is not actually a catastrophe for the Spim GUI, since the only really time-critical bit is the ‘transmit’ path in which we give the timing controller a time at which to send a trigger. However, general performance may be improved slightly if we can cut down on that latency a bit. As a result, I think the preferred install method should be a direct copy of the modified driver in the zip file in this directory. However, as of Apr 2015 all live systems (including several that have been using heart sync for years, and previous published data/papers) had been using the default driver with no major ill effects. I also gather that on OS X 10.10 it may not be possible to install the modified driver (see below), and therefore it may be necessary to revert to the old install method unless/until a solution can be found


As described in TN105 in this folder, it is possible to modify the driver to change that timer for cases where low latency is required (at the expense of less efficient use of the USB bus). The modified driver in the zip file in this directory has a latency of 1ms for the “FT232H” and “FTDI R Chip” devices. It’s possible to check that these have been loaded and configured properly using the IORegistryExplorer.

Scott says that on OS 10.10 this approach does not work, since the driver needs to be signed in order to be usable… but modification of the Info.plist invalidates the signing. He does not currently have a solution for this.



Note 1: if the FTDI driver is not installed then the Apple-supplied IOUSBFamily.kext will be used as the FTDI driver - and that has its own Info.plist. If the proper FTDI driver is installed, though, that seems to take precedence

Note 2: Scott seems to think it ought to be possible to use ioctl to modify the latency, but he has not had any success in doing that, and thinks it’s an Apple bug/missing feature (Bug report #18818013)

Note 3: If editing the driver, it may be necessary to fix ownership to root:wheel. Run “sudo kextutil -b com.FTDI.driver.FTDIUSBSerialDriver” to see if there are problems with it. This will also flag up code signing issues