# Stitch Extension for Gemini CLI

The Stitch extension for Gemini CLI enables you to interact with the Stitch MCP (Model Context Protocol) server using natural language commands. This makes it easier to manage your design projects and assets within [Stitch](https://stitch.withgoogle.com/), the AI-powered UI/UX design and code generation tool.

## ✨ Features

- **🎨 List Projects:** View a list of your Stitch projects.
- **🎨 Project Details:** Get detailed information about a specific project.
- **🎨 Retrieve Screens:** Access all screens within a given project.
- **🎨 Download Assets:** Download assets such as images and HTML files.
- **🎨 Generate Screen From Text:** Generate new screens from text prompt.
- **🎨 More features coming soon...*

## 📋 Prerequisites

Before using this extension, ensure you have the following:

1.  **Gemini CLI:**
    *   Install the Gemini CLI (v0.19.0 or newer).
    *   Refer to [Gemini CLI ](https://geminicli.com/) for installation instructions.
    *   Setup Gemini CLI Authentication.

## 🚀 Installation

1.  **Install the Extension:**
    Run the following command in your terminal to install the Stitch extension:
    ```bash
    gemini extensions install https://github.com/gemini-cli-extensions/stitch
    ```

2.  **Get API Key:**
    *   Go to [Stitch](https://stitch.withgoogle.com/).
    *   Click on your profile icon in the top-right corner.
    *   Select "Stitch Settings" from the dropdown menu.
    *   Go to the "API Keys" section.
    *   Click on "Create Key".
    *   Copy the generated API key.

2.  **Configure `X-Goog-Api-Key`:**
    *   Open the configuration file located at `~/.gemini/extensions/Stitch/gemini-extension.json`.
    *   Replace the placeholder `API_KEY` with the actual API key you obtained in the prerequisites step.

## 💡 Usage

1.  **Start Gemini CLI:**
    Launch the Gemini CLI with the Stitch extension enabled:
    ```bash
    gemini
    ```

2.  **List Available Tools:**
    To see all available MCP tools, including those from Stitch, use:
    ```
    /mcp list
    ```

3.  **Interact with Stitch:**
    Use the `/stitch` command prefix to send natural language requests. Examples:

    *   **List Projects:**
        ```
        /stitch What Stitch projects do I have?
        ```
    *   **Get Project Details:**
        ```
        /stitch Tell me details about my project 3677573127824787033
        ```
    *   **List Screens:**
        ```
        /stitch Give me all the screens of project 3677573127824787033
        ```
    *   **Download Assets:**
        ```
        /stitch Download the image of screen 6393b8177be0490f89eb8f2c1e4cfb37
        /stitch Download the HTML of screen 6393b8177be0490f89eb8f2c1e4cfb37
        ```
    *   **Generate new Screens:**
        ```
        /stitch Design a mobile app for people who love skiing in the Alps. 
        ```         
    *   **Enhance a Prompt:**
        ```
        /stitch Enhance this prompt: "Design a landing page for a podcast about the latest in Design and AI."
        ```

## 📜 Terms of Service

By using this product you agree to the terms and conditions of the following license: [Google APIs Terms of Service](https://console.cloud.google.com/tos?id=universal).

## 💸 Pricing

*    Stitch MCP is **free of charge**.

## 🔧 Resources

*   [Stitch](https://stitch.withgoogle.com/): The official Stitch web application.
*   [Gemini CLI Extensions](https://google-gemini.github.io/gemini-cli/docs/extensions/): Documentation on using extensions in Gemini CLI.
*   [GitHub Issues](https://github.com/gemini-cli-extensions/stitch/issues): Report bugs or request new features.

## 📄 Legal

*   **License:** [Apache License 2.0](https://github.com/gemini-cli-extensions/stitch/blob/main/LICENSE)
