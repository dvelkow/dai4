# DAI

One command to launch N AI coding assistants side-by-side in a tmux session.

```
dai2                          dai4
┌───────────┬───────────┐     ┌──────┬──────┐
│  claude   │   codex   │     │claude│codex │
└───────────┴───────────┘     ├──────┼──────┤
                              │gemini│ omni │
dai6                          └──────┴──────┘
┌──────┬──────┬──────┐
│claude│codex │gemini│        dai8
├──────┼──────┼──────┤        ┌─────┬─────┬─────┬─────┐
│claude│codex │gemini│        │  1  │  2  │  3  │  4  │
└──────┴──────┴──────┘        ├─────┼─────┼─────┼─────┤
                              │  5  │  6  │  7  │  8  │
                              └─────┴─────┴─────┴─────┘
```

## How it works

The number in the command name sets pane count. Arguments set which AI tools to run. Tools cycle across panes if you provide fewer args than panes.

```bash
dai4                    # 4 panes, all claude
dai4 codex              # 4 panes, all codex
dai4 claude codex       # 4 panes: claude, codex, claude, codex
dai2 claude gemini      # 2 panes: claude, gemini
dai8 claude gemini codex omni   # 8 panes cycling through all four
dai6 codex              # 6 panes, all codex
```

Every session comes with:

- **Mouse support** — click to switch panes, scroll history
- **Clipboard integration** — drag to copy, right-click to paste (macOS)
- **Vi copy mode** — `v` to select, `y` to yank
- **50,000-line scrollback** per pane
- **256-color support**
- **Active pane highlighting** (green border)
- **Status bar** with dynamic DAI badge, date, and time

## Requirements

- [tmux](https://github.com/tmux/tmux) (`brew install tmux`)
- The AI CLI tools you want to use (`claude`, `gemini`, `codex`, `omni`, or any other)

## Install

```bash
git clone https://github.com/dvelkow/dai4.git
cd dai4

# Create symlinks for the pane counts you want
ln -s dai dai2
ln -s dai dai4
ln -s dai dai6
ln -s dai dai8

# Add to PATH
echo 'export PATH="'$(pwd)':$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Now `dai2`, `dai4`, `dai6`, `dai8` all work from anywhere.

## Customization

Edit the `tool_cmd()` function in `dai` to add flags or aliases for specific tools:

```bash
tool_cmd() {
    case "$1" in
        claude) echo "claude --some-flag" ;;
        *)      echo "$1" ;;
    esac
}
```

## License

MIT
