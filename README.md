[fish](https://fishshell.com/) - the friendly interactive shell [![Build Status](https://travis-ci.org/fish-shell/fish-shell.svg?branch=master)](https://travis-ci.org/fish-shell/fish-shell)
================================================

fish is a smart and user-friendly command line shell for macOS, Linux, and the rest of the family.
fish includes features like syntax highlighting, autosuggest-as-you-type, and fancy tab completions
that just work, with no configuration required.

For more on fish's design philosophy, see the [design document](https://fishshell.com/docs/current/design.html).

## Quick Start

fish generally works like other shells, like bash or zsh. A few important differences can be found at <https://fishshell.com/docs/current/tutorial.html> by searching for the magic phrase "unlike other shells".

Detailed user documentation is available by running `help` within fish, and also at <https://fishshell.com/docs/current/index.html>

You can quickly play with fish right in your browser by clicking the button below:

[![Try in browser](https://cdn.rawgit.com/rootnroll/library/assets/try.svg)](https://rootnroll.com/d/fish-shell/)

## Getting fish

### macOS

fish can be installed:

* using [Homebrew](http://brew.sh/): `brew install fish`
* using [MacPorts](https://www.macports.org/): `sudo port install fish`
* using the [installer from fishshell.com](https://fishshell.com/)
* as a [standalone app from fishshell.com](https://fishshell.com/)

### Packages for Linux

Packages for Debian, Fedora, openSUSE, and Red Hat Enterprise Linux/CentOS are available from the
[openSUSE Build
Service](https://software.opensuse.org/download.html?project=shells%3Afish&package=fish).

Packages for Ubuntu are available from the [fish
PPA](https://launchpad.net/~fish-shell/+archive/ubuntu/release-3), and can be installed using the
following commands:

```
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt-get update
sudo apt-get install fish
```

Instructions for other distributions may be found at [fishshell.com](https://fishshell.com).

### Windows

- On Windows 10, fish can be installed under the WSL Windows Subsystem for Linux with `sudo apt install fish` or from source with the instructions below.
- Fish can also be installed on all versions of Windows using [Cygwin](https://cygwin.com/) (from the **Shells** category).

### Building from source

If packages are not available for your platform, GPG-signed tarballs are available from
[fishshell.com](https://fishshell.com/) and [fish-shell on
GitHub](https://github.com/fish-shell/fish-shell/releases).  See the *Building* section for instructions.

## Running fish

Once installed, run `fish` from your current shell to try fish out!

### Dependencies

Running fish requires:

* curses or ncurses (preinstalled on most \*nix systems)
* some common \*nix system utilities (currently `mktemp`), in addition to the basic POSIX utilities (`cat`, `cut`, `dirname`, `ls`, `mkdir`, `mkfifo`, `rm`, `sort`, `tee`, `tr`, `uname` and `sed` at least, but the full coreutils plus find, sed and awk is preferred)
* gettext (library and `gettext` command), if compiled with translation support

The following optional features also have specific requirements:

* builtin commands that have the `--help` option or print usage messages require `ul` and either `nroff` or `mandoc` for display
* automated completion generation from manual pages requires Python (2.7+ or 3.3+) and possibly the
  `backports.lzma` module for Python 2.7
* the `fish_config` web configuration tool requires Python (2.7+ or 3.3 +) and a web browser
* system clipboard integration (with the default Ctrl-V and Ctrl-X bindings) require either the
  `xsel`, `xclip`, `wl-copy`/`wl-paste` or `pbcopy`/`pbpaste` utilities
* full completions for `yarn` and `npm` require the `all-the-package-names` NPM module

### Switching to fish

If you wish to use fish as your default shell, use the following command:

	chsh -s /usr/local/bin/fish

`chsh` will prompt you for your password and change your default shell. (Substitute `/usr/local/bin/fish` with whatever path fish was installed to, if it differs.) Log out, then log in again for the changes to take effect.

Use the following command if fish isn't already added to `/etc/shells` to permit fish to be your login shell:

    echo /usr/local/bin/fish | sudo tee -a /etc/shells

To switch your default shell back, you can run `chsh -s /bin/bash` (substituting `/bin/bash` with `/bin/tcsh` or `/bin/zsh` as appropriate).

## Building

### Dependencies

Compiling fish requires:

* a C++11 compiler (g++ 4.8 or later, or clang 3.3 or later)
* CMake (version 3.2 or later)
* a curses implementation such as ncurses (headers and libraries)
* PCRE2 (headers and libraries) - a copy is included with fish
* gettext (headers and libraries) - optional, for translation support

Sphinx is also optionally required to build the documentation from a cloned git repository.

### Building from source (all platforms) - Makefile generator

To install into `/usr/local`, run:

```bash
mkdir build; cd build
cmake ..
make
sudo make install
```

The install directory can be changed using the `-DCMAKE_INSTALL_PREFIX` parameter for `cmake`.

### Building from source (macOS) - Xcode

```bash
mkdir build; cd build
cmake .. -G Xcode
```

An Xcode project will now be available in the `build` subdirectory. You can open it with Xcode,
or run the following to build and install in `/usr/local`:

```bash
xcodebuild
xcodebuild -scheme install
```

The install directory can be changed using the `-DCMAKE_INSTALL_PREFIX` parameter for `cmake`.

### Help, it didn't build!

If fish reports that it could not find curses, try installing a curses development package and build again.

On Debian or Ubuntu you want:

    sudo apt-get install build-essential cmake ncurses-dev libncurses5-dev libpcre2-dev gettext

On RedHat, CentOS, or Amazon EC2:

    sudo yum install ncurses-devel

## Contributing Changes to the Code

See the [Guide for Developers](CONTRIBUTING.md).

## Contact Us

Questions, comments, rants and raves can be posted to the official fish mailing list at <https://lists.sourceforge.net/lists/listinfo/fish-users> or join us on our [gitter.im channel](https://gitter.im/fish-shell/fish-shell) or IRC channel [#fish at irc.oftc.net](https://webchat.oftc.net/?channels=fish). Or use the [fish tag on Stackoverflow](https://stackoverflow.com/questions/tagged/fish) for questions related to fish script and the [fish tag on Superuser](https://superuser.com/questions/tagged/fish) for all other questions (e.g., customizing colors, changing key bindings).

Found a bug? Have an awesome idea? Please [open an issue](https://github.com/fish-shell/fish-shell/issues/new).
