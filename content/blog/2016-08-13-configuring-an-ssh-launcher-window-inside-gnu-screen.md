---
title: "Binding an SSH launcher to a GNU Screen hotkey"
date: 2016-08-13
---

I have a confession to make. I use SSH to access servers.

I tell the sysadmins I teach to make changes to their servers using [configuration management](http://www.cfengine.com/), but:

(a) most clients I work with are just starting to use configuration management so we use SSH to access the systems that aren't under in configuration management yet, and

(b) I enjoy troubleshooting issues rather than just shooting my IT infrastructure in the head and instantiating a new one that might have the same issue. But this post isn't about immutable infrastructures. It's about SSHing to servers.

From "things that make me happy", I added two lines near the top of my [GNU Screen](https://www.gnu.org/software/screen/) config file, `.screenrc`:

```

# start ssh launcher loop

screen -t launcher /bin/sh -c 'while true; do echo -n "Hostname: "; read host;  screen -t $host ssh $host; clear; done'

# bind ctrl-K to "switch to window 0 which contains the SSH launcher"

bindkey "13" select 0

```

Now when I want to open a new session, I press `Ctrl-K` and enter the hostname, and GNU Screen will start a new window, titled with the name of the host, running an SSH session to that host.

It's the little things in life.

**Update**:

Now that I've used this for a day, I remembered the problem with this setup -- after you launch an ssh session, if you press the screen command key twice to go back to the previous window, you end up in the launcher window instead.

When I worked at EarthLink, I made a little shell script similar to this that I called with screen's "exec" command and did some gnarly input/output redirection where the script took my input and it's output was fed back to the screen as if it was user input and that contained the command to launch the ssh session. I didn't save it; looks like I'll have to reconstruct it.

Also, the latest version of GNU Screen is rather improved: you can renumber windows, split windows vertically, etc.

Yes, I know about tmux. I'm just used to screen. :)
