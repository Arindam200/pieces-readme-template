# <p align="center"> Pieces Python CLI Tool  

<p align="center">
      <a href="https://github.com/pieces-app/cli-agent" alt="GitHub contributors">
         <img src="https://img.shields.io/github/contributors/pieces-app/cli-agent.svg" />
      <a>
      <a href="https://github.com/pieces-app/cli-agent" alt="GitHub issues by-label">
         <img src="https://img.shields.io/github/issues/pieces-app/cli-agent" />
      </a>
      <a href="https://discord.gg/getpieces" alt="Discord">
         <img src="https://img.shields.io/badge/Discord-@layer5.svg?color=7389D8&label&logo=discord&logoColor=ffffff" />
      </a>
      <a href="https://twitter.com/getpieces" alt="Twitter Follow">
         <img src="https://img.shields.io/twitter/follow/pieces.svg?label=Follow" />
      </a>
      <a href="https://github.com/pieces-app/cli-agent" alt="License">
         <img src="https://img.shields.io/github/license/pieces-app/pieces-os-client-sdk-for-python.svg" />
      </a>
   </p>
</p>

## Introduction
This is a comprehensive command-line interface (CLI) tool designed to interact seamlessly with Pieces OS. It provides a range of functionalities such as asset management, application interaction, and integration with various Pieces OS features.

## Installation
To get started with the Pieces Python CLI Tool, you need to:

1. **The CLI Supports**: Ensure Pieces OS is installed and running on your system.
- [macOS](https://docs.pieces.app/installation-getting-started/macos) - Compatible with macOS 11 Big Sur or higher.
- [Windows](https://docs.pieces.app/installation-getting-started/windows) - Compatible with Windows 10 version 1809 or higher.
- [Linux](https://docs.pieces.app/installation-getting-started/linux) - Compatible with Ubuntu 18 or higher.
  
2. **Install the Python package**:

   ```bash
   pip install pieces-cli
   ```

   ```bash
   brew install pieces-cli
   ```

   ```bash
   conda install pieces-cli
   ```
You can also check Pieces Python [CLI Documentation](https://github.com/pieces-app/cli-agent/blob/prod/Documentation.md)

## Usage
After installing the CLI tool, you can access its functionalities through the terminal. The tool is initialized with the command `pieces` followed by various subcommands and options.

The `run` command starts the CLI in a loop. While you can use each command without running the CLI in a loop you'll get much faster results and a better experience using run. 

Once the CLI is running in a loop you can simply type the command.

    For instance: 
    open

    Instead of: 
    pieces open

If you have a numbered list or search open you can just type the number and it will open the asset associated. 

```bash
  pieces run
  ```

<details>
<summary>List Assets</summary>

To list assets or applications, use the command:

**Default of 10**
  ```bash
  pieces list
  ```

**Lists your x most recent assets**
  ```bash
  pieces list x
  ```

**Lists all registered applications**
  ```bash
  pieces list apps
  ```

**Lists all accessible AI models**
  ```bash
  pieces list models
  ```
</details>

<details>
<summary>Open, Save, Create, Edit, and Delete Assets</summary>

**Open an asset:**

Opens an asset from a list or search. If only "open" is used then it will open your most recent asset. This also creates a link to the asset's code.

```bash
pieces open [ITEM_INDEX]
```

**Save the current asset**

*Does Not Currently Work*

```bash
pieces save
```

**Create a new asset:**

Will take whatever text is copied to your clipboard and create an asset. The asset will automatically be scanned and recognized for it's file type. 

```bash
pieces create
```

**Edit an existing asset:**

This currently only works for an assets's name

```bash
pieces edit
```

**Delete an asset:**

This will delete an opened asset by using list or search first. If you do not have an opened asset it will open your most recent asset and ask if you'd like to delete it. 

```bash
pieces delete
```
</details>

<details>
<summary>Search and Query</summary>

*Perform a fuzzy search:**

```bash
pieces search [your query]
```

Finds strings that approximately match patterns. Normal search.

**Perform a Neural Code Search:**
```bash
pieces search query --mode ncs
```

Uses machine learning, deep neural networks, and natural language processing. It can understand the intent of a user's search query and match it with the most relevant results.

**Perform a Full Text Search:**
```bash
pieces search query --mode fts
```

Examines all words in a document to find matches to search criteria

**Ask a question to a model:**
** Requires quotes around question **

This currently only supports GPT 3.5 and it does not have working memory. Only coding questions are currently supported. To use the model's code you can copy it from the console and use the create command to create an asset using the copied code. 

```bash
pieces ask "your question"
```
</details>

<details>
<summary>Additional Commands</summary>
  
**Retrieve the version of Pieces OS and the CLI:**

```bash
pieces version
```

**For a detailed help menu:**

```bash
pieces help
```
</details>

It is advised to keep the CLI tool updated to the latest version to ensure compatibility with Pieces OS and access to all features. Please refer to our documentation for details on supported versions.

## Contributing
</details>
<details>
<summary>To run this project locally, follow these steps:</summary>

1. Fork this project via GitHub. 

2. Clone this project: 
```shell
git clone https://github.com/pieces-app/cli-agent
```

3. Create a Virtual Environment
```shell
python3 -m venv venv
``` 

4. Activate Your Virtualenv
```shell
source venv/bin/activate for Mac & Linux OS

cd venv\Scripts for Windows OS
activate 
```

5. This project uses poetry for managing dependencies and builds. Install poetry with:
```shell
pip install poetry
```

6. Then use poetry to install the required dependencies
```shell
poetry install
```

7. You build with
```shell
poetry build
```

8. Finally any project dependencies should be added to the pyproject.toml file with
```shell
poetry add 
```

9. Open the Dist folder
```shell
cd dist
``` 

10. Install the WHL file
```shell
pip install pieces-0.0.13-py3-none-any.whl
``` 

11. To view all the CLI Commands
```shell 
Pieces help 
``` 

these can be local/github/pypi etc.

</details>

## Learn More / Support
Explore more about Pieces SDK and get help from the following resources:

- 🚀 [Getting Started Tutorial](https://docs.pieces.app/installation-getting-started/what-am-i-installing)
- 📜 [Pieces Docs](https://docs.pieces.app/)
- 💬 [Discord Community](https://discord.gg/getpieces)

## License

This repository is available under the [MIT License](./LICENSE).