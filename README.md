# Ixel

**Put your AI models to work together.**

Ixel is the all-in-one from [IxelAI](https://ixelai.com). One install gets you two tools and an app:

- **[Ixel MAT](https://github.com/OpenIxelAI/ixel-mat)** asks several models at once. They answer, grade each
  other's work without knowing whose it is, and a moderator writes the verdict. Use it in the terminal
  (`ixel`), in the app, or as a plugin for Claude Desktop, Claude Code, Codex and Cursor.
- **[Handoff](https://github.com/OpenIxelAI/Handoff-by-IxelAI)** gives your agents one task board to share.
  Say `handoff dispatch "codex review my changes, gemini make me a list of …"` and each agent gets its part,
  all running at once, with the results back on the board.
- **The Ixel app** opens from the Start Menu, Applications, or your app menu. Ask your models (with
  pictures, video or a voice note), see Handoff's board and your project's pull requests, reach your
  servers and the OpenClaw or Hermes agents on them (Machines, which used to be Ixel Console), and check
  and change your setup.

Everything runs on your computer, with the API keys, subscriptions and local models you already have.

## Install

Windows, in a normal PowerShell window (not "Run as administrator"):

```powershell
irm https://ixelai.com/install.ps1 | iex
```

macOS or Linux, in a terminal:

```sh
curl -fsSL https://ixelai.com/install.sh | sh
```

Then open a new window and run `ixel setup` to choose your models, and `handoff setup --write` in a
project's folder to connect Claude Code and Codex.

You need Windows 10 or 11, macOS 12 or newer, or Linux, plus Python 3.10 or newer and Git. On Windows (and
on a Mac with Homebrew) the installer offers to get them. You also need at least one AI: an API key, a
subscription CLI such as Claude Code or Codex, or a local model through Ollama or LM Studio.

The installer needs no administrator rights. It downloads each tool from GitHub and runs that tool's own
installer, and running it again updates everything. Read it first if you like:
[install.ps1](install.ps1) and [install.sh](install.sh) are the files ixelai.com serves.

### Just one tool?

Each tool also installs on its own. To add the other one later, run its line.

| | Windows | macOS or Linux |
|---|---|---|
| Ixel MAT, with the Ixel app | `irm https://ixelai.com/ixel-mat/install.ps1 \| iex` | `curl -fsSL https://ixelai.com/ixel-mat/install.sh \| sh` |
| Handoff | `irm https://ixelai.com/handoff/install.ps1 \| iex` | `curl -fsSL https://ixelai.com/handoff/install.sh \| sh` |

### Uninstall

Each tool's installer prints the line that removes it. To remove all of Ixel at once:

```powershell
# Windows
Remove-Item -Recurse -Force -ErrorAction SilentlyContinue "$env:LOCALAPPDATA\IxelMAT", "$env:LOCALAPPDATA\Handoff", "$HOME\.local\bin\ixel.cmd", "$HOME\.local\bin\handoff.exe", "$HOME\.local\bin\handoff.cmd", "$([Environment]::GetFolderPath('Programs'))\Ixel.lnk"
```

```sh
# macOS or Linux
rm -rf ~/.local/share/ixel-mat ~/.local/share/handoff ~/.local/bin/ixel ~/.local/bin/handoff \
  ~/Applications/Ixel.app ~/.local/share/applications/ixel.desktop
```

Your settings in `~/.config/ixel-mat`, and each project's `.handoff` board, stay until you delete them.

## Where it stands

- **The app** has Ask, Board, Machines, Health and Settings. Ask attaches pictures, video and sound, and
  `/handoff` hands out work. The Board shows Handoff's tasks and your project's pull requests on GitHub,
  Gitea or GitLab, and has an agent review or fix one. Machines replaces Ixel Console: in Machines, press
  **Import** to bring its machines over with the keys it pinned, then run `ixel-console uninstall`.
- **It's tested on Linux so far**, the one-line installers included; Windows and macOS runs are next. If
  one fails for you, please [open an issue](https://github.com/OpenIxelAI/Ixel/issues/new/choose) with
  the output.
- Under the hood, `ixel` and `handoff` stay separate commands, each in its own folder, so you can update or
  remove one without the other.

## Problems and ideas

[Open an issue](https://github.com/OpenIxelAI/Ixel/issues/new/choose) here for anything about Ixel,
including installing it. Security problems go privately to **openixel.ai@gmail.com**; see
[SECURITY.md](SECURITY.md).

## Working on Ixel

`install.ps1` and `install.sh` here are the same files as the ones at the root of the
[ixelai.com repository](https://github.com/OpenIxelAI/ixelai.com), which makes the per-tool copies from
them with `scripts/make-installers.py`. Change both together.

## License

[MIT](LICENSE)
