# Iosevka Comfy

IMAGES HERE: <https://protesilaos.com/emacs/iosevka-comfy-pictures>.

Customised build of the [Iosevka
typeface](https://github.com/be5invis/Iosevka), with a consistent
rounded style and overrides for almost all individual glyphs in both
roman (upright) and italic (slanted) variants.

+ Git repo on SourceHut: <https://git.sr.ht/~protesilaos/iosevka-comfy>
  - Mirrors:
    + GitHub: <https://github.com/protesilaos/iosevka-comfy>
    + GitLab: <https://gitlab.com/protesilaos/iosevka-comfy>
+ Mailing list: <https://lists.sr.ht/~protesilaos/general-issues>
+ Sample pictures: <https://protesilaos.com/emacs/iosevka-comfy-pictures>
+ Backronym: Iosevka (Could Only Modify a Font, Yes)

## Principles of the design

Iosevka Comfy optimises for inter-glyph and inter-style consistency
within the overarching constraint of usability at small point sizes.
The shapes are round and are designed in concert to both impose a
predictable rhythm and keep characters distinct from each other.

Roman and italic styles are made to look more consistent than the
default upstream Iosevka while retaining their unique features.  Unlike
the default Iosevka style, the upright glyphs do not have a mixture of
straight/blocky and curved or serified characters (special exceptions
notwithstanding).  While the italics do not have calligraphic tendencies
that greatly contrast with their counterparts.  The differences within
each style set and between the styles themselves are more nuanced.  The
intent is to make everything feel part of the same aesthetic.
Distinctions are drawn on the premise of contributing to the demands of
the design in light of usability, without ever calling attention to
themselves (as opposed to sporadic calligraphic glyphs amid an otherwise
austere presentation which seem to say "look how pretty I am!").

To achieve consistency between roman and italic styles we remove
elements of roundedness in the latter's glyphs to make them look a bit
sturdier.  Otherwise they would feel more rounded than their roman
counterparts given the added slant.  We do not want that added implicit
emphasis of extra roundedness because the slant is already sufficient:
to emphasise the emphasis is the kind of exaggeration that Iosevka Comfy
strives to eliminate.

## Variants

Iosevka Comfy comes in three sets of three.  These triplets follow the
naming scheme `NAME{,-fixed,-duo}`.  The base name is monospaced and
supports ligatures.  The "fixed" one is strictly monospaced so as to
work with all terminal emulators: it does not support ligatures.  And
the "duo" is quasi-proportionately spaced, while supporting ligatures.

1. The **compact, sans-serif** set:

   - `iosevka-comfy` is monospaced and supports ligatures.  Apart from
     ligatures, it allows certain special glyphs, such as arrows, to
     occupy more than one block.

   - `iosevka-comfy-fixed` is like `iosevka-comfy` albeit strictly
     monospaced and thus does not support ligatures.  All glyphs are
     exactly the same width.  Use this if you prefer it or if your
     application (e.g. terminal emulator) does not recognise
     `iosevka-comfy` as a monospaced font.

   - `iosevka-comfy-duo` is quasi-proportional and supports ligatures.  The
     naturally narrow glyphs, such as `i`, are allowed to occupy their
     natural width instead of one space.

2. The **compact, serif** set:

   - `iosevka-comfy-motion` is monospaced and supports ligatures.  It is
     like `iosevka-comfy` but with lots of small tweaks that add serifs
     and tailed ends to relevant glyphs.  Put simply, it is the serified
     counterpart of `iosevka-comfy`.

   - `iosevka-comfy-motion-fixed` is the serif equivalent of the
     aforementioned `iosevka-comfy-fixed`.

   - `iosevka-comfy-motion-duo` is the serif equivalent of
     `iosevka-comfy-duo`.

3. The **wide, sans-serif** set:

   - `iosevka-comfy-wide` is the same as `iosevka-comfy` except it is
     noticeably wider.  It also looks taller than `iosevka-comfy` even
     though both variants fit the same number of lines on a screen.

   - `iosevka-comfy-wide-fixed` is the "wide" counterpart of the
     `iosevka-comfy-fixed` family.

   - `iosevka-comfy-wide-duo` is the "wide" counterpart of the
     `iosevka-comfy-duo` family.

## Install on GNU/Linux

Unless you have some exotic system, in which case you know what you are
doing, you can install fonts for your local user by copying the `.ttf`
files or their directories in `~/.local/share/fonts/`.  For system-wide
installation, place them in `/usr/share/fonts/`.

Depending on your system, you may need to delete the `ttf` or
`ttf-unhinted` builds.  Though this is not strictly necessary, as the
system knows which one to pick.

When in doubt, install locally.

**Perform a shallow clone** of this repository to speed things up:

```sh
git clone --depth 1 https://git.sr.ht/~protesilaos/iosevka-comfy
```

## Build information

Iosevka Comfy is configured in accordance with the documentation of the
upstream project.  This practically means that we define our
`private-build-plans.toml`, install the `npm` dependencies, and then
build the `.ttf` files with something like the following for each
variant:

```sh
npm run build -- ttf::iosevka-comfy
```

Or this loop:

```sh
for i in iosevka-comfy{,-motion,-wide}{,-fixed,-duo} ; do npm run build -- ttf::$i ; done
```

The last update to Iosevka Comfy was done on 2022-09-14 using upstream
version `v16.2.0`, commit `b7a59ee4`.

Each file is provided as-is in the hope that it may prove useful, but
is otherwise intended only for my private use.
