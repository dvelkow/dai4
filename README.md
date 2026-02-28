# DAI4

A single command that launches 4 AI coding assistants side-by-side in a tmux session.

```
┌──────────────┬──────────────┐
│    Claude     │    Codex     │
├──────────────┼──────────────┤
│    Gemini     │     Omni     │
└──────────────┴──────────────┘
```

## What it does

Running `dai4` creates a tmux session with 4 equally-sized panes, each running a different AI CLI tool:

| Pane | AI Tool |
|------|---------|
| Top Left | `claude` |
| Bottom Left | `gemini` |
| Top Right | `codex` |
| Bottom Right | `omni` |

The session comes preconfigured with:

- **Mouse support** — click to switch panes, scroll to browse history
- **Clipboard integration** — drag to select and copy, right-click to paste (macOS)
- **Vi copy mode** — `v` to select, `y` to yank, `Ctrl+C` to copy
- **50,000-line scrollback** per pane
- **256-color support**
- **Active pane highlighting** (green border)
- **Status bar** with session badge, date, and time

## Requirements

- [tmux](https://github.com/tmux/tmux) (`brew install tmux`)
- The AI CLI tools you want to use: `claude`, `gemini`, `codex`, `omni`

## Install

```bash
# Clone the repo
git clone https://github.com/dvelkow/dai4.git

# Make it available globally
# Option 1: Add to PATH
echo 'export PATH="/path/to/dai4:$PATH"' >> ~/.zshrc
source ~/.zshrc

# Option 2: Symlink to a directory already in PATH
ln -s /path/to/dai4/dai4 /usr/local/bin/dai4
```

## Usage

```bash
dai4
```

That's it. Run it from any directory.

## License

MIT
