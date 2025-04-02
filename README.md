<img src="https://raw.githubusercontent.com/calmstate/vasto/refs/heads/main/assets/logo.png" alt="Vasto Logo" width="200">

**Create AI-powered endpoints the easy way.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Platform: Windows](https://img.shields.io/badge/Platform-Windows-lightgrey.svg)](#) <!-- Add other platforms later -->
<!-- Add other badges as needed: build status, version, etc. -->

Use Vasto to instantly turn your local [Ollama](https://ollama.com/) models into versatile, custom HTTP APIs for development, testing, and local integration.

![Vasto Application Screenshot](https://raw.githubusercontent.com/calmstate/vasto/refs/heads/main/assets/app.png)

---

## What is Vasto?

Vasto is a desktop application designed to bridge the gap between your locally running Ollama Large Language Models (LLMs) and your development projects. Instead of writing boilerplate server code to interact with Ollama's API for every different task, Vasto provides a simple graphical interface to:

1.  **Define Endpoints:** Specify custom routes (e.g., `/summarize`, `/generate-blog`), HTTP methods (GET, POST), and the Ollama model to use.
2.  **Structure I/O:** Define the expected JSON input structure (from URL parameters, query strings, or request body) and the desired JSON output structure.
3.  **Activate & Serve:** Vasto runs a local HTTP server that listens for requests on your defined endpoints, interacts with Ollama using your specified model and prompt structure (derived from the I/O definitions), and returns the structured JSON output.

Essentially, Vasto acts as a configurable proxy and management layer for your local Ollama instance, exposing specific model capabilities as standardized web APIs.

## Why Vasto? 🤔

*   ⏱️ **Rapid Prototyping:** Go from idea to a working AI endpoint in minutes. Perfect for quickly testing concepts that leverage local LLMs without complex setup.
*   🧩 **No More Boilerplate:** Stop writing repetitive server code for common LLM tasks. Vasto handles the HTTP server, request parsing, Ollama interaction, and response formatting.
*   🎯 **Standardized I/O:** Define clear JSON schemas for inputs and outputs. Ensures consistent and predictable API behavior, making integration easier.
*   🏠 **100% Local & Private:** Runs entirely on your machine, connecting directly to your local Ollama instance. Your models, prompts, and data stay completely private.
*   ⚙️ **Easy Management:** Create, update, activate/deactivate, and delete endpoints through a user-friendly interface.

## Key Features ✨

*   🔌 Direct connection to your local **Ollama instance**.
*   🧠 Compatible with **any Ollama model** you have installed (`ollama list`).
*   ↔️ Define custom routes and HTTP methods (`GET`, `POST`).
*   📝 Specify precise **JSON input and output structures**.
*   📥 Handles input from URL parameters, query strings, and request bodies.
*   ⚙️ Manage endpoints: **create, update, toggle activation**, delete.
*   🔒 Secure endpoints with optional **API Key (Bearer Token)** authentication.
*   💾 Persistent configuration stored locally in `endpoints.json`.
*   📦 Works as a **packaged application** (Installer/Portable).
*   📋 Quickly **list available Ollama models** directly within Vasto's UI.

## Prerequisites

*   **[Ollama](https://ollama.com/) installed and running** on your local machine. Vasto needs Ollama to function.

## Getting Started 🚀

### 1. Download Vasto

Head over to the **[Releases Page](https://github.com/calmstate/vasto/releases)** to download the latest version for your operating system.

*   Look for the appropriate asset (e.g., `.exe` installer or `.zip` portable for Windows).

### 2. Install / Run

*   **Installer:** Run the downloaded `.exe` file and follow the prompts.
*   **Portable:** Unzip the downloaded file and run the `Vasto.exe` (or similar) executable inside the folder.

## Usage 🛠️

1.  **Launch Vasto:** Start the application after installation.
2.  **Ensure Ollama is Running:** Vasto needs to connect to a running Ollama instance.
3.  **Create an Endpoint:**
    *   Click the "Create Endpoint" (or similar) button.
    *   Define the **Route** (e.g., `/translate`).
    *   Select the **HTTP Method** (e.g., `POST`).
    *   Choose the **Ollama Model** to use (Vasto can fetch the list from `ollama list`).
    *   Define the **Input JSON Schema** (what data the endpoint expects).
    *   Define the **Output JSON Schema** (how the LLM response should be structured).
    *   (Optional) Configure an **API Key**.
    *   Save the endpoint.
4.  **Activate the Endpoint:** Toggle the endpoint to "Active" in the endpoint list.
5.  **Test the Endpoint:** Use an HTTP client like `curl`, Postman, or integrate it into your application.

    ```bash
    # Example for a POST endpoint at /translate expecting JSON input
    curl -X POST http://localhost:YOUR_VASTO_PORT/translate \
         -H "Content-Type: application/json" \
         # -H "Authorization: Bearer YOUR_API_KEY" # If API key is set
         -d '{
               "text": "Hello world",
               "target_language": "Spanish"
             }'

    # Expected Response (based on output schema definition):
    # {
    #   "translated_text": "Hola mundo"
    # }
    ```
    *(Note: Replace `YOUR_VASTO_PORT` with the port Vasto is running on, likely shown in the UI or logs. Replace `YOUR_API_KEY` if you configured one)*

## Configuration ⚙️

Your endpoint definitions are saved locally in a file named `endpoints.json` within Vasto's application data directory. While you can view this file, it's recommended to manage endpoints through the Vasto UI to avoid formatting errors.

## Roadmap 🗺️

*   [ ] macOS Support (Packaged Application)
*   [ ] Linux Support (Packaged Application / AppImage)
*   [ ] Pre-built Endpoint Templates (e.g., Summarization, Translation, Chat)
*   [ ] More Authentication Options
*   [ ] Improved UI/UX based on feedback
*   [ ] Streaming responses support

## Contributing 🤝

Contributions are welcome! Please feel free to submit a Pull Request or open an Issue for bugs, feature requests, or suggestions.

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## License 📄

This project is licensed under the **GNU Affero General Public License v3.0** - see the [LICENSE](LICENSE) file for details, or visit [https://www.gnu.org/licenses/agpl-3.0.html](https://www.gnu.org/licenses/agpl-3.0.html).
