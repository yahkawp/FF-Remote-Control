Welcome to the _Remote Control_ Firefox Extension.

It allows you to remote control a particular Firefox window with a TCP
connection (such as telnet or netcat).

Something like this:

    base@peter:~> telnet localhost 32000
    window.location="http:/www.google.com/"
    {"result":"http:/www.google.com/"}

You send any Javascript commands to firefox in a single line, and it sends
either a result or an error back JSON-encoded. As a convenience, a command of
`reload` is taken to be a shortcut for `window.location.reload()`

Using netcat/nc, you can therefore:

    echo reload | nc -q 1 localhost 32000

and the page will reload.

Project Status
==============

Alas, I find that other commitments leave me no time to work on this. Feel free
to fork, take over or suggest what I should do with it. If somebody wants to
take it over, feel free. Read
[Issue #16](https://github.com/pmorch/FF-Remote-Control/issues/16)

If a new project maintainer should emerge, I'm happy to put a link here to that
new maintainer.

Getting Started
===============

* Download and install the extension
* Select a Firefox window or tab you want to remote control
* Click the Remote Control toolbar button
    * If firebug is installed and active in that window, you can see logging in
      the Firebug console. (Firebug is not required, but the firebug console
      will be used if installed and active)
* Use telnet, nc or any other tool to send javascript commands to your Remote
  Controlled Firefox.

Preferences and Controlling Behavior
====================================

There are preferences for:

* Whether to listen for connections from localhost only (default = localhost
  only).
* Which TCP port number to listen on (default=32000)
* Whether to send remote commands to currently active tab (default=false)

In addition, by default when firefox is initially started, Remote Control is
_not_ active. You have to select a window/tab and start Remote Control by
clicking the toolbar button.

But it _is_ possible to start Remote Control automatically when Firefox starts
by setting the environment FIREFOX_\START\_REMOTE\_CONTROL=1. If that
environment variable is set _and_ the icon is present on the toolbar, it will
start when Firefox starts. The requirement for the icon to be present is to
avoid this extension being used for malicious purposes without the user
knowing.

Issues
======
Please report any problems to the
[Issue tracker](https://github.com/pmorch/FF-Remote-Control/issues)

License
=======

Remote Control is licensed under the
[GNU General Public License v2.0](http://www.gnu.org/licenses/gpl-2.0.html)
(See also [gpl-2.0.txt](gpl-2.0.txt))
