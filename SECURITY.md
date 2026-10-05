# Security

## Reporting a problem

Please report anything that looks like a security problem privately, by email to **openixel.ai@proton.me**,
or with GitHub's **Report a vulnerability** button on this repository's **Security** tab if it's there.
Don't open a public issue. Problems in one tool can also go privately to that tool's repository:
[Ixel MAT](https://github.com/OpenIxelAI/ixel-mat) or [Handoff](https://github.com/OpenIxelAI/Handoff-by-IxelAI).

## What the installers do

`install.ps1` and `install.sh` are the files https://ixelai.com serves. They:

- need no administrator rights or `sudo` themselves, and install only into your user folders. Getting a
  missing Git or Python may: winget can ask for an administrator's OK, and on Linux your package manager
  uses `sudo` (on Debian and Ubuntu, Python's `venv` module is a package of its own, `python3-venv`);
- download Ixel MAT and Handoff with git from their GitHub repositories, over HTTPS. If a tool's folder
  came from another address, they start it over from the one asked for, but never over changes of yours
  (changed or new files, commits not on its remote, a stash): then they stop and say so;
- run each tool's own installer from that download, which makes a Python environment for it, gets the
  Python libraries it needs from PyPI, and puts its command on your PATH: your user PATH on Windows, and
  bash's, zsh's or fish's startup file on a Mac or Linux. For any other shell, the installer prints the
  line to add;
- offer to install what's missing, and ask first: Git and Python with winget on Windows, Apple's Command
  Line Tools and Homebrew's Python on a Mac. They ask only when someone is there to answer; with no one to
  ask, they install nothing extra and say what's missing.

They never ask for or store an API key. Each tool keeps your keys on your computer; see its own
SECURITY.md for how.

## What must never be committed here

This repository is public. Never commit API keys, tokens, `.env` files, private keys, personal email
addresses, phone numbers, home addresses, or screenshots and recordings that show any of them.
