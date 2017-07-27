# OS X hotkeys

* `[⌘ CMD]+[⇧ SHIFT]+[.]` reveals hidden files in Finder and Open/Save dialogs

# Terminal

## Show emoji in `git log`

Install `less` via `brew` (need version 481 or later), set locale to UTF-8. [source](http://www.recursion.org/2016/6/19/displaying-emoji-in-git-log)

    brew install homebrew/dupes/less

# brew

## Updating java

When you encounter

    ==> Uninstalling Cask java
    ==> Running uninstall process for java; your password may be necessary
    ==> Removing launchctl service com.oracle.java.Helper-Tool
    ==> Not privileged to remove service.

Do following

    sudo launchctl remove com.oracle.java.Helper-Tool
    sudo launchctl remove com.oracle.java.Java-Updater

and update again.
