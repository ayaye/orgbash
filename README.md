1. About
========

Installing Linux software can sometimes be rather tricky.
Especially if you do it only occasionally and have time to forget details.
Like me.

That's why I decided to write solutions in the form of bash scripts.
They are not perfect most of the time and may require small tweaks.
So I added a small library that allows to run these scripts step by step
with the ability to edit or undo each command.

This is what orgbash is: a bash script organizer.
Feel free to adapt it for yourself, create and share scripts.

orgbash is designed for Debian and `aptitude`,
but it is possible to adapt it for other distributions and package managers.


2. Installation
===============


2.1. `sudo` - allow user to run programs with superuser (root) privileges
-------------------------------------------------------------------------

Install `sudo` (root password required):

    su -l -c "apt install sudo" 

Add the current user ($USER) to the sudoers group:

    su -l -c "adduser $USER sudo" 

Re-login required for changes to be in effect!


2.2. `aptitude` - interface to Debian package manager (user password required)
------------------------------------------------------------------------------

    sudo apt install aptitude


2.3. `etckeeper` - version control system for /etc (user password required)
---------------------------------------------------------------------------

`etckeeper` will automatically install `git`.
I recommend installing `etckeeper`,
but if you don't need it, `git` is sufficient for `orgbash`.

    sudo aptitude install etckeeper


2.4. Clone `orgbash` repository (or fork it beforehand)
-------------------------------------------------------

    git clone https://github.com/ayaye/orgbash.git
    cd orgbash

`orgbash` is ready.


3. Usage
--------

    ./ob task [parameters...]

`Enter` or `Space` - confirm command
`Esc` - skip command
`e` - edit command. Use with care!


4. Additional details
---------------------

`orgbash` stores a log of task execution in `.timestamps/$TASK` subdirectory:
`log`    - full log.
`done`   - timestamp.
`backup` - directory with backup copies of changed files.


5. Example: Debian testing with LXDE in VirtualBOX
--------------------------------------------------


Install fresh Debian from `netinst` CD.
Don't set root password.
Enter username and password.
`sudo` will be installed and user will be added to sudoers.
Clear all `*` about software options.

  sudo apt install aptitude

  sudo aptitude install etckeeper

  git clone https://github.com/ayaye/orgbash

  cd orgbash

Switch to `testing` release:

  ./ob apt/change-release

After restart install `lxde` Desktop environment:

  ./ob lxde

After restart mount VirtualBox Guest Additions CD and run:

  ./ob vbox

After restart set up comfortable command line:

Pick some of:

  ./ob cli/bash
  ./ob cli/command-not-found
  ./ob cli/completion
  ./ob cli/man
  ./ob cli/network
  ./ob cli/zip

Or execute them all:

  ./ob cli

  ./ob mc
