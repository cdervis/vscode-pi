# pi Agent for VS Code

## Run your local pi coding agent directly inside VS Code.

<picture>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/cdervis/vscode-pi/main/media/cover-light.png">
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/cdervis/vscode-pi/main/media/cover-dark.png">
  <img alt="pi Agent for VS Code" src="https://raw.githubusercontent.com/cdervis/vscode-pi/main/media/cover-dark.png">
</picture>

<p align="center">
  <a href="https://marketplace.visualstudio.com/items?itemName=cdervis.vscode-pi"><img src="https://img.shields.io/badge/VS%20Code-Marketplace-0078D4?logo=visualstudiocode&logoColor=white"></a>
  <a href="https://open-vsx.org/extension/cdervis/vscode-pi"><img src="https://img.shields.io/badge/Open%20VSX-Registry-C8962E?logo=openvsx&logoColor=black"></a>
  <a href="https://github.com/cdervis/vscode-pi/releases/latest"><img src="https://img.shields.io/github/v/release/cdervis/vscode-pi?label=Release&logo=github"></a>
</p>


<p align="center">
  <img src="https://img.shields.io/badge/VS%20Code-%E2%89%A51.85.0-007ACC" alt="Required VS Code version">
  <img src="https://img.shields.io/badge/pi-%E2%89%A50.66.1-purple" alt="Minimum pi version">
</p>

This is a sidebar extension that launches your installed [pi](https://pi.dev) binary in RPC mode and turns it into a VS Code-native chat workflow. It adds streaming transcript rendering, tool output UI, session restore/history, model switching, and file context-aware prompts.

All while staying lightweight and true to pi's minimalism-focused philosophy.

Tested on macOS, Linux, and Windows.

## Features

- Sidebar chat built for long-running coding sessions
- Streaming markdown answers with syntax highlighting
- Rich tool rendering for read, write, edit, bash, images, and subagents
    - Including interactive Mermaid diagrams
- Message queuing and steering
- Supports your pi prompts and skills, e.g. "/commit"
- Session manager with search, rename, delete, and forking
- `@` file and folder mentions from the current workspace
- Easy-to-use model selector and thinking-level controls
- Context window tracking and manual compaction
- Smart merging of tool blocks

## Requirements

- VS Code or VSCodium
- A local `pi` installation available on `PATH` or `pi.binaryPath` setting
- A configured pi agent directory with at least one provider/model in `models.json`

If you don't have pi installed, the extension can install it for you using npm.
This requires you to have npm installed and available in your environment.

It can also create a basic `auth.json` file, but having a preconfigured pi installation is preferred. The onboarding process of the extension is a work-in-progress.

## Getting Started

1. Install pi: `npm install -g @mariozechner/pi-coding-agent`
2. Install this extension.
3. [Configure pi](https://github.com/cdervis/vscode-pi#readme) to your liking.
4. Open the `PI AGENT` view in the activity bar and start a chat.

## Notes

- The extension is a UI layer built on top of pi. Live pi state remains the source of truth.

## Troubleshooting

### pi is not detected

- Make sure `pi` is installed and available on your shell `PATH`.
- If it is installed somewhere custom, set `pi.binaryPath` to the absolute path.
- If the extension reports an incompatible version, update your local `pi` install first.

### Sessions or history look wrong

- Check `pi.agentDir`. The extension uses the resolved agent directory for both runtime startup and session-history file access.
- If you switch agent directories, restart the extension host or run the pi restart action so the running process and file-backed history stay aligned.

### Models are missing

- Confirm your pi agent directory contains a valid `models.json`.
- Make sure your provider configuration and API keys are set where pi expects them.

### Provider requests fail

- Re-check the provider credentials stored in your pi config or VS Code-backed secrets.
- After updating a key, restart pi from the extension so the spawned process picks up the new environment.

> **Unofficial extension**. This project is community-built and is not affiliated with or endorsed by the [pi agent](https://pi.dev) project.

> **This is a prerelease version, please [report any feedback and issues](https://github.com/cdervis/vscode-pi) to help improve it!**
