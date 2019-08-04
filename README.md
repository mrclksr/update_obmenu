# ABOUT

update\_obmenu is a Perl script that creates and updates your Openbox menu.
It scans certain directories for desktop files, and adds new application
entries and submenus, including icons, to your Openbox menu.

# INSTALLATION
    % mkdir ~/bin
    % cp update_obmenu ~/bin
    % chmod u+x ~/bin/update_obmenu

# DEPENDENCIES

devel/p5-IO-KQueue

# RECOMMENDATION

Backup `~/.config/openbox/menu.xml`, and execute `update_obmenu -n` to
create a new `menu.xml`. Finally, add your modifications to this file, and
run `update_obmenu -u`.
For monitoring application directories on FreeBSD's unionfs use `-p`, as kqueue
isn't working reliable there. That is, after a few modifications on one of
the directories, no further events are returned by `kevent()`.

# EXCLUDE DESKTOP FILES

Add the paths of desktop files to the file `~/.config/update_obmenu.ignore`
to be ignored.

# USAGE

    Usage: update_obmenu [options] -n
           update_obmenu [options] -u
           update_obmenu [options] -a [-p delay]
    Options:
      Mandatory options:
      -a [-p delay] Monitor application directories and autoupdate menu. If
                    -p delay is given, poll for directory modifications every
                    'delay' seconds using stat(2). Otherwise kqueue(2) is used.
      -u            Update your Openbox menu.
      -n            Create a new Openbox menu. Your old menu.xml will be
                    overwritten!
      General options:
      -i theme      Use the given icon theme.
      -I fallback   Use the given fallback icon theme.
      -t xterm      Define terminal emulator for programs running in a terminal.

