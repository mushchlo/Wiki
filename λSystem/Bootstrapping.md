(This project uses [your fingies](https://snowbrains.com/wp-content/uploads/2014/06/hand.jpg) to build).

The process of bootstrapping is easy for all systems that [Justine Tunney's Cosmopolitan](https://github.com/jart/cosmopolitan) C library, check if you're supported on the [[Cosmopolitan support chart]]. 

# If your system has support on Cosmopolitan:

Just run the executable when you want to run the system *from the console*. We have no graphics support by default, but instead hack them in using userspace drivers in the host OS.

	`lambdasystem.exe`

# If your system doesn't have Cosmopolitan

If your system is not already supported by that library, try to add support if you know how! It's a very useful system to have working.

If that cannot be done, a bootstrapping executable can be made by compiling the C source code provided for a simple evaluator and encoding system. It will then create a faster binary, which it will then use to bootstrap the first stable version all the way to the latest stable version, then to the latest version.
(Expects \$CC to be in the environment)

#todo