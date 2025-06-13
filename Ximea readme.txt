I have encountered problems with various versions of the drivers. This is a retrospective note, unfortunately without reference to specific version numbers in most cases.

v4.17.51 was latest version as of 21 Aug 2019. The one I’ve previously considered “latest” is v4.17.37

- Some versions definitely have problems where they sometimes hang looking for cameras (when I open the camera menu). I am not sure which versions, and I don’t know if I have tested their own viewer software to see if it has the same problem at the same time. In July 2022 I raised this with Ximea (https://desk.ximea.com/tickets/57565) and they say they are going to upgrade the version of libusb that is embedded in their dylib (which we think may fix this hanging issue)

- I think there is a reason (not sure if it’s the same?) why I have downgraded some machines to not-the-latest version of the ximea drivers.

- If I try and run two Ximea cameras from the same USB hub, I get all sorts of errors when I open the second camera (which seem to be only recoverable by rebooting). Even if I throttle their bandwidth, I seem to get intermittent errors. One camera ends up maxing out at 7fps, I’m not sure why, requiring a lot of unplugging (and rebooting?) to reset. I wonder if this might be an issue of drawing too much current from the hub or something?