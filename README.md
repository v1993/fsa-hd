# The Legend of Zelda: Four Swords Adventures HD texture pack

This is an HD texture project for [The Legend of Zelda: Four Swords Adventures](https://en.wikipedia.org/wiki/The_Legend_of_Zelda:_Four_Swords_Adventures) running on Dolphin emulator. It aims for modern look with [waifu2x-converter-cpp](https://github.com/DeadSix27/waifu2x-converter-cpp) used for texture upscaling. If you want unaltered graphical style, try [The Legend of Zelda Four Swords Adventures - Enhanced -](https://forums.dolphin-emu.org/Thread-the-legend-of-zelda-four-swords-adventures-enhanced) instead (not my project, it also aims at NTSC-U version instead of Europe). 

Features:

* 4x upscaling from original
* No major graphical issues
* A bunch of hard-to-fix minor graphical issues!

It have theoretically everything you can see on main screen upscaled, less obviously including:

* Single-player GBA screen contents
* Fonts (original font is used, but made much sharper) and other interface elements
* Intro movie
* Shadow battle arenas
* Shadow battle end screens (when SP GBA screen pops up)
* Tingle tower and all of its minigames
* * This includes GBA screen that pops up in horse racing for last player left

Not upscaled:

* Individual GBA screens. They aren't even handled by Dolphin rendering pipeline
* Anything from Navi/Tetra Trackers mode as it is not present in this version
* Probably some swords that get shown when you die or power up on single player GBA subscreen. Getting them all is incredibly tedious and they get so tiny screen time so it is not really worth it
* Unlikely, but probably some multiplayer-only exclusive features that I'm unaware of
* Less obviously, game demo movies (gameplay showcase). Those consist of 16k+ individual pictures to upscale because of how video decoder works and even upscaling original video gives poor results due to it being of lower quality than actual game

# Installation

**Important: This pack aims at EU version of FSA. Other ones are not tested.**

Put contents of this repository into `your_dolphin_directory/Load/Textures/G4SP01`.
On Linux it will be `$HOME/.local/shared/dolphin-emu/Load/Textures/G4SP01`.

Please note that this pack is designed for development versions of Dolphin emulator (created and tested on `5.0-11679`) and might not work with older versions.

To get pack working, you have to check "Load Custom Textures" in Dolphin -> Graphics -> Advanced. If you get poor performance, try checking "Prefetch Custom Textures", but this gives regular crashes for me. If it lags, "Prefetch Custom Textures" ends up with crashing, you're skilled enough and have a plenty of free memory, using ramdisk (or 10GB zram partition formatted as ext2) is a very good idea.

It is VERY recommended to play at least at 2x resolution as downscaling on native resolution makes many things appear ugly and text hard on eyes.

# Known problems

* Artifacts near trees. ARTIFACTS NEAR TREES. They're the bane of my existence. I got rid of most of them, but few are still there.
* Circles that show what Link is currently doing in Shadow Battle have white outline around Links. This is because rendering there omits alpha channel.
* If you look carefully at some things in game, you can notice that they have weird cuts. This is because spritesheets used by this game have differently sized textures and educated guessing was used to achieve both mostly consistent and artifact-free results.
* I tried for good 10 minutes and was not able to make boss of stage 8-1 open mouth while looking up. If it have animation for that, it is very rare and not upscaled.

# Notes

* `.dds` format is used for ground textures to reduce their size in-memory and speed loading them up. DXT5 is used for compression as no Linux tools seem to support newer formats. They still look fine (wasn't able to tell difference from PNG).
* Tools used:
* * Dolphin emulator for obvious purposes
  * [waifu2x-converter-cpp](https://github.com/DeadSix27/waifu2x-converter-cpp) for upscaling
  * GIMP for manual image editing
  * Imagemagick for batch image operations
  * Bash for basic scripting and Lua with [lgi](https://github.com/pavouk/lgi) for advanced one
  * Brain for educated guessing, project leading, file structuring, uploading to GitHub and writing this readme file