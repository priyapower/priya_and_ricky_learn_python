# Setup:

1. [Windows - Basic (dev env coming soon)](#windows-setup)
1. [Mac](#mac-setup)

## Windows Setup
_Following the Microsoft [tutorials](https://docs.microsoft.com/en-us/windows/python/beginners)_

1. PYTHON:
  - Following the Beginner version (Windows Store vs Python on Windows Subsytem for Linux - the dev environment will come later as he begins to work through more intermediate work)
  - Installed `Python 3.7` from Microsoft Store
  - Confirmed python and pip versions in PowerShell by using `Python --version` and `pip --version`
1. IDE:
  - Downloaded [VS Code](https://code.visualstudio.com/)
  - Open VS Code and click on "Extensions" (on left of screen) or use `CTRL + SHIFT + X`
  - Search for Python in the extensions menu and install
  - Open the Command Palette (`CTRL + SHIFT + P`), and type `Python: Select Interpreter` and select appropriate Python Environment (Python 3.7 Interpretter)
  - Confirm we see the correct interpretter in the bottom left (if we click on it we are taken to a section to add a new interpreter to the path)
  - Open the Terminal (```CTRL + ````)
  - In VS Code Terminal (which should be PowerShell by default), enter `python`
  - You should now see what version you are in as you enter the "Python world"
  - Type `print("Hello World")` and hit enter/return
  - We see a printout of "Hello World"
  - Type `exit()` or `quit()` or `CTRL + Z` to exit "Python World"
1. GIT:
  - Installed [git](https://git-scm.com/download/win) using Windows defaults

## Mac Setup
_Following the [docs](https://docs.python-guide.org/starting/install3/osx/)_

1. Out of Box
  - Mac OS X Comes with Python 2.7 out the box, tested in my terminal using `python --version` and got response `Python 2.7.16` (Okay for learning)
  - However, we want **Python 3** (better for development)
1. COMPILER:
  - We are first downloading GCC (GNU Compiler Collection - a compiler system)
  - First checked my system, using `xcode-select --version` gave me `xcode-select version 2373`
  - Using `gcc --version` gave me:
    ```terminal
    Configured with: --prefix=/Library/Developer/CommandLineTools/usr --with-gxx-include-dir=/Library/Developer/CommandLineTools/SDKs/MacOSX10.15.sdk/usr/include/c++/4.2.1
    Apple clang version 12.0.0 (clang-1200.0.32.27)
    Target: x86_64-apple-darwin19.6.0
    Thread model: posix
    InstalledDir: /Library/Developer/CommandLineTools/usr/bin
    ```
  - This means I have Command Line Tools from Apple which has GCC
1. PACKAGE MANAGER:
  - Install Homebrew - I already have it
  - I checked my system with `brew -v` or `brew --version` and got back `Homebrew 2.5.10...`
  - Opened `~/.profile` and added `export PATH="/usr/local/opt/python/libexec/bin:$PATH"` to the very bottom
  - Installed Python 3 with `brew install python`
  - Took about 2 minutes to fully install
  - Confirmed using `python3 --version`, I now see `Python 3.8.2`
1. PIP:
  - Check installation of pip and that it is pointing to the correct Python
  - Use `python3 -m pip --version` and got back `pip 19.2.3 from /Library/Developer/CommandLineTools/Library/Frameworks/Python3.framework/Versions/3.8/lib/python3.8/site-packages/pip (python 3.8)`
  - Success! (I can also use `pip3 --version`)
1. PIPENV:
  - [Pipenv](https://docs.python-guide.org/dev/virtualenvs/#virtualenvironments-ref) is a dependency manager for Python projects. If you’re familiar with Node.js’ npm or Ruby’s bundler, it is similar
  - Did `pip3 install --user pipenv`
  - `pipenv` is not available in my shell, so I may need to do some more work with this. Check out this [resource](https://stackoverflow.com/questions/46391721/pipenv-command-not-found)
