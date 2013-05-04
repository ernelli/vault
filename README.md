Vault
=====

vault.html is a personal secure password/information manager built as a single page webapp.

It is started by loading the page in a standards compliant webbrowser (Tested in firefox and google chrome).

Whenever the encrypted data is modified in the app, by saving the page in its current state to disk, a persistent copy can be kept.

The saved page only contains the encrypted data, e.g the vault, so it can be safely stored in an online storage such as github, preferably as a private repo or in dropbox, google drive etc.

Security
========

The stored data is encrypted using AES256 in CBC mode with the key generated from a passphrase. The key derivation from the passphrase is strenghened by using 4096 rounds of sha1, e.g similar to PBKDF2. The passphrase generates a 256 bit key and a 128 bit initialisation vector for the CBC. The passphrase is salted using the timestamp given by the system clock in ms encoded in hex. The salt is not considered a secret, it just prevents rainbow attacs and the birthday paradox.

The key strenghening only adds about 12 bits of entropy to the passphrase so a really long passhphrase is required to prevent brute force attacks to the encrypted data. Depending on CPU speed and javascript engine performance, longer or shorter key strenghening may be used.

Todo
====

- Remove the dependencies to jquery, e.g implement #id and .class selectors, as well as show, hide, val, text and append in embedded js.

- Add an options/configuration section where various settings can be tweaked such as key strenghening count etc.

- Fix keyboard shortcuts to trigger lock/unlock using ENTER and lock/clear vault using ESC.