# Stitch Extension for Gemini CLI

The Stitch extension for Gemini CLI enables you to interact with the Stitch MCP (Model Context Protocol) server using natural language commands. This makes it easier to manage your design projects and assets within [Stitch](https://stitch.withgoogle.com/), the AI-powered UI/UX design and code generation tool.

## ✨ Features

- **🎨 List Projects:** View a list of your Stitch projects.
- **🎨 Project Details:** Get detailed information about a specific project.
- **🎨 Retrieve Screens:** Access all screens within a given project.
- **🎨 Download Assets:** Download assets such as images and HTML files.
- **🎨 Generate Screen From Text:** Generate new screens from text prompt, using Gemini 3 Pro or Gemini 3 Flash(default) models.
- **🎨 More features coming soon...**

## 📋 Prerequisites

Before using this extension, ensure you have the following installed:

1.  **Gemini CLI:**
    *   Install the Gemini CLI (v0.19.0 or newer).
    *   Refer to [Gemini CLI Documentation](https://geminicli.com/) for installation instructions.

2.  **gcloud CLI:**
    *   Install and initialize the [gcloud CLI](https://cloud.google.com/sdk/docs/install).
    *   Ensure you have a Google Cloud Project to use with Stitch.

## 🚀 Installation

Run the following command in your terminal to install the Stitch extension:

```bash
gemini extensions install https://github.com/gemini-cli-extensions/stitch --auto-update
```

## 🔐 Configuration & Authentication

To use the Stitch extension, you need to configure authentication. The Stitch MCP server supports two authentication methods:

- **API Key Authentication**: Simpler to set up. Use an API key generated from Stitch settings, powered by Google Cloud Managed Projects. Ideal for personal use and quick setup.
- **Application Default Credentials (ADC)**: Uses Google Cloud credentials for authentication. Requires your own Google Cloud project with proper IAM permissions, needs multiple manual steps to set up.

Choose one method below based on your needs.

### 1. Authenticate with Auth API Key

1.  **Get API Key:**
    *   Go to [Stitch](https://stitch.withgoogle.com/).
    *   Click on your profile icon in the top-right corner.
    *   Select "Stitch Settings" from the dropdown menu.
    *   Go to the "API Keys" section.
    *   Click on "Create Key".
    *   Copy the generated API key.

2.  **Configure Extension:**
    Run the following commands to configure your API key (replace `your-api-key-here` with your actual API key):
    ```bash
    export API_KEY="your-api-key-here"
    sed "s/YOUR_API_KEY/$API_KEY/g" ~/.gemini/extensions/Stitch/gemini-extension-apikey.json > ~/.gemini/extensions/Stitch/gemini-extension.json
    ```

### 2. Authenticate with Application Default Credentials (ADC)

1.  **Login to gcloud:**
    ```bash
    gcloud auth login
    ```

2.  **Configure Project and Quota:**
    Set your project ID variable and configure the project. Replace `your-project-id` with your actual Google Cloud Project ID.
    ```bash
    export PROJECT_ID="your-project-id"
    gcloud config set project $PROJECT_ID
    gcloud auth application-default set-quota-project $PROJECT_ID
    ```

3.  **Enable Stitch MCP API:**
    Enable the Stitch MCP service on your project.
    ```bash
    gcloud beta services mcp enable stitch.googleapis.com --project=$PROJECT_ID
    ```

4.  **Grant Permissions:**
    Your account needs the `roles/serviceusage.serviceUsageConsumer` role.
    ```bash
    gcloud projects add-iam-policy-binding $PROJECT_ID \
      --member="user:your-email@gmail.com" \
      --role="roles/serviceusage.serviceUsageConsumer"
    ```

5.  **Login to ADC:**
    ```bash
    gcloud auth application-default login
    ```

6.  **Configure Extension:**
    Run the following command to update the configuration file with your project ID:

    ```bash
    sed "s/YOUR_PROJECT_ID/$PROJECT_ID/g" ~/.gemini/extensions/Stitch/gemini-extension-adc.json > ~/.gemini/extensions/Stitch/gemini-extension.json
    ```

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

    /mcp desc
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

        You can generate new screens from text prompt, using Gemini 3 Pro or Gemini 3 Flash (default) models.
        ```
        /stitch Design a mobile app for people who love skiing in the Alps, using Gemini 3 Pro.
        ```
    *   **Enhance a Prompt:**
        ```
        /stitch Enhance this prompt: "Design a landing page for a podcast about the latest in Design and AI."
        ```

## 💸 Pricing

*    Stitch MCP is **free of charge**.

## 🔧 Resources

*   [Stitch](https://stitch.withgoogle.com/): The official Stitch web application.
*   [Gemini CLI Extensions](https://google-gemini.github.io/gemini-cli/docs/extensions/): Documentation on using extensions in Gemini CLI.
*   [GitHub Issues](https://github.com/gemini-cli-extensions/stitch/issues): Report bugs or request new features.

## 📄 Legal

Your use of the Stitch API is governed by the Google Terms and Use Policy, and the Google APIs Terms, and your Stitch settings. The Stitch Privacy Notice describes how your data is handled.

*   **[Google Terms and Use Policy](https://policies.google.com/terms)**
*   **[Google APIs Terms of Service](https://console.cloud.google.com/tos?id=universal)**
*   **[Stitch Privacy Notice](https://stitch.withgoogle.com/privacy)**
*   **[Apache License 2.0](https://github.com/gemini-cli-extensions/stitch/blob/main/LICENSE)**
