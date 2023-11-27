# TwisterOS Setup For Rock 4SE
I write this tutorial for future me or fellow Rock Pi 4 SE members who will be here in the future

Using Twister OS Armbian 2.0.3.

Default Twister OS 2.0.3 is very hard to boot on SE, its DTB is different from 4B, i guess it causes the problem (i dunno).
https://forum.armbian.com/topic/27382-rock4-se-or-rock-pi-4-se-device-tree-overlays-do-not-look-correct/.
So our first target will be moved kernel to **Armbian_21.08.1_Rockpro64_buster_current_5.10.60** or older. 

-- i dunno why but kernel 21.05.4 from default twister OS img boot usually failed, freeze on armbian logo, or right after cursor appear 

**1. First boot**.

First boot is really pain in the ass, unplug power if ur board is freezed til it fully boot, after that press "resize storage" app, it will reboot and ye, enjoy the pain again (gud luck)

**2. Downgrade kernel**.

Open armbian-config -> system -> other -> press spacebar to select -> choose kernel (Armbian_21.08.1_Rockpro64_buster_current_5.10.60 or older), wait til it reboot and tada, boot success rate become 100%

**3. Freeze kernel**.

Open armbian-config -> system -> freeze, so u won't accident upgrade it again (it'll upgrade to newest version if u do "apt update/upgrade", i dunno why, but boot work fine so it's okay, i tried update without freeze and welcome back to step 1.)

**4. Update and upgrade**.

**BEFORE UPDATE**, u should remove 2 conflicted packaged "linux-libc-dev:armhf" and "libc6-dev:armhf", use:

sudo apt remove linux-libc-dev:armhf && libc6-dev:armhf

Now everything work fine ! i guess (3.5mm jack doesn't work, bluetooth audio is broken).
I know nothing about linux so if anything go wrong pls explain to me. Thanks for reading 

**Update 1:** Don't use playonlinux to install **box86**, it will delete whole OS app, another stuff is okay.

**Update 2:** Fix 3.5 audio jack (source: https://forum.armbian.com/topic/13707-rockpi4b-no-audio-from-35mm-jack/#comment-99217) (bluetooth audio is still broken)
  armbian-config -> system -> hardware -> toggle rk3328-i2c0 -> restart
  terminal time:
  amixer set 'Right Headphone Mixer Right DAC' on
  amixer set 'Left Headphone Mixer Left DAC' on
