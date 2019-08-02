# ABOUT

update_obmenu is a Perl script that creates and updates your Openbox menu.
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

# USAGE

    Usage: update_obmenu [-i theme] [-I <fallback theme>] -u|-n|-a [-p delay]
    -a   : Monitor application directories and autoupdate menu.
    -p   : Instead of kqueue use stat to poll for changes every 'delay' seconds.
    -u   : Update your Openbox menu.
    -n   : Create a new Openbox menu. Your old menu.xml will be overwritten!
    -i   : Use the given icon theme.
    -I   : Use the given fallback icon theme.

