# pi Agent for VS Code

## Slow down, pi and VS Code are all you need.

A sidebar extension that launches your installed `pi` binary in RPC mode and turns it into a VS Code-native chat workflow. It keeps the agent close to your editor while staying lightweight and true to pi's minimalism.

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

The extension runs on macOS, Linux, and Windows, including with built-in **on-device** dictation.

## Features

- Sidebar chat built for long-running coding sessions
- Streaming markdown answers with syntax highlighting
- Rich tool rendering for read, write, edit, bash, image, and tool output
- Interactive Mermaid diagrams and zoomable image previews
- Message queuing, steering, and follow-up handling while the agent is busy
- Support for your pi prompts and skills, such as `/commit` and `/skill:plan-development`
- Session manager with search, rename, delete, and forking
- Model selector, model cycling, and thinking-level controls
- Context window tracking, automatic compaction, and manual compaction
- Workspace-aware `@` file and folder mentions
- Package management from the command palette and sidebar info menu
- Local microphone dictation with on-device `whisper.cpp`
- Auto-attached editor, selection, diagnostics, and git context controls
- Pasted or dropped image attachments in chat
- Post-run changed-files summaries after editing sessions
- HTML chat export
- UI customization for typography, spacing, labels, thinking blocks, separators, and corner style
- Optional diagnostics logging for troubleshooting startup, runtime, sidebar, resource, and dictation issues

## Requirements

- VS Code or VSCodium 1.85.0 or newer
- `pi` 0.66.1 or newer
- Provider credentials for the model you want to use

If `pi` is not installed yet, the extension can install it during onboarding when npm is available in your environment. You can also point the extension at a custom binary with `pi.binaryPath`.

## Getting Started

1. Install the extension from the VS Code Marketplace or Open VSX.
2. Open the `PI AGENT` view in the activity bar.
3. Follow onboarding if prompted. It can help install `pi`, choose a provider, add credentials, review setup, and select a model.
4. Start a chat.

## Dictation

The microphone button uses a bundled native helper and local `whisper.cpp` models. Transcription runs on-device after the selected model has been downloaded once.

Dictation supports:

- macOS
- Windows x64 & ARM64
- Linux x64 & ARM64

Use `pi.voice.enabled` to show or hide the microphone button. Use `pi.voice.model` to choose between the built-in tiny/base and multilingual/English-only model options. The sidebar shows download and recording progress, and the info menu can remove downloaded dictation models when cached models are present.

## Diagnostics

Diagnostics are off by default. Enable `pi.diagnostics.enabled` only when you are troubleshooting or preparing a support report.

When enabled, the extension writes high-signal progress and error logs to the **pi Diagnostics** output channel. The log includes lifecycle events, startup/runtime errors, model and thinking-level changes, compaction activity, token and session statistics, resource actions, and dictation state. It is intended to help identify why a workflow failed without dumping every internal detail of the extension.

Use **pi: Show Diagnostics Log** to inspect the current log, or **pi: Export Diagnostics Log...** to save it to a file of your choosing. Review exported logs before sharing them.

## Export

Use **Export chat as HTML** from the sidebar info menu to save the current chat transcript. Relative export folders are resolved from the workspace root.

## Troubleshooting

### pi is not detected

- Make sure `pi` is installed and available on your shell `PATH`.
- If it is installed somewhere custom, set `pi.binaryPath` to the absolute path.
- If the extension reports an incompatible version, update your local `pi` install first.

### Setup or models are missing

- Open the `PI AGENT` view and follow onboarding if it appears.
- Check `pi.agentDir` if you keep pi config somewhere other than the default agent directory.
- Make sure provider credentials are configured for the model you want to use.

### Sessions or history look wrong

- Check `pi.agentDir`. The extension uses the resolved agent directory for both runtime startup and session-history file access.
- If you switch agent directories, restart pi from the extension so the running process and file-backed history stay aligned.

### Provider requests fail

- Re-check the provider credentials stored in your pi config or VS Code-backed secrets.
- After updating a key, restart pi from the extension so the spawned process picks up the new environment.

### Dictation is unavailable

- Confirm `pi.voice.enabled` is turned on.
- Allow microphone access for VS Code in your OS privacy or audio settings.
- On unsupported platforms, the microphone button explains that dictation is unavailable.
- To collect troubleshooting logs, enable `pi.diagnostics.enabled`, reproduce the issue, then run **pi: Export Diagnostics Log...** and include the exported file with your report.

## Support

- Website: [vscode-pi.dev](https://vscode-pi.dev)
- Issues: [github.com/cdervis/vscode-pi/issues](https://github.com/cdervis/vscode-pi/issues)

> **Unofficial extension**. This project is community-built and is not affiliated with or endorsed by the [pi agent](https://pi.dev) project.
