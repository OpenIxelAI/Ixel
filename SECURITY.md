# Security

## Reporting a problem

Please report anything that looks like a security problem privately, by email to **openixel.ai@gmail.com**,
or with GitHub's **Report a vulnerability** button on this repository's **Security** tab if it's there.
Don't open a public issue. Problems in one tool can also go privately to that tool's repository:
[Ixel MAT](https://github.com/OpenIxelAI/ixel-mat) or [Handoff](https://github.com/OpenIxelAI/Handoff-by-IxelAI).

## What the installers do

`install.ps1` and `install.sh` are the files https://ixelai.com serves. They:

- need no administrator rights or `sudo`, and install only into your user folders;
- download Ixel MAT and Handoff with git from their GitHub repositories, over HTTPS;
- run each tool's own installer from that download, which makes a Python environment for it and puts its
  command on your PATH;
- offer to install what's missing, and ask first: Git and Python with winget on Windows, Apple's Command
  Line Tools and Homebrew's Python on a Mac.

They never ask for or store an API key. Each tool keeps your keys on your computer; see its own
SECURITY.md for how.

## What must never be committed here

This repository is public. Never commit API keys, tokens, `.env` files, private keys, personal email
addresses, phone numbers, home addresses, or screenshots and recordings that show any of them.
