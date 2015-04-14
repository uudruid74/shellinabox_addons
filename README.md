# shellinabox_addons

This is just a couple short utilities for doing a few cool things
with shellinabox.  This is set up using tmux or byobu to provide for
a persistent session that will survive browser reloading and such.

This gives you a couple features, such as being able to log in to
the same shell from another location (such as via ssh), controlling
which applications are accessible, and being able to lauch multiple
applications into the same virtual terminal window via html buttons.
Look at tmux's "sendkeys" if you want to have html buttons type
specific values rather than launch commands.

This works by having shellinabox run a backend script "installcmd"
that is in charge of what is actually run in the shellinabox window.
I have apache set to forward URLs to shellinabox so that port #s
are not required and everything can run under the default web port.
Apache proxy file and shellinabox start-up files are included.

Please see the Screenshot to see what's going on.  The shell window
and the html-embedded shell are connected.  Each has a "shell" and
"disk" tabs open.  These are opened by clicking the buttons on the
left of the shell.  If either switches to the same tab as the other,
then both screens update simultaneously until you switch to the other.

The backend is versioned (just in case) and so your URLs should be
of the format of ...

	/shell/?0.1&command
        ... version & command to run

The command to run must be configured in the installcmd backend which
is currently in /root/bin, but feel free to adjust the shellinabox
start-up to look for it elsewhere.


#	 * * *  WARNING * * * 			 * * * WARNING * * * 		#

SECURITY WARNING:  This was set up for a web-based installer that
assumes a single user with root access.  You should change this to
a specific user or pass userinformation along (.htaccess) through the
environment and have the back-end script use "su" to run the command
as the correct user.  Regular shells can be run with "login".  You'll
also want to change the "session" name from "Draven" to whatever the
user has logged in as.  

 *** Closing your browser does NOT close the session! ***


