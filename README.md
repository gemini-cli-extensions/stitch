# Stitch Extension for Gemini CLI

The Stitch extension for Gemini CLI enables you to interact with the Stitch MCP (Model Context Protocol) server using natural language commands. This makes it easier to manage your design projects and assets within [Stitch](https://stitch.withgoogle.com/), the AI-powered UI/UX design and code generation tool.

## ✨ Features

- **🎨 List Projects:** View a list of your Stitch projects.
- **🎨 Project Details:** Get detailed information about a specific project.
- **🎨 Retrieve Screens:** Access all screens within a given project.
- **🎨 More features coming soon...*

## 📋 Prerequisites

Before using this extension, ensure you have the following:

1.  **Gemini CLI:**
    *   Install the Gemini CLI (v0.20.0 or newer).
    *   Refer to [go/gemini-cli](https://go/gemini-cli) for installation instructions.
    *   Setup Gemini CLI Authentication.

2.  **gcloud CLI:**
    *   Install and initialize the [gcloud CLI](https://go/gcloud-cli).

3.  **GCP Project Configuration:**
    *   Set your project and quota project.
        ```bash
        export PROJECT_NAME="your-project-id"
        gcloud config set project $PROJECT_NAME
        gcloud auth application-default set-quota-project $PROJECT_NAME
        ```
    *   **Service Usage Role:** Your account must have the `roles/serviceusage.serviceUsageConsumer` role.
        ```bash
        gcloud projects add-iam-policy-binding $PROJECT_NAME \
          --member="user:%USERNAME%@gmail.com" \
          --role="roles/serviceusage.serviceUsageConsumer"
        ```
    *   **Enable Stitch MCP:** Enable the Stitch MCP service on your project.
        ```bash
        gcloud beta services mcp enable stitch.googleapis.com --project=$PROJECT_NAME
        ```

4.  **Authentication:**
    *   Authenticate with Application Default Credentials (ADC).
        ```bash
        gcloud auth application-default login
        ```

## 🚀 Installation

1.  **Install the Extension:**
    Run the following command in your terminal to install the Stitch extension:
    ```bash
    gemini extensions install https://github.com/gemini-cli-extensions/stitch --auto-update
    ```
    *Note: The `--auto-update` flag is optional but recommended to keep the extension up-to-date.*

2.  **Configure `X-Goog-User-Project`:**
    *   Open the configuration file located at `~/.gemini/extensions/Stitch/gemini-extension.json`.
    *   Replace the placeholder `YOUR_PROJECT_ID` with the actual project ID you obtained in the prerequisites step.

## 💡 Usage

1.  **Start Gemini CLI:**
    Launch the Gemini CLI with the Stitch extension enabled:
    ```bash
    gemini -e stitch
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

## 🔧 Resources

*   [Stitch](https://stitch.withgoogle.com/): The official Stitch web application.
*   [Gemini CLI Extensions](https://gemini-cli-extensions.github.io/): Documentation on using extensions in Gemini CLI.
*   [GitHub Issues](https://github.com/gemini-cli-extensions/stitch/issues): Report bugs or request new features.

## 📄 Legal

*   **License:** [Apache License 2.0](https://github.com/gemini-cli-extensions/stitch/blob/main/LICENSE)