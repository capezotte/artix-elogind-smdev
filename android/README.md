# Android USB script

This script reads a file called `androidtab`, which contains lines matching this ERE:

```
[0-9a-fA-F]{4}:[?0-9a-fA-F]{4}:.*
```

The first field colon-separated-field is a vendor ID, the second is a product ID (and `?` can match any character, as it does for shell scripts' `case` statement), the third is a comma-separate list of actions, of which so far `user` (enable user access), `adb` (create `/dev/android_adb` symlink) and `fastboot` (create `android_fastboot` symlink) are implemented. The default action of creating a `/dev/androidN` symlink is always run.

All lines not matching the above ERE are considered comments.

The included `androidtab` is generated from [M0rf30's android udev rules](https://github.com/M0Rf30/android-udev-rules/blob/master/51-android.rules), and is therefore licensed under the GNU General Public License.

You might want to replace `/etc/smdev/androidtab` and `chmod 666` inside `android.add` to suit your needs.
