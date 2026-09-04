# Keychron B1 Pro ZMK Configuration

Clean, stable configuration for the newer B1 Pro hardware variant tested on a B1P-K1 keyboard.

## Repository layout

```text
.
├── .github/
│   └── workflows/
│       └── build.yml
├── config/
│   ├── keychron_b1_us.keymap          # ACTIVE keymap: this is what gets built
│   ├── west.yml
│   └── boards/
│       └── shields/
│           └── b1_new_hw/
│               ├── Kconfig.defconfig
│               ├── Kconfig.shield
│               └── b1_new_hw.overlay
├── keymaps/
│   ├── default/
│   │   └── keychron_b1_us_stock.keymap
│   └── saved/
│       └── 2026-09-04_working_esc-caps-swap.keymap
├── 0001-esb-nrf-fix.patch
└── README.md
```

## What to edit

For ordinary layout work, edit only:

```text
config/keychron_b1_us.keymap
```

That file is the active keymap used by the build.

Use `keymaps/saved/` as a library for experiments, named versions, or layouts you may want later. When you want to activate one, copy its contents over `config/keychron_b1_us.keymap`.

Do not edit the `b1_new_hw` shield for normal keymap changes. It contains the verified hardware matrix definition for this newer B1 Pro variant.

## Baselines

`keymaps/default/keychron_b1_us_stock.keymap`
is a preserved copy of Keychron's stock B1 US keymap.

`keymaps/saved/2026-09-04_working_esc-caps-swap.keymap`
is the first verified working custom keymap. It is stock except that, in Windows mode, physical Esc sends Caps Lock and physical Caps sends Escape.

## Building

Push a change under `config/`, or run the workflow manually:

```text
Build Keychron B1 Pro
```

The artifact is:

```text
keychron-b1-pro-firmware
```

It contains:

- `zmk.uf2` — firmware to flash
- `zephyr.dts` — resolved Devicetree for diagnostics
- `.config` — resolved Kconfig for diagnostics

The workflow also checks the known-good B1P-K1 matrix transform before publishing the artifact.

## Flashing

Enter `NRF52BOOT`, then copy `zmk.uf2` to the drive.

The recessed hardware bootloader/reset button is the reliable recovery route if a custom keymap makes the normal bootloader shortcut inaccessible.

## Important: Keychron persistent keymap settings

Keychron's firmware can restore a persisted Launcher/VIA-style keymap after flashing. If a newly compiled keymap looks correct in source but old bindings remain on the keyboard, perform the Keychron factory reset:

```text
Fn + J + Z
```

Hold for about 3 seconds.

This was required after the first successful custom Esc/Caps remap.

## Hardware note

The newer tested B1P-K1 hardware does not work with the older published B1 matrix definition. The verified configuration in `b1_new_hw.overlay` uses `row2col` scanning and a measured 77-key transform. Keep that file as the stable hardware layer; ordinary customization should happen only in the active keymap.
