# snapcraft-desktop-integration
Desktop integration helpers

These helpers are integrated inside the toolkit contents snap (like
gnome-46-2404, for example).

## Testing changes

To test changes on these files, you have to:

* create a fork, and then a new branch with your changes.
* download the *contents* snapcraft project where you want to
  test them (for example, for gnome contents, you should download
  the https://github.com/ubuntu/gnome-sdk repository and change
  to the desired *contents* branch, the one without the -sdk
  postfix).
* edit the *contents* snapcraft file to make it point to your fork/branch
  of *snapcraft-desktop-integration*
* build the new *contents* snap
* install it in your system, or in the system where you want to test it

That's all: now, any snap installed in the testing system that uses the
*contents* snap, will use the modified one.
