# SelfConnect Plugin

Inter-terminal injection for Windows. Lets PKA agents find other terminal windows, inject text, read their output, and submit Claude Code prompts - enabling multi-terminal coordination.

## Key Functions

- `find_target(title_keyword) -> WindowTarget` - find a terminal by window title substring
- `send_string(target, text, char_delay=0.02)` - inject text character by character
- `submit_claude_input(hwnd)` - submit the current input in a Claude Code TUI
- `get_text_uia(hwnd) -> str` - read full terminal text via UIA accessibility tree

## Requirements

Windows only. Requires pywin32:

```powershell
pip install pywin32>=306
```

## Install

```powershell
pip install -r plugins/selfconnect/requirements.txt
```

Register in `plugins/registry.yaml`.
