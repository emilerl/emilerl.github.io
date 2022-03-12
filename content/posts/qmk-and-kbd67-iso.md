---
title: "QMK and KBD67 Lite R3 ISO"
date: 2022-03-12T08:32:01+01:00
draft: false
cover:
    image: "/kbd67-sushi.jpeg" 
    alt: "KBD67 Lite R3 ISO with Enjoy Sushi Keycaps" # alt text
    caption: "KBD67 Lite R3 ISO transparent orange with Enjoy Sushi Keycaps" # display caption under cover
---

I recently decided I wanted to build my keyboard based on the [KBDfans KBD67 Lite R3](https://kbdfans.com/products/kbd67lite) ISO kit. With my two other keyboards, the [Keychron Q1](https://www.keychron.com/products/keychron-q1) and [KBNordic Nordic60](https://kbnordic.eu/keyboard-parts/pcb/nordic60-hotswap-pcb-isoansi.html), I've built custom [QMK](https://qmk.fm) firmware as I want some extra features that are not possible with [VIA](https://www.caniusevia.com) alone. Things like [leader keys](https://thomasbaart.nl/2018/12/20/qmk-basics-leader-key/) and having easily having keymaps and macros in sync across different keyboards. I also really like the [Space Cadet](https://github.com/qmk/qmk_firmware/blob/master/docs/feature_space_cadet.md) feature, having the left and right shift keys act as left and right parenthesis if tapped and shift if held. Because I'm using an ISO layout, I have to re-map `LSPO_KEY`and `RSPC_KEY` to `KC_8` and `KC_9`, otherwise, I get `)` from the left shift and `=` from the right.

As the wired KBD67 has QMK support, I thought it would be a walk in the park to get my customizations compiled and flashed on my new board. It was not as easy as that though. I started by trying to compile the default keymap for `kbdfans/kbd67/mkiirgb_iso`, locally, in my fork of the QMK firmware. That resulted in a build error at the very end. The `check-size` at the end of the build process failed because the resulting firmware was too large: `24800/24576 (224 bytes over)`. I also tried to do the same with the QMK Configurator, just to ensure that there wasn't something locally that screwed up the build and sure enough, it failed there too.

I started to compare the `mkiirgb_iso` with the `mkiirgb/v3` as I was thinking that the PCBs are probably similar. The defines a size for the boot loader in the rules.mk file: `BOOTLOADER_SIZE = 6144`. I assumed this could probably be related.

As this was from the main branch and since I'm not all that familiar with the inner workings of QMK, I decided to file an [issue](https://github.com/qmk/qmk_firmware/issues/16565). I tagged the listed maintainer of the keyboard and waited a couple of days, but no response. As I wanted to get it working I asked in the QMK discord and I received the tip to look through the suggestions in the [Squeezing AVR]([https://docs.qmk.fm/#/squeezing_avr](https://docs.qmk.fm/#/squeezing_avr)) article.

Just enabling the link-time optimization by setting `LTO_ENABLE = yes`
in the `rules.mk` file helped me get it to a passing size.

The day after I saw that a solution for my issue was posted where some RGB animations were disabled and the `BOOTLOADER_SIZE = 6144` was set in the `rules.mk` for the `mkiirgb_iso`. I built the firmware with these changes and flashed it. Initially, everything seemed to work as it should, but I realized after a while that I couldn't soft reset the keyboard anymore by holding ESC while plugging in the USB cable. I had to use the physical reset button on the bottom of the PCB to be able to flash it again. I removed the boot loader size flags from `rules.mk` and re-compiled. After this, everything works as it should again.