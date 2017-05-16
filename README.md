# macOS Homebrew Sick Doctor Warning

![](http://i.imgur.com/fLKR6Pw.png)

A little script to announce [Homebrew](http://brew.sh/) doctor anomalies (`brew doctor) in the OS&thinsp;X Notification Center.

## Installation

```bash
brew install frdmn/formulas/homebrew-sick-doctor-warning
brew services start homebrew-sick-doctor-warning
```

To automate the execution we can use Homebrew's `service` subcommand to add it in our launchctl configuration. This will fire the script at login, at 10:01 and at 15:01. (If you want to change this, consider a [manual install](#user-content-manual-installation):

```bash
ln -sfv /usr/local/opt/homebrew-sick-doctor-warning/*.plist ~/Library/LaunchAgents
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.homebrew-sick-doctor-warning.plist
```

## Manual Installation

Updates are checked at login, 10:01 and 15:01. If you want to have the script run at other times, consider to manually install everything.

### Prerequisites

- [Homebrew](http://brew.sh/), of course.
- [terminal-notifier](https://github.com/alloy/terminal-notifier) is for sending the results of the script to the Notification Center.
Install with `brew install terminal-notifier`.

Download the script and place it in your environment path (how about `/usr/local/bin`?) and give it executable rights: `chmod +x /usr/local/bin/homebrew-sick-doctor-warning`.

### Automation

[Here](http://alvinalexander.com/mac-os-x/mac-osx-startup-crontab-launchd-jobs) is a little overview on writing launchd-entries.

1. Copy the example launch agent file into your user library: `cp opt/homebrew.sick-doctor-warning.plist ~/Library/LaunchAgents/homebrew.sick-doctor-warning.plist`
2. Modify the starting times and and other settings to your flavour
3. Start with `launchctl load ~/Library/LaunchAgents/homebrew.sick-doctor-warning.plist`. (You can halt the process by using _unload_ as launchctl command).

## Version

1.0.0

## License

[MIT](LICENSE)
