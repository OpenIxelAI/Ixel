<p align="center">
  <a href="https://ixelai.com"><img src="https://ixelai.com/ixel-logo.png" alt="Ixel" width="200"></a>
</p>

# Ixel

**Put your AI models to work together.**

Ixel is the all-in-one from [IxelAI](https://ixelai.com). One install gets you:

- **[Ixel MAT](https://ixelai.com/ixel-mat/):** ask several models at once. They grade each other's
  answers without knowing whose they are, and you get one verdict.
- **[Handoff](https://ixelai.com/handoff/):** one task board your agents share, so Claude,
  Codex and the rest hand work to each other instead of through you.
- **The Ixel app:** Ask, the Board, [Machines](https://ixelai.com/machines/) (your servers and the agents on
  them), Health and Settings in one window.

Everything runs on your computer, with the API keys, subscriptions and local models you already have.

**[ixelai.com](https://ixelai.com)** · [Docs](https://ixelai.com/docs/) · [Privacy](https://ixelai.com/docs/privacy/)

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
[ixelai.com repository](https://github.com/OpenIxelAI/ixelai.com). Change them there; its
`python scripts/make-installers.py` copies them here and `--check` fails when they differ.

## License

[MIT](LICENSE)
