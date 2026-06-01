# HELM — Setup

HELM supervises the Claude Desktop sessions on a Windows machine: it approves the
routine permission popups, escalates the risky ones, revives stalled sessions, and
keeps your AI fleet moving while you step away.

## Requirements
- **Windows 10/11**
- **Claude Desktop** installed and signed in
- **Python 3.10+**

## Install (one command)
```
pip install -r requirements.txt
python install.py
```
`install.py` checks dependencies, registers HELM to start at login, creates config
templates, and runs a self-test. When it finishes:
```
pythonw watchdog.py        # start it now (or just reboot)
```
A small HELM window docks in the top-right of your screen.

## Optional integrations
Both are optional — the core (approving popups) works without them.

- **Telegram control & escalation.** Create a bot with @BotFather, then put your token
  in `config.json`:
  ```json
  { "telegram_bot_token": "123456:ABC...", "telegram_chat_id": "<your numeric chat id>" }
  ```
  Get your chat id by messaging the bot and visiting
  `https://api.telegram.org/bot<token>/getUpdates`. Then from your phone you can text
  `/status`, `/fleet`, `/pause`, `/resume`, `/selftest`, `/recent`, `/goals`, `/help`.

- **Smart option choice (cheap model).** Put an OpenRouter (or OpenAI-compatible) key in
  `config.json` as `worker_api_key` to let HELM pick the best option on ambiguous
  questions. Without it, it uses its built-in rules.

## Config files
- `config.json` — tokens/keys (optional; see above)
- `auto_continue.txt` — title/session patterns HELM may auto-revive (empty = none)
- `goals.json` — declared outcomes, e.g. `[{"goal":"Keep the scraper running","match":"scraper","status":"active"}]`
- `STOP` — create this file to halt HELM; delete it to resume

## Safety
HELM never auto-approves irreversible actions (delete, send email, publish, pay) — those
always wait for you. It never spawns background `claude -p` processes. A self-test runs
every 20 minutes and alerts you (if Telegram is set) the moment any subsystem degrades.

## Uninstall
Delete the HELM autostart entry (`HKCU\Software\Microsoft\Windows\CurrentVersion\Run\ClaudeSupervisor`),
remove the desktop/Start-Menu `HELM` shortcuts, and delete this folder.
