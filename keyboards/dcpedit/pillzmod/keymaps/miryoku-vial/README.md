## Credit/resources

Miryoku-like keymap for Kinesis Advantage 2 with Pillzmod (controller board replaced with WeAct BlackPill STM32F411 - 8Mhz XTAL)

-   Hardware: https://github.com/dcpedit/pillzmod
-   Original Vial layout keymap: https://github.com/dcpedit/vial-qmk/tree/pillzmod/keyboards/dcpedit/pillzmod
-   https://github.com/manna-harbour/miryoku
-   Miryoku keymap https://github.com/manna-harbour/miryoku_qmk/tree/miryoku/users/manna-harbour_miryoku

This is kludged together and does not have all the customization as Miryoku. It is just the standard Colemak DH layout with some small tweaks. Number row, F-keys and function/symbols keys (barring thumb clusters) of the kinesis are generally retained

### To build

1. Download dcpedit's vial-qmk fork and switch to the pillzmod branch and [setup qmk](https://docs.qmk.fm/newbs_getting_started):

```bash
git clone https://github.com/dcpedit/vial-qmk
cd vial-qmk
git checkout pillzmod
git submodule update --recursive --remote
```

2. Download this repository and add it to qmk's user config

```bash
git clone https://github.com/jcantosz/qmk_userspace.git
cd qmk_userspace
qmk config user.overlay_dir="$PWD"
```

3. Build the keymap

```bash
# switch back to the vial-qmk directory
cd vial-qmk
qmk compile -kb dcpedit/pillzmod -km miryoku-vial
```

4. Open QMK toolkit and flash the bin

### Changes from base Miryoku

-   Modifier keys are for Mac
-   Base Layer:
    -   Thumb keys primary/tap function swapped moved around. Hold functions location remains the same.
        -   Original ESC, SPC, TAB -- GAP -- ENT, BCK, DEL
        -   New: SPC, TAB, ESC -- GAP -- DEL, ENT, BCK
-   Media Layer:
    -   removed RGB and Bluetooth controls
    -   Right cluster changes
        -   Top row: N/A, N/A, Brightness Down, Brightness Up, N/A
        -   Middle row: unassigned leftmost key
        -   Bottom row: Desktop left, Webpage back, Webpage right, Desktop right
    -   Thumb cluster changes:
        -   Top row: left arrow, right arrow
-   Nav Layer:
    -   Right cluster changes
        -   Top row: unchanged
        -   Middle row: unchanged
        -   Bottom row: Alt+Left, Ctrl+E, Ctrl+A, Alt+Riight
        -   Bottom row + 1 (sym): Shift+Alt+Left, Shift+CMD+Right, Shift+Alt+Left, Shift+CMD+Right
    -   Thumb cluster changes:
        -   Top row: CMD+Up, N/A
        -   Middle row: CMD+Down
-   Mouse Layer
-   Thumb cluster changes: - Top row: Button 4, Button 5
-   All other layers the same

TODO pull in miryoku's defaults for mouse, tap, etc
