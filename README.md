# GMailinator

Adds Gmail-esque keyboard shorcuts to Mail.app.  This is still very much a work
in progress.

Tested with Mail for macOS Big Sur.

## Supported Shortcuts

|  Key   | Action                         |
| :----: | ------------------------------ |
|   #    |  Delete                        |
|   /    |  Mailbox search                |
|   !    |  Toggle message as Junk        |
|   a    |  Reply All                     |
|   c    |  Compose new message           |
|  e, y  |  Archive                       |
|   f    |  Forward message               |
|   G    |  Go to the last message        |
|   g    |  Go to the first message       |
|   j    |  Go to next message/thread     |
|   k    |  Go to previous message/thread |
|   l    |  Move to folder (opens dialog) |
|   o    |  Open selected message         |
|   R    |  Get new mail (Refresh)        |
|   r    |  Reply                         |
|   s    |  Flag                          |
|   u    |  Mark message as read          |
|   U    |  Mark message as unread        |
|   v    |  View raw message dialog       |
|   z    |  Undo                          |

## How to install/update

1. Clone or download the repository from GitHub
2. Run `./install.sh`.
    * You can do this by opening a Terminal, drag the install script from Finder, and press return.
    * You will be prompted for authentication to allow the plugin by `spctl`.
3. In Mail, open Settings -> General -> Manage Plug-ins, and enable Gmailinator.
    * If you don’t see the "Manage Plug-ins" button, try quitting and re-opening Mail.
4. You will be prompted to restart Mail to activate the plugin.

## Allow usage in Big Sur

1. Codesign the bundle
```
codesign -s "<Replace with the identity>" -v -f GMailinator.mailbundle/
```
Alternatively, you can enable "Automatically manage signing" in Xcode:
  - Under the "Signing and Capabilities" tab (find this by clicking GMailinator root in sidebar)
  - Check "Automatically manage signing"
  - Change "Team" dropdown. You'll need to do some setup if you don't have a team
  - Now mail bundle will automatically be signed on Xcode build

2. Allow in system policy
```
spctl --add ~/Library/Mail/Bundles/GMailinator.mailbundle
```

## Credits

A lot of this was built with heavy use of of the
[BindDeleteKeyToArchive](https://github.com/benlenarts/BindDeleteKeyToArchive)
project by Ben Lenarts.  The Xcode project and interface skeleton were
all from that project, and for the most part, renamed.  I added the keybinding code.

A lot of the code is also either copied in whole, or modified from the
Nostalgy4Mail.app project, by [Hajo Nils
Krabbenhöft](https://github.com/fxtentacle/Nostalgy-4-Mail.app), and
subsequently by [Jelmer van der
Linde](https://github.com/jelmervdl/Nostalgy-4-Mail.app). I've added support
for ARC (turns out there were quite a few leaks), and prettied-up (imho) the
move-to-folder dialog.

Other references:

- [Rui Carmo's PyObjC vim keybinding script](http://taoofmac.com/space/blog/2011/08/13/2110)
