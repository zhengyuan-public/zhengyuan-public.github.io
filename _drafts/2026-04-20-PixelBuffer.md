---
comments: true
title: Pixel Buffer
date: 2026-04-20 12:00:00
image:
    path: /assets/img/images_alphawow/LuaPreview.png
math: true
categories: [Machine Learning, Reinforcement Learning]
tags: [machine-learning, reinforcement-learning]
---

### Install Lua 5.1 on macOS

```bash
$ brew tap keonly/homebrew-legacy-lua
$ brew install keonly/legacy-lua/lua@5.1

$ brew link lua@5.1

# Inside ~/.zshrc, create an alias for lua5.1
alias lua="lua5.1"
```

### VSCode Setup

Extensions

- `Lua` by `sumneko`
- `Wow API` by `Ketho`
- `Wow Bundle` by `Septh`

---

### Pixel Buffer with Lua 5.1

#### TOC file

A TOC file is a file with a `.toc` file extension that provides information about an AddOn for WoW when WoW loads the AddOn. An AddOn must have a TOC file to work.

`AlphaWowPixelBuffer.toc`

```text
## Interface: 30300
## Title: AlphaWowPixelBuffer
## Notes: Visual data stream for external recording and CV processing.
## Author: Zheng YUAN
## LoadOnDemand: 0
## DefaultState: Enabled
## Version: 0.1
## X-Protocol-Version: 1

AlphaWowPixelBuffer.lua
```

### Reference

- [World of Warcraft 3.3.5a API](https://wowwiki-archive.fandom.com/wiki/World_of_Warcraft_API)
