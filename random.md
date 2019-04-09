Utterly random notes
=====

### TouchID for sudo
If you have a TouchID-capable Mac computer, you can use the fingerprint sensor to sudo. In order to do this, you'll have to edit your sudo file.

* Navigate to the sudo file - /etc/pam.d/sudo
* Add the following line to the top: `auth sufficient pam_tid.so`
* Save the file. Now whenever you `sudo`, your Mac computer will prompt you for your fingerprint instead of your password!