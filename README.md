# Ixel

**Put your AI models to work together.**

Ixel is the all-in-one from [IxelAI](https://ixelai.com). One install gets you two tools and an app:

- **[Ixel MAT](https://github.com/OpenIxelAI/ixel-mat)** asks several models at once. They answer, grade each
  other's work without knowing whose it is, and a moderator writes the verdict. Use it in the terminal
  (`ixel`), in the app, or as a plugin for Claude Desktop, Claude Code, Codex and Cursor.
- **[Handoff](https://github.com/OpenIxelAI/Handoff-by-IxelAI)** gives your agents one task board to share.
  Say `handoff dispatch "codex review my changes, gemini make me a list of …"` and each agent gets its part,
  all running at once, with the results back on the board. Claude Code and Codex change files on a branch
  of their own; answers, reviews and pictures come from the models you set up in Ixel MAT.
- **The Ixel app** opens from the Start Menu, Applications (in your home folder), or your app menu. Ask your models (with
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

Then, in a new terminal window, run `ixel setup` to choose your models, and `handoff setup --write` in a
project's folder to connect Claude Code and Codex. On a Mac or Linux, the installers add `~/.local/bin` to
your PATH for bash, zsh and fish, and a new window picks that up. With another shell, the installer prints
the line to add to your startup file instead (for sh, dash or ksh, `export PATH="$HOME/.local/bin:$PATH"`
in `~/.profile`, then log out and back in).

You need Windows 10 or 11, macOS 12 or newer, or Linux, plus Python 3.10 or newer and Git. On Windows (and
on a Mac with Homebrew) the installer offers to get them. On Debian and Ubuntu, Python's `venv` module is a
package of its own (`sudo apt install python3-venv`); the installer says so if it's missing. You also need
at least one AI: an API key, a subscription CLI such as Claude Code or Codex, or a local model through
Ollama or LM Studio.

The installer itself needs no administrator rights (getting Git or Python may: winget can ask for an
administrator's OK, and on Linux your package manager uses `sudo`). It downloads each tool from GitHub,
runs that tool's own installer (which gets the Python libraries it needs from PyPI), and running it again
updates everything. If a tool's folder came from another address (a fork you installed before), running
it again starts that folder over from the address you asked for, unless it holds changes of yours: then
it stops and tells you, so you can move them first. Read the installers first if you like:
[install.ps1](install.ps1) and [install.sh](install.sh) are the files ixelai.com serves.

### Just one tool?

Each tool also installs on its own. To add the other one later, run its line.

| | Windows | macOS or Linux |
|---|---|---|
| Ixel MAT, with the Ixel app | `irm https://ixelai.com/ixel-mat/install.ps1 \| iex` | `curl -fsSL https://ixelai.com/ixel-mat/install.sh \| sh` |
| Handoff | `irm https://ixelai.com/handoff/install.ps1 \| iex` | `curl -fsSL https://ixelai.com/handoff/install.sh \| sh` |

### Uninstall

Each tool's installer prints the line that removes it. To remove all of Ixel at once, first run
`handoff setup --remove`, which takes out what `handoff setup` added to your apps. Then run the lines below.
If you already had an app called Ixel, the installer named Ixel's own Ixel MAT instead (`Ixel MAT.lnk`,
`Ixel MAT.app`, `ixel-mat.desktop`), so put that name in place of Ixel's and leave yours.

```powershell
# Windows
Remove-Item -Recurse -Force -ErrorAction SilentlyContinue "$env:LOCALAPPDATA\IxelMAT", "$env:LOCALAPPDATA\Handoff", "$HOME\.local\bin\ixel.cmd", "$HOME\.local\bin\handoff.exe", "$HOME\.local\bin\handoff.cmd", "$([Environment]::GetFolderPath('Programs'))\Ixel.lnk"
```

```sh
# macOS or Linux
rm -rf ~/.local/share/ixel-mat ~/.local/share/handoff ~/.local/bin/ixel ~/.local/bin/handoff \
  ~/Applications/Ixel.app "${XDG_DATA_HOME:-$HOME/.local/share}/applications/ixel.desktop"
```

These stay until you delete them:

- your settings in `~/.config/ixel-mat`, and each project's `.handoff` board;
- Handoff's approval key, in `~/.config/handoff` on Linux, `~/Library/Application Support/Handoff` on a
  Mac and `%APPDATA%\Handoff` on Windows;
- the app window's browser data, if you used it: `~/.local/state/ixel-mat` on Linux,
  `~/Library/Application Support/IxelMAT` on a Mac (on Windows it's in the `IxelMAT` folder above);
- the PATH lines the installers added. On a Mac or Linux they're under `# Added by Ixel MAT installer`
  and `# Added by Handoff installer` in `~/.bashrc`, `~/.bash_profile` (Mac) or `~/.zshrc`, or in fish's
  `conf.d/ixel-mat.fish` and `conf.d/handoff.fish`. On Windows it's `%USERPROFILE%\.local\bin` in your
  user PATH.

## Where it stands

- **The app** has Ask, Board, Machines, Health and Settings. Ask attaches pictures, video and sound, and
  `/handoff` hands out work. The Board shows Handoff's tasks and your project's pull requests (on GitHub,
  GitLab or Codeberg, or your own Gitea, Forgejo or GitLab server), and has an agent review or fix one.
  Machines replaces Ixel Console: in Machines, press **Import** to bring its machines over with the keys
  it pinned, then run `ixel-console uninstall`.
- **It's tested on Linux so far**, the one-line installers included; Windows and macOS runs are next. If
  one fails for you, please [open an issue](https://github.com/OpenIxelAI/Ixel/issues/new/choose) with
  the output.
- Under the hood, `ixel` and `handoff` stay separate commands, each in its own folder, so you can update or
  remove one without the other.

## Privacy

Ixel has no account, no server of its own and no telemetry: your questions go from your computer to the AI
companies you set up, and nowhere else. What a company does with them after that is up to that company, not
Ixel. Some train their models on what you send, or let their staff read it, mostly depending on whether you
use an API key or a sign-in plan. [Which companies may train on it](https://ixelai.com/docs/privacy/#training)
says what each one does, with links to its own terms, and how to keep your questions out. The rest of
[that page](https://ixelai.com/docs/privacy/) lists everything Ixel sends and keeps.

## Problems and ideas

[Open an issue](https://github.com/OpenIxelAI/Ixel/issues/new/choose) here for anything about Ixel,
including installing it. Security problems go privately to **openixel.ai@proton.me**; see
[SECURITY.md](SECURITY.md).

## Working on Ixel

`install.ps1` and `install.sh` here are the same files as the ones at the root of the
[ixelai.com repository](https://github.com/OpenIxelAI/ixelai.com), which makes the per-tool copies from
them with `scripts/make-installers.py`. Change both together.

## License

[MIT](LICENSE)
