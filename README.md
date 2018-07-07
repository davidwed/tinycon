# tinycon
TinyCon - A tiny console library, written for C++
--------------------------------------------------------------------------------
License:  BSD
Author:   Unix-Ninja | chris (at) unix-ninja (dot) com
Version:  0.6
Released: March 20, 2013
--------------------------------------------------------------------------------

Perhaps you are writing an application that requires user input to a console on
the commandline. There is the readline library from GNU, but it's license may
be a bit restrictive for your type of application. Instead, TinyCon is meant to
be a fairly light-weight and cross-platform input console library written in
C++, that is released under a less restrictive license. It is available for
Windows, OS X, and Linux. To use this library, simply include the tinycon.cpp
source file into your project. Then you can create an instance of the
"tinyConsole" class:

  tinyConsole tc;

Optionally, you can also specify a custom command prompt when you delcare your
instance:

  tinyConsole tc("prompt> ");

To run tinycon, just use the run() method.

  tc.run();

Tinycon will then sit and collect input from the user until the class registers
a quit state, (by default this occurs when the user types "exit");

To compile the demo with GCC, you can run the following:
$  g++ -o demo demo.cpp tinycon.cpp


MAKING IT USEFUL
-----------------

Tinycon becomes most useful when inheriting it in a custom class. Here, you have
the option to over-ride the trigger() and hotkeys() methods. By doing so, you
can define your own custom behaviour to how tinycon handles user input.


REFERENCE
----------

getLine([int mode] [, string mask])
    This method will collect user input until the return key is pressed. Once
    collected, it will return the input as a string.
    Optionally, you can specify the mode of operation as either M_LINE (default)
    or M_PASSWORD. Setting this to M_PASSWORD will supress echoing of the input
    characters as they are typed.
    A mask can also be supplied when using M_PASSWORD mode. If given, the mask
    will be echoed to the screen instead of the characters being typed.

hotkeys(char c)
    This method will trigger each time a key is pressed. You can override this
    method in an inherited class, and use it to evaluate the value of "c" in
    order to perform some action that matches your criteria.
    (Please note, the enter key does NOT trigger the hotkeys method).

run()
    This method starts collecting input from the user in an infinite loop. It
    will terminate when a "quit" state is registered.

setBuffer(string s)
    This method will copy the contents of the current line buffer with the
    contents of the given string "s".

setMaxHistory(int size)
    This method setst the size of the history buffer. You can use this to
    control the total number of commands that tinycon can remember. A user can
    use the up and down arrow keys to scroll through history on the commandline.

trigger(string input)
    When a user presses the enter key, their input is passed as a string to this
    method. You can override this method in an inherited class to process a
    user's input.

quit(boolean state)
    This method registered the quit state of the console. It can be set to true
    or false;


