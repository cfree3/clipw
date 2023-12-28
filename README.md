`clipw`: A simple CLI password manager.
=======================================

> *NOTE:* This repository is no longer maintained! Please consider an alternative such as
> [Bitwarden][bitwarden] instead.

About
-----
`clipw` began with a coversation between a coworker and myself regarding the CLI password
manager we wanted but that did not exist.

### What can it do?
`clipw` can store passwords, credit card numbers, or any other type of information. At its
heart, though, `clipw` is a _password_ manager -- and the fields it tracks reflect this
aim.

Each entry in the `clipw` store has a _key_ (title/ID), a _username_, and a _password_, but
you can adapt this to your needs. For example, to store information on a credit card, you
could lay out your info as follows:

* _key_: `visa` (type of card, or something you'll remember)
* _username_: `0000 0000 0000 0000` (credit card number)
* _password_: `000` (security code)

Dependencies
------------
Each of the following dependencies should be in your `$PATH`:

* `bash`
* `gpg`

It is assumed that the "standard" GNU utilities -- such as `cat` and `sed` -- will be in your
`$PATH`.

Optional Dependencies
---------------------
* `xclip` (direct copy to clipboard)
* `pwgen` (password generation)

Installing
----------
"Installation" is a misnomer with `clipw`: it's just a script. Place the actual `clipw` script
anywhere you'd like. (In _Using_ -- below -- it is assumed that `clipw` is in your `$PATH`).

By default, `clipw` will keep your password store in a subdirectory of `$XDG_CONFIG_HOME`;
however, there is built-in support for locating the password store alongside the script itself
(useful if you wish to carry around `clipw` on a USB drive). To activate this functionality,
simply rename `clipw` to `clipw-e` or create a symlink to the script called `clipw-e`. Done!

Using
-----
`clipw [FUNCTION] [ARGUMENTS]`

**Note:** You must execute `clipw init` _first_!

### Functions

* `clear KEY`

   Removes entry `KEY` from the password store.

* `destroy`

   Completely removes the password store. **You will lose _all_ your stored info!**

   If you destroy your password store, you must call `clipw init` before using
   `clipw` again.

* `get KEY [show]`

   Retrieves password for entry `KEY` from the store. If passed `show` (or if `xclip`
   is not available), the password will be printed to stdout.

* `help`

   Prints basic help information.

*  `init`

   Initializes the `clipw` password store; this must be called before using any other function.

* `list`

   Lists all store entry keys.

* `passwd`

   Changes the store (master) password.

* `put KEY [custom]`

   Adds a new entry to the password store; `KEY` is the "title" of the store entry
   (something like "facebook" or "gmail"). If passed the `custom` flag (or if `pwgen`
   is not in your path), then you will later be prompted for a password; otherwise,
   one will be generated for you.

* `where`

   Prints the location of the password store.

Limits
------
The simple implementation of `clipw` (including the fact that it is really nothing but a shell
script) means that its functionality is limited. For example, the format for the password
store (which is just an encrypted text file) means that usernames cannot contain the colon (:)
character.

License
-------
`clipw` is released under the MIT license (see `LICENSE.md`). Note that `clipw` is just a single
shell script; utilities called by the script are licensed by their respective owners.

DISCLAIMER
----------
I give no assurance of this utility's security, and I do not guarantee that it will not zap your
computer and fry your homedir. _Use at your own risk._

[bitwarden]: https://bitwarden.com/
