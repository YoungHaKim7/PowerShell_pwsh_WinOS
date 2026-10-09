```pwsh
Welcome to the Python installation manager configuration helper.

********************************************************************************

Windows is not configured to allow paths longer than 260 characters.

Python and some other apps can exceed this limit, but it requires changing a
system-wide setting, which may need an administrator to approve, and will
require a reboot. Some packages may fail to install without long path support
enabled.
Update setting now? [y/N] y
The setting has been successfully updated, and will take effect after the next reboot.

********************************************************************************

The global shortcuts directory is not configured.

Configuring this enables commands like python3.14.exe to run from your
terminal, but is not needed for the python or py commands (for example, py
-V:3.14).

We can add the directory (C:\Users\ytok1\AppData\Local\Python\bin) to PATH now,
but you will need to restart your terminal to use it. The entry will be removed
if you run py uninstall --purge, or else you can remove it manually when
uninstalling Python.
Add commands directory to your PATH now? [y/N] y
PATH has been updated, and will take effect after opening a new terminal.

********************************************************************************

You do not have the latest Python runtime.

Install the current latest version of CPython? If not, you can use 'py install
default' later to install.

Install CPython now? [Y/n] y
Python install manager was successfully updated to 26.3.

Additional shebang configuration is now available. Please see
https://docs.python.org/using/windows#shebang-lines for more information.

********************************************************************************
The signature for https://www.python.org/ftp/python/index-windows.json was successfully verified.
Installing Python 3.14.8.
Downloading: ..................................................................✅
Extracting: ...................................................................✅
To see all available commands, run 'py help'
********************************************************************************

********************************************************************************

Configuration checks completed.

To run these checks again, launch Python install manager from your Start menu,
or py install --configure from the terminal.

********************************************************************************

Usage:
    py <regular Python options>
                         Launch the default runtime with specified options. This
                         is the equivalent of the python command.
    py -V:<TAG>          Launch runtime identified by <TAG>, which should
                         include the company name if not PythonCore. Regular
                         Python options may follow this option.
    py -3<VERSION>       Equivalent to -V:PythonCore\3<VERSION>. The version
                         must begin with the digit 3, platform overrides are
                         permitted, and regular Python options may follow. py -3
                         is the equivalent of the python3 command.
    py exec <any of the above>
                         Equivalent to any of the above launch options, and the
                         requested runtime will be installed if needed.
    py help [<CMD>]      Show help for Python installation manager commands
    py install <TAG>     Download new Python runtimes, or pass --update to
                         update existing installs.
    py list [<FILTER>]   Show installed Python runtimes, optionally filtering by
                         <FILTER>.
    py uninstall <TAG>   Remove one or more runtimes from your machine. Pass
                         --purge to clean up all runtimes and cached files.

Find additional information at https://docs.python.org/using/windows.

View online help? [y/N]

```
