# Vibe Coders Keyboard 🎹

A minimal macro keyboard configuration for AI-assisted coding workflows. This setup turns a compact 3-button + 1-knob USB macro keyboard into a dedicated vibe coding controller -- letting you trigger speech-to-text, undo actions, launch apps, and navigate with one hand while you keep the other on your mouse.

---

## Hardware

A **3×1 macro keyboard with 1 knob** (3 buttons in a single column, one rotary encoder).

Compatible hardware uses vendor/product IDs: `1189:8890`, `1189:8840`, or `1189:8842`.

> ⚠️ The keyboard must be connected via USB cable when programming it, even if it supports Bluetooth.

---

## Key Mappings

Configuration file: [`vibe_coder_keyboard_mapping.yaml`](vibe_coder_keyboard_mapping.yaml)

### Buttons

| Button | Shortcut | Action |
|--------|----------|--------|
| 1 (top) | `Ctrl + Option + R` | Open **[Whispr Flow](https://whisprflow.app/)** -- AI speech-to-text dictation |
| 2 (middle) | `Cmd + Z` | **Undo** -- delete last action |
| 3 (bottom) | `Cmd + Space` | Open **Spotlight / App Launcher** -- quickly launch apps or trigger additional speech-to-text workflows |

### Knob

| Action | Key | Effect |
|--------|-----|--------|
| Rotate left (CCW) | `←` Left Arrow | Move cursor left |
| Press down | `Enter` | Confirm / Enter |
| Rotate right (CW) | `→` Right Arrow | Move cursor right |

---

## Setup

### 1. Install the keyboard programming tool

This project uses [`ch57x-keyboard-tool`](https://github.com/kriomant/ch57x-keyboard-tool) to write the configuration to the keyboard.

**macOS (Homebrew):**
```sh
brew install rustup-init && rustup-init
cargo install ch57x-keyboard-tool
```

**Linux:**
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install ch57x-keyboard-tool
```

**Windows:** Download the [prebuilt release](https://github.com/kriomant/ch57x-keyboard-tool/releases) or install Rust via [rustup](https://rustup.rs/) and run `cargo install ch57x-keyboard-tool`. Also install [USBDK](https://github.com/daynix/UsbDk/releases).

### 2. Connect the keyboard

Plug the keyboard in via USB cable.

### 3. Validate the configuration

```sh
ch57x-keyboard-tool validate vibe_coder_keyboard_mapping.yaml
```

### 4. Upload the configuration

```sh
ch57x-keyboard-tool upload vibe_coder_keyboard_mapping.yaml
```

> On Linux, you may need `sudo` if you get a permissions error:
> ```sh
> sudo ch57x-keyboard-tool upload vibe_coder_keyboard_mapping.yaml
> ```

---

## Workflow

1. **Dictate code or text** -- press Button 1 (`Ctrl+Option+R`) to start Whispr Flow and speak your thoughts.
2. **Undo mistakes** -- press Button 2 (`Cmd+Z`) to undo the last action.
3. **Launch apps or use Spotlight speech input** -- press Button 3 (`Cmd+Space`) to open the app launcher and optionally use macOS dictation.
4. **Navigate** -- rotate the knob left/right to move your cursor, or press it to hit Enter.

---

## Configuration File

```yaml
orientation: normal

rows: 3
columns: 1
knobs: 1

layers:
  - buttons:
      - ["ctrl-opt-r"]
      - ["cmd-z"]
      - ["cmd-space"]
    knobs:
      - ccw: "left"
        press: "enter"
        cw: "right"
```

For full documentation on the configuration format and all supported key names, see [`README_Original.md`](README_Original.md) and [`example-mapping.yaml`](example-mapping.yaml).

---

## License

[MIT](LICENSE)
