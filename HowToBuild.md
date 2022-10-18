
## How to build GitLink

GitLink has two buildable components: the documentation, and a shared library component which is loaded via LibraryLink.  This document covers only how to build and run the shared library component.

#### Prerequisites
* Version 11.1 or greater of Mathematica or Wolfram Desktop (earlier versions might work but have not been tested).
* A C++ compiler supporting the C++14 standard and the C Compiler Driver feature of the Wolfram Language.
 * Visual Studio 2015 or later is preferred under Windows.
 * Xcode bundled with a 10.9 or later SDK is preferred on Mac.
 * gcc 5.0 or above on Linux should work.
* A built version of libgit2 (0.26.x or 0.27.x). While it's possible to use a dynamic library build, we prefer to use the static library build, which requires a small change to the default libgit2 cmake files.

#### Building GitLink
* Open the file src/build.wl in the Wolfram system.
* Evaluate the first three cells.  Then determine the values of the `libDirs` and `includeDir`. Ensure that the built libgit2 and its header files can be found in these locations.
* Run the entire package.
* If there are build errors and you need to see the unedited output, uncomment the line(s) setting the `"ShellOutputFunction"` option.

#### Running GitLink
* Build GitLink.
* Quit and restart the kernel.
* Run ``PacletManager`PacletDirectoryAdd["<git clone dir>/GitLink"]``.
* Load the package using `Get` or `Needs`. E.g., ``Get["GitLink`"]``.
* When loading the package this way, the system may choose to try to load the unbuilt source documentation pages rather than any final built documentation pages. If you want to use the documentation while in this state, it may be easiest to simply run another copy of the Wolfram system where you can access the documentation.
* You can test that you're running the library you think you are, and the features which were used to compile libgit2, by evaluating `$GitLibraryInformation` and examining the results.
