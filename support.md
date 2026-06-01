# HELM — Support & FAQ

Most questions are answered here. If you're still stuck, email **support@<yourdomain>**
with your OS version, Claude Desktop version, and what you saw.

## Getting started
**How do I install it?** Unzip `HELM-Windows-v1.0.zip`, double-click `HELM.exe`. A small
HELM window docks in the top-right and starts working. It also adds itself to startup.

**Nothing happened when I double-clicked it.** Windows SmartScreen may have blocked it
(unsigned app). Click "More info" → "Run anyway". You only do this once.

**Where's the window?** Top-right of your main monitor. If you closed it, run `HELM.exe`
again. To shrink it, click "Compact ▁"; click the strip to expand.

## It's not approving my prompts
1. **Is Claude Desktop the active/visible app?** The most reliable approvals happen on
   the session you're viewing. Background sessions are best-effort.
2. **Give it ~5 seconds.** It checks every few seconds, not instantly.
3. **Is it paused?** The dot is amber when paused. Click "Pause/Resume" to toggle.
4. **Run the self-test:** click "🧪 Self-Test". If "Claude window" or "UIA can see
   content" fails, close and reopen Claude Desktop, then HELM.
5. **Claude Desktop updated?** A major Claude update can shift the UI. Update HELM to the
   latest; if it persists, email us the Claude version.

## Safety
**Will it approve something destructive?** No. HELM never auto-approves deleting, sending
email, publishing, posting, or anything with payment — those always wait for you. It only
clicks buttons that are actually on screen.

**Does my data leave my computer?** No. HELM runs locally. No cloud account, no telemetry.
Telegram control is optional and uses your own bot.

## License / Pro
**How do I activate Pro?** After buying, you get a license key by email. Copy
`config.example.json` to `config.json` (in the HELM folder) and paste the key as
`"license_key"`. Pro activates within a couple of minutes — no restart needed.

**It still says FREE.** Make sure the file is named exactly `config.json` (not
`config.json.txt`), the key is in quotes, and you're online for the first verification.
Wait 2–3 minutes or restart HELM.

**Which AIs does it work with?** Claude Desktop on Windows only (incl. Claude Code
sessions). Not ChatGPT/Gemini.

**Can I use it on more than one PC?** Pro covers up to 3 of your machines.

## Telegram (Pro)
**How do I set up phone control?** Create a bot with @BotFather, put the token and your
numeric chat id in `config.json`. Get your chat id by messaging the bot then visiting
`https://api.telegram.org/bot<token>/getUpdates`. Then text `/status`, `/sessions`,
`/continue <name>`, `/pause`, `/resume`, `/selftest`.

## Billing
**Refunds?** 14-day no-questions refund. Email us.
**Is it a subscription?** No — Pro is a one-time purchase with free v1 updates.

## Uninstall
Delete the HELM autostart entry (Registry: `HKCU\...\CurrentVersion\Run\HELM`), remove the
desktop/Start-Menu shortcuts, and delete the HELM folder. Your data folder is
`%USERPROFILE%\.claude\supervisor`.
