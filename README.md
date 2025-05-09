# GroqRunner

GroqRunner is a feature-rich development environment that combines terminal functionality, file management, and Groq AI chat integration in a modern, dark-themed GUI interface.

## Features

- **Multi-Terminal Support**: Create and manage multiple terminal instances within tabs
- **File Explorer**: Built-in folder outliner for easy file navigation
- **Groq AI Integration**: Direct chat interface with Groq's LLaMA-3 70B model
- **Virtual Environment Management**: Automatic creation and activation of Python virtual environments
- **Dark Theme**: Modern, eye-friendly dark theme for comfortable coding
- **Settings Management**: Configurable API keys and font sizes
- **Single Instance**: Prevents multiple instances of the application from running simultaneously

## Requirements

- Python 3.x
- PyQt5
- Requests library
- Windows OS (required for single-instance prevention and some file system operations)
- Groq API key

## Installation

1. Clone or download this repository
2. Install the required dependencies:
```
pip install -r requirements.txt
```

## Usage

### Starting the Application

Run the main script:
```
python main.py
```

### First-Time Setup

1. When first launching the application, you'll be prompted to enter your Groq API key
2. The application will automatically create and activate a virtual environment in the project directory

### Features Guide

#### Terminal Usage
- Click "New Terminal" in the toolbar to create a new terminal tab
- Enter commands in the input field at the bottom of each terminal tab
- Click "Execute" or press Enter to run commands

#### File Management
- Use the folder outliner on the left to browse files
- Double-click any file to open it in a new tab with the file viewer
- Files open in read-only mode by default
- Use "Toggle Edit Mode" button to edit files
- Save changes with the "Save" button
- Click "Refresh Folder" in the toolbar to update the file view

#### Groq Chat Interface
- Enter messages in the chat input field
- Use special commands:
  - `///cmd <command>` - Execute a terminal command
  - `///create <filename>` - Create a new file

#### Settings
- Access the Settings tab to configure:
  - Groq API Key
  - Font Size
  - Other preferences

## Architecture

The application is built using:
- PyQt5 for the GUI framework
- QProcess for terminal emulation
- QFileSystemModel for file system integration
- Groq API for AI chat capabilities

## Security Notes

- API keys are stored in memory during runtime and are encrypted to prevent unauthorized access. The application ensures that keys are not accessible to other processes.
- The application uses mutex to prevent multiple instances
- Virtual environment isolation for package management

## Logging

The application maintains detailed logs in `application.log`, tracking:
- Application startup/shutdown
- Virtual environment operations
- Command executions
- API interactions
- Error messages

## Llama Guard Content Moderation

This version uses Groq's Llama Guard 3 for content moderation. All AI responses are checked using the Llama Guard API. Unsafe content is blocked or flagged according to the moderation result.

### How it works
- When Groq returns a response, it is sent to the Llama Guard moderation endpoint.
- If the response is marked as unsafe, it is blocked and a warning is shown.
- See [Groq Llama Guard 3 documentation](https://console.groq.com/docs/content-moderation) for more details.

## Building the Portable EXE

To build the portable Llama Guard version:

1. Make sure your `requirements.txt` is up to date.
2. Run:
   ```
   pyinstaller GroqRunner_llamaguard.spec
   ```
3. The resulting `GroqRunner_llamaguard.exe` will be in the `dist/` or `build/` directory.

## GitHub Repository

Only the following files are tracked in the repository:
- `main.py`
- `README.md`
- `GroqRunner_llamaguard.exe` (for releases)

All other files are ignored for security and portability.

## Contributing

Feel free to submit issues and enhancement requests. I welcome contributions to improve GroqRunner.

## Author

JD Dondlinger

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Copyright (c) 2025 J.Dondlinger
