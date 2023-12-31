+++
author = "R. O."
title = "Pop!_OS First impressions"
date = "2023-11-15"
description = ""
tags = [
    "Linux",
    "Pop!_OS"
]
+++

Collected notes from switching from Windows 10 to [Pop!_OS](https://pop.system76.com/) as my _daily driver_ OS.

## Upsides

* Less distraction / Distraction-free environnment. No ads, no widgets with (boulevard) news forced upon you, no flashy login-screen pictures "Do you like what you see?", no trying to force Edge browser or other Microsoft tools upon you, no account-necessity, no automatic-updates that keep you from working
* vpn
* It's so distraction-free, it feels boring in the beginning.
* The build in app-store, the *Pop!\_Shop*, is a revelation, a liberation when you're coming from the Windows-world. Instead of searching on the net, landing on dubious websites, clicking through ads and finally installing an .exe-file that installs additional ad-ware if you're not careful - just open the *Pop!\_Shop* and browse! Knowingly that the store will direct you where you want to go without detours. *And* it also inspires curiosity, just browsing the offer, discover new stuff, trying it out, keeping it or deleting it again pressing just one button. The open-source world strangley feels empowering. You almost feel all the goodness that people put into it, when you one-click-download-and-install a new wonderful app from the open-source app store.
* All apps updated with one click. No manual downloading and installing for every app!
* Over-Amplification feature! I was wishing for such a feature for almost 6 years on Windows. It's built-in to the OS.
* Volume and Display brightness overlays are more usable and beautiful than on Windows
* Different levels for headphones and loudspeaker, like on Mac OS. Great :)
* Can include my cloud-storage right from the setup, without Nextcloud client software. Works nicely, although it does not download the files and therefore the desktop search does not find them. Replaced this with the Nextcloud client, now files can be searched and opened from the Desktop search.
* Also calendar/contacts are synched with one (!) click after this initial setup during installation. Great!
* I like the aesthetics and simplicity of Files (file viewer), it's more user friendly and usable than Explorer imho. Much faster and more intuitive search.
* All the default apps look great and work great
* Desktop search (=Launcher) much better than on Windows 
  * Stuff like built-in calculator is just neat.
* Everything seems faster and smoother. Comparable applications load up faster (eg. Signal, Firefox, OnlyOffice)
* Native NTFS support, read and write. All my ntfs drives work smoothly and without problems.
* Coming back from Sleep (Suspend), audio (webstream) will continue playing, while Windows 10 will loose the driver etc.
* I like the file browser better. It's simpler, but does the job better. With Windows 10 I always struggle because it does not display the file size or last modified value. I never really learned how this works predictably in Windows, while the GNOME Files thing just works out of the box!

## Downsides

* Display scale settings did not save out of the box. (Solution, some setting, *HiDPI Daemon*, had to be disabled first.
* 2-finger scrolling speed on touchpad can only be changed on the command line (!), no GUI for this. To be fair. The same touchpad scrolling was also not great under Windows.
  \-> Gnome-tweaks: https://support.system76.com/articles/touchpad
* 2-finger scrolling:
  * Natural scrolling setting does not work -> Probably because of my command line hacks, so this does not count.
  * Typing difficult, I always accidentally hit the Touchpad and my cursor flys off (despite having selected "Touchpad off while typing" in Settings.
* Waking up from sleep:
  * Serious bug when waking up from sleep (overnight): OS will come alive, but no new command works; No app can be started, not even reboot or shutdown works! Had to power off via the power button
  * When closing laptop and reopening: Display turned head over heals.
* Youtube-Video-Playback quality. No hardware acceleration (+ 60% Processor load) -> moves fans und drains battery unnecessarily and leaves one with bad video quality.
* Video/audio in general: lot of formats/codecs do not work out of the box. To be fair there is a support article about this. https://support.system76.com/articles/codecs/
  In the support article we learn:

  > Because of legal restrictions, this package cannot be installed automatically
* Bluetooth speaker nicht erkannt (Legami) | mit UE Boom funktionierts ohne Probleme. -> Evtl. codec umstellen für Legami?
* ~~LibreOffice deinstalliert, OnlyOffice installiert: Doppelklick auf Excel -> es passiert nichts mehr, nichtmal eine Meldung. Default application behaviour broken. Solution: Rightclick -> open with OnlyOffice. Couple of hours later it works, fine.~~
* ~~Switch between external and internal display (Laptop). Display scaling settings not saved?~~ Nope, it works!
* ~~Nextcloud Desktop client: Setting *Launch on System Startup* does not work with Flatpak version~~ -> Solution: Works with Debian version.
* Hibernate not possible (not speaking of automatic)
* ~~Weather widget: Show only Fahrenheit. Not possible to adjust (Celsius, or delete widget)~~ -> Adjusted to Celsius.
* Some notifications show up again after 3 days, even if they have been "clicked away" previously.
* Dock: Setting "Intelligently hide" does not work totally smoothly.
  * Mouse has to be "slammed" quite hard against the bottom border of the screen in order to make it appear. Gentle touching does not trigger it unfortunately.
  * Conceals items on desktop
* After around 1 month of daily use first system crash.
* After around 1.5 months of daily use sound device disappears. Reboot does not help. (See helpful stuff.)
* Recent total system crashes when listening to music from external harddrive with VLC and using TC Konnekt Audiointerface.
* Automatic suspend does not respect audio playback (Youtube)?

## Helpful stuff

- Problem with ProtonVPN and the killswitch (no internet): `protonvpn-cli ks --off\`\` This disables the killswitch


* Touchpad fix: `xinput --set-prop 13 'Synaptics Scrolling Distance' -500 -500` (Find out ID (13) of Touchpad with `xinput list`)
* Touchpad while typing fix: Users can simply open terminal and run the command below to test it out:

`syndaemon -i 0.8 -K -t -d`

The command will run the service silently in background. And the parameters are:

```
-i 0.8 tells to wait 0.8 second after last key press before re-enabling the touchpad.
-K makes it ignore Modifier+Key combos, such as Ctrl, Alt, and/or Shift + key combinations.
-t tells to disable tapping / scrolling only. Mouse movement is still possible while typing.
-d runs the command as daemon, in background.
```

[Source](https://ubuntuhandbook.org/index.php/2021/10/disable-touchpad-typing-option-not-working/)

* Sound not working anymore (10.2.2023)

https://support.system76.com/articles/audio/

And this command + reboot ([source](https://github.com/pipewire-debian/pipewire-debian/issues/49))

```
sudo apt reinstall pipewire pipewire-bin pipewire-pulse
systemctl --user --now enable pipewire pipewire-pulse
```

## Bugreports

* Settings > Accessibility: Enable "High contrast" mode. Disable "High contrast" mode -> Dark mode is activated involontarily. (Settings > Appearance: "Dark" selected. Previously was "Light".

# Distros evaluated before choosing Pop

Mint
Pop!\_OS
ElementaryOS
Fedora
Nobara

