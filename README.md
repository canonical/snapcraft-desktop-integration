# snapcraft-desktop-integration
Desktop integration helpers

These helpers are integrated inside the toolkit runtime snap (like
gnome-46-2404, for example).

## Testing changes

To test changes on these files, you have to:

* create a fork, and then a new branch with your changes.
* download the *runtime* snapcraft project where you want to
  test them (for example, for gnome runtime, you should download
  the https://github.com/ubuntu/gnome-sdk repository and change
  to the desired *runtime* branch, the one without the -sdk
  suffix).
* edit the *runtime* snapcraft file to make it point to your fork/branch
  of *snapcraft-desktop-integration*
* build the new *runtime* snap
* install it in your system, or in the system where you want to test it

That's all: now, any snap installed in the testing system that uses the
*runtime* snap, will use the modified one.
