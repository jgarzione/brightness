brightness
==========

Command-line display brightness control for OS X.

This tool enables programmatic control of OS X screen brightness. You can set and retrieve hardware brightness settings with this utility.

Install with Homebrew
--------------------

```brew install brightness```

Install From Source
------------------

```shell
git clone https://github.com/nriley/brightness.git
cd brightness
make
sudo make install
```

OS X Version Support
------------------

Two versions are included.  Both require OS X 10.6 or later — but go back in the history and you’ll find versions that work with older OS X versions.

`brightness.c` uses documented APIs.  It works on internal laptop displays.  It doesn’t work on older Apple external LCDs.  I don’t know if it works on newer displays, such as Thunderbolt displays, because I don’t have any to test with.

`brightness.m` uses SPIs reverse-engineered from Displays System Preferences as of 2005.  It does not work as of OS X 10.9, always returning 0 brightness, but does work on OS X 10.6.  (I do not have any plans to update it nor any hardware with which to test, but contributions are welcome.)

Compilation instructions are in comments at the top of each file.

Usage Examples
-------

Set 100% brightness: ```brightness 1```

Set 50% brightness: ```brightness 0.5```

Show current settings: ```brightness -l```

````
% brightness
usage: brightness [-m|-d display] [-v] <brightness>
   or: brightness -l [-v]
% brightness -lv
display 0: main, active, awake, online, built-in, ID 0x4280a80
	resolution 1680 x 1050 pt (3360 x 2100 px) @ 0.0 Hz, origin (0, 0)
	physical size 286 x 179 mm
	IOKit flags 0x400003; IOKit display mode ID 0x80001002
	usable for desktop GUI, uses OpenGL acceleration
display 0: brightness 0.690430
% brightness -m 0.6
% brightness -l    
display 0: main, active, awake, online, built-in, ID 0x4280a80
display 0: brightness 0.599609
````
