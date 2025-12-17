# English Tutor Plugin Installation Guide

This plugin is designed to work with **Claude Code**. Follow these steps to install and use it in your project.

## Proven Plugin Structure

Ensure your plugin directory has the following structure:

```
workspace/english-tutor/
├── .claude-plugin/
│   ├── marketplace.json      # Marketplace definition
│   └── plugin.json           # Plugin manifest
├── agents/
│   └── structure-analyst.md  # Agent definition
├── skills/
│   └── english-grammar/
│       └── SKILL.md          # Skill guide
├── commands/
│   └── structure.md          # Command definition
└── assets/
    └── example-filled-structure.md # Sample file
```

## Method 1: Local Installation (Dev Mode)

This is the fastest way to test the plugin without publishing to GitHub.

1.  **Open Claude Code CLI** at the project root (`cc-glean`).

2.  **Add Local Directory as Marketplace**:
    Register the plugin folder as a marketplace source:
    ```bash
    /plugin marketplace add ./workspace/english-tutor
    ```
    *Note: This reads `workspace/english-tutor/.claude-plugin/marketplace.json` to register the definition.*

3.  **Install the Plugin**:
    Once the marketplace is added (it will be named `local-english-tutor` as defined in the JSON file), install the plugin:
    ```bash
    /plugin install english-tutor@local-english-tutor
    ```
    *Note: If you are reinstalling updates, run `/plugin uninstall english-tutor` first.*

4.  **Verify**:
    Type `/help` to check if `/structure` command is available, or simply run:
    ```bash
    /structure --dry-run
    ```

## Method 2: GitHub Distribution (For Teams)

To share this plugin with your team, host it on a GitHub repository.

1.  **Prepare Metadata**:
    Ensure `.claude-plugin/plugin.json` matches this schema:
    ```json
    {
      "name": "english-tutor",
      "version": "1.0.0",
      "description": "English learning assistant and grammar structure analyst",
      "commands": [
        "./commands/structure.md"
      ],
      "agents": [
        "./agents/structure-analyst.md"
      ]
    }
    ```
    *Note: Paths must start with `./` and end with extension (e.g., `.md`).*

2.  **Prepare Marketplace Definition**:
    Ensure `.claude-plugin/marketplace.json` defines the source correctly:
    ```json
    {
      "name": "local-english-tutor",
      "owner": { "name": "local" },
      "plugins": [
        {
          "name": "english-tutor",
          "description": "English learning assistant...",
          "source": "./" 
        }
      ]
    }
    ```
    *Note: When pushing to GitHub, you might want to rename "local-english-tutor" to something more specific to your team.*

3.  **Push to GitHub**:
    Initialize repo and push all files in `workspace/english-tutor` to GitHub.

4.  **Install from GitHub**:
    Teammates can install using:
    ```bash
    /plugin marketplace add owner/repo-name
    /plugin install english-tutor
    ```

## Usage

After successful installation, execute the command:
```bash
/structure
```
This will scan for pending grammar structure files and use the `english-tutor:structure-analyst` agent to process them.
