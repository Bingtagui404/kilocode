---
title: "Installation"
description: "How to install Kilo Code on your system"
---

# Installation

Get started with Kilo Code by installing it on your preferred platform. Choose your development environment below.

{% callout type="info" title="Two Extension Versions" %}
Kilo Code offers two VS Code extension versions: the **stable release** (Classic, v5.x) and a **pre-release** (New, v7.x+) built on the Kilo CLI. The pre-release uses a new architecture with JSONC config files and a granular permission system. See [Introduction](/docs/getting-started) for details.
{% /callout %}

## Choose Your Platform

{% tabs %}
{% tab label="VS Code (Classic)" %}

## VS Code Classic Extension (v5.x)

{% partial file="install-vscode.md" /%}

{% /tab %}
{% tab label="VS Code (New)" %}

## VS Code Pre-Release Extension (v7.x+)

The pre-release extension is built on the [Kilo CLI](https://github.com/Kilo-Org/kilocode) core and features a new Solid.js-based UI, JSONC config files, and a granular permission system.

### Installing the Pre-Release

1. Open VS Code
2. Go to Extensions (`Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Search for "Kilo Code"
4. Click the dropdown arrow next to **Install** and select **Install Pre-Release Version**

### Switching Back to Classic

If you need to return to the stable version:

1. Open Extensions in VS Code
2. Find Kilo Code
3. Click the dropdown and select **Switch to Release Version**

### Migrating from Classic

When you first open the pre-release extension, a **migration wizard** detects settings from the Classic extension (providers, MCP servers, custom modes, default model) and offers to migrate them. You can also trigger this manually from **Settings → About**.

### Feedback and Issues

Report issues or provide feedback in the [Kilo-Org/kilocode repository](https://github.com/Kilo-Org/kilocode/issues).

{% /tab %}
{% tab label="CLI" %}

## Command Line Interface (v7.x+)

{% partial file="install-cli.md" /%}

{% /tab %}
{% tab label="JetBrains" %}

## JetBrains IDEs (Classic)

{% partial file="install-jetbrains.md" /%}

{% /tab %}
{% tab label="Slack" %}

## Slack Integration

{% partial file="install-slack.md" /%}

{% /tab %}
{% tab label="Other IDEs" %}

{% partial file="install-other-ides.md" /%}

{% /tab %}
{% /tabs %}

## Manual Installations

### Open VSX Registry

[Open VSX Registry](https://open-vsx.org/) is an open-source alternative to the VS Code Marketplace for VS Code-compatible editors that cannot access the official marketplace due to licensing restrictions.

For VS Code-compatible editors like VSCodium, Gitpod, Eclipse Theia, and Windsurf, you can browse and install directly from the [Kilo Code page on Open VSX Registry](https://open-vsx.org/extension/kilocode/Kilo-Code).

1. Open your editor
2. Access the Extensions view (Side Bar icon or `Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Your editor should be pre-configured to use Open VSX Registry
4. Search for "Kilo Code"
5. Select "Kilo Code" and click **Install**
6. Reload the editor if prompted

{% callout type="note" %}
If your editor isn't automatically configured for Open VSX Registry, you may need to set it as your extension marketplace in settings. Consult your specific editor's documentation for instructions.
{% /callout %}

### Via VSIX

If you prefer to download and install the VSIX file directly:

1. **Download the VSIX file:**
   - Find official releases on the [Kilo Code GitHub Releases page](https://github.com/Kilo-Org/kilocode/releases)
   - Download the `.vsix` file from the [latest release](https://github.com/Kilo-Org/kilocode/releases/latest)

2. **Install in VS Code:**
   - Open VS Code
   - Access Extensions view
   - Click the "..." menu in the Extensions view
   - Select "Install from VSIX..."
   - Browse to and select your downloaded `.vsix` file

{% image src="/docs/img/installing-vsix.png" alt="Installing Kilo Code using VS Code's Install from VSIX dialog" width="600px" caption="Installing Kilo Code using VS Code's \"Install from VSIX\" dialog" /%}

## Troubleshooting

**Extension Not Visible**

- Restart VS Code
- Verify Kilo Code is listed and enabled in Extensions
- Try disabling and re-enabling the extension in Extensions
- Check Output panel for errors (View → Output, select "Kilo Code")

**Installation Problems**

- Ensure stable internet connection
- Verify VS Code version 1.84.0 or later
- If VS Code Marketplace is inaccessible, try the Open VSX Registry method

**Windows Users**

- Ensure that **`PowerShell` is added to your `PATH`**:
  1. Open **Edit system environment variables** → **Environment Variables**
  2. Under **System variables**, select **Path** → **Edit** → **New**
  3. Add: `C:\Windows\System32\WindowsPowerShell\v1.0\`
  4. Click **OK** and restart VS Code

## Next Steps

After installation, check out these resources to get started:

- [Quickstart Guide](/docs/getting-started/quickstart) - Get up and running in minutes
- [Setting Up Authentication](/docs/getting-started/setup-authentication) - Configure your AI provider
- [Your First Task](/docs/code-with-ai/agents/chat-interface) - Learn the basics of working with Kilo Code

## Getting Support

If you encounter issues not covered here:

- Join our [Discord community](https://kilo.ai/discord) for real-time support
- Submit issues on [GitHub](https://github.com/Kilo-Org/kilocode/issues)
- Visit our [Reddit community](https://www.reddit.com/r/KiloCode)
