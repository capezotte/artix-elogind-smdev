# smdev + elogind seat management

This gets the [Artix implementation of smdev](https://aur.archlinux.org/packages/smdev) to notify elogind of devices which should be accessible to logged in, non-root users.

Usage example:

`./generate-uaccess /usr/lib/udev/rules.d/*.rules /etc/udev/rules.d/*.rules /home/user/some_package/src/*.rules | sudo tee /etc/smdev/add/40-elogind`

Thankfully, it seems (e)logind does not need libudev's tag enumeration to be notified of devices with uaccess, but rather, a helper program located in /usr/lib. By making smdev call this program, we can make access to many devices Just Work™ without the user having to add themselves to groups audio, video and input.

By editing the last line of the script, any seat manager with a similar arrangement can be made to work.
