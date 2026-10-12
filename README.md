<p align="center">
  <a href="https://ixelai.com"><img src="https://ixelai.com/ixel-logo.png" alt="Ixel" width="200"></a>
</p>

# Ixel

**Put your AI models to work together.**

Ixel is the all-in-one from [IxelAI](https://ixelai.com). One install gets you:

- **The Ixel app:** everything in one window. Ask (several models answer and grade each other blind, and
  you get one verdict), the Board (Handoff's shared task board for your agents, with a model or chain picker,
  effort, cost per task, and Merge), the [Agent](#ixel-agent-beta) (beta),
  [Machines](https://ixelai.com/machines/) (your servers and the agents on them), Health and Settings.
- **[Ixel Agent (beta)](#ixel-agent-beta):** an agent in the Ixel app that can work on your computer for you.
  It asks before any change.
- **[Ixel MAT](https://ixelai.com/ixel-mat/):** ask several models at once. They grade each other's
  answers without knowing whose they are, and you get one verdict.
- **[Handoff](https://ixelai.com/handoff/):** one task board your agents share, so Claude,
  Codex and the rest hand work to each other instead of through you.

Everything runs on your computer, with the API keys, subscriptions and local models you already have.

**[ixelai.com](https://ixelai.com)** · [Docs](https://ixelai.com/docs/) · [Privacy](https://ixelai.com/docs/privacy/)

## What it is, and what it isn't

- It runs on your computer. There is no account, no server of ours and no telemetry. Your questions go from
  your computer to the AI companies you set up.
- It isn't a model or a hosted service. It uses your own API keys, subscriptions and local models.
- It acts when you ask or approve, not on its own around the clock. The Board runs a task only once you
  approve it, and never pushes. Merge goes into the branch you have checked out.
- When the panel agrees, that doesn't make the answer right. The models can share the same mistake.
- The Agent's commands are sandboxed, with no network and writes only in its folder, only on macOS and only
  while Computer access is off; even then they can read your files. Elsewhere, or with it on, they run as you,
  after you approve them.
- Handoff's sandbox that lets agents run commands is Linux only. On macOS and Windows its workers only edit
  files.

## Ixel Agent (beta)

The Ixel Agent is an agent in the Ixel app that can work on your computer for you.

- It asks before every edit, command, screenshot or opening something. If you choose Always allow for a
  command, that command runs without asking next time.
- You can give it a photo, video or file.
- The Computer access switch is off by default. While it is off, commands on macOS run sandboxed with no
  network, and the agent stays in the folder you picked. Turning it on lets the agent work across your home
  folder, run commands with the network, take screenshots and open apps. It still asks first.

Its code is in the [Ixel-MAT repository](https://github.com/OpenIxelAI/Ixel-MAT) with the rest of the app.
Read [AGENT_BETA.md](https://github.com/OpenIxelAI/Ixel-MAT/blob/main/AGENT_BETA.md) or the
[Agent docs](https://ixelai.com/docs/app/#agent).

## Install

Windows, in a normal PowerShell window (not "Run as administrator"):

```powershell
irm https://ixelai.com/install.ps1 | iex
```

macOS or Linux:

```sh
curl -fsSL https://ixelai.com/install.sh | sh
```

Then open a new terminal and run `ixel setup` to choose your models. You need Python 3.10 or newer and Git; the
installer offers to get them where it can. Running it again updates everything.

Want just one tool? Ixel MAT and Handoff each have their own one-line install on [ixelai.com](https://ixelai.com/#install).
To uninstall, see the [install guide](https://ixelai.com/docs/install/#uninstall). [install.ps1](install.ps1) and
[install.sh](install.sh) here are the exact files ixelai.com serves, if you'd like to read them first.

## Privacy

Ixel has no account, no server of its own and no telemetry: your questions go from your computer to the AI
companies you set up, and nowhere else. Some of them train on what you send:
[which ones, and how to keep your questions out](https://ixelai.com/docs/privacy/#training).

## Problems and ideas

[Open an issue](https://github.com/OpenIxelAI/Ixel/issues/new/choose) for anything about Ixel, installing it
included. Report security problems privately to **openixel.ai@proton.me**; see [SECURITY.md](SECURITY.md).

`install.ps1` and `install.sh` are byte for byte the ones at the root of the
[ixelai.com repository](https://github.com/OpenIxelAI/ixelai.com). Change them there: with this checkout
beside that one (or named with `--ixel`), its `python scripts/make-installers.py` copies them here, and `--check`
fails when they differ.

## Checks

`.github/workflows/install.yml` runs the real installers end to end on every pull request and push to main:
`install.sh` on Linux and macOS (everything, then Handoff alone with `sh install.sh handoff` in an empty home
folder) and `install.ps1` on Windows, in PowerShell 7 and in Windows PowerShell 5.1. Each run then checks, in a
new shell, that `ixel version` and `handoff version` work. It can also be run by hand from the Actions tab,
against another branch of Ixel MAT or Handoff.

## License

[MIT](LICENSE)
