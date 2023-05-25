# gothic-animations-decompiled
This repository contains Gothic game animations in their raw form ASC.

- Files from GOG version fo the game
- Decompiled using Gothic Sourcerer 3.14
- Process might have introduced artifacts

## Why ?
- To remove this repetitive task for everyone in the future 
- To provide best possible "start-point" to work with animations
- Decompilation of Gothic animations is not 'symetrical' process and it's impossible to obtain original files, but we can get pretty close.
    - ASC files are often reused across different MDS definitions, as result we get multiple files with the same name. Those animations often contain only part of the original file. Without further processing, compiling them would result in parts of animation missing.

## Structure
I deviated a little from original folder structure, to keep individual animations as "packages".

### Humans

    Anims
    ├── Humans
    |    ├── Armor                                          #armors only
    |    ├── Body                                           #body meshes
    |    ├── InExtremo                                      #meshes/anims related to In Extremo
    |    ├── Humans                                         
    |    |    ├── HUMANS.MDS 
    |    |    └── (asc related to base humans.mds)
    |    ├── HUMANS_1HST1
    |    |    ├── HUMANS_1HST1.MDS 
    |    |    └── (new asc introduced by overlay)
    |    └── (other overlay packages)
    |

Since humans have so many overlays, they have own folder to keep everything tidy. Humans folder contains base animations for *HUMANS.MDS*, other folder contain mostly new animations that are used in that overlay, some may use animations from other overlays.

_For example **Humans_1hst2** reuses some animations from **Humans_1hst1**_
### Mobsi

    ├── Mobsi
    |    ├── Door_Wooden
    |    |    ├── DOOR_WOODEN.MDS 
    |    |    ├── DOOR_WOODEN.ASC
    |    |    └── DOOR_WOODEN_USE.ASC
    |    └── (other mobsi packages)...
    ├── Mobsi_Static
    |    ├── LADDER_2.ASC
    |    └──...

**Mobsi** folder contains animated interactive vobs, each in it's own folder with MDS + ASC Model and ASC Animation while in use. Some mobsi are just reskins and reuse asc animation (Door_* all use Door_Wooden_Use.ASC) so be sure to check mds, if you have all the files.

**Mobsi_Static** contains interactive vobs, that do not move by themselves, but npcs have interaction anims, like chair. I keep them at top of structure for easy access by level designers 
### Monster

    ├── Monster
    |    ├── Scavenger
    |    |    ├── SCAVENGER.MDS 
    |    |    └── (... scavenger asc files)
    |    ├── Orcbitter (Scavenger)                          # name in parenthesis suggests base animation set
    |    |    ├── ORCBITTER.MDS 
    |    |    └── (... new animations asc files)
    |    └── (other monster packages)...

Gothic often achieves monster variety with reskin trick - **Orcbitter** is just different skin for **Scavenger**, but since sounds need to be defined in mds script file, Orcbitter has own mds while reusing Scavenger asc files. This means, asc files in orcbitter folder are not enough to compile it by itself, name in parenthesis suggests which monster is base / has required files.
### Morph

    ├── Morph
    |    ├── Heads
    |    |    ├── HUM_HEAD_BALD
    |    |    |    ├── HUM_HEAD_BALD.MMS 
    |    |    |    ├── HUM_HEAD_BALD.ASC 
    |    |    |    ├── HUM_HEAD_BALD_EAT.ASC
    |    |    |    ├── HUM_HEAD_BALD_EMOTIONS.ASC
    |    |    |    └── HUM_HEAD_BALD_VISEME.ASC
    |    ├── Items
    |    ├── Vobs
Morph folder contains 3 subsections, that need not to be explained. Each of them contains 'package' for single morph mesh, which contains script, model and it's animations. Some meshes like heads reuse animations from other morph meshes with the same model.
