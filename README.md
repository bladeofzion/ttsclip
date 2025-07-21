# ttsclip
Text-to-speech from clipboard using OpenAI API (with chunking for long text).
**ttsclip** is a simple Bash utility that converts text from your clipboard to speech using the OpenAI TTS API. It handles long text by chunking it, processes the audio with effects (e.g., reverb, compression), and plays it back. Ideal for hobbyist hackers on Linux setups like LMDE 6, for quick TTS previews or automation.

## Features
- Reads text directly from the clipboard (via `xclip`).
- Automatically chunks long text (>4096 chars) to fit API limits.
- Uses OpenAI's TTS model (e.g., "tts-1-1106" with "nova" voice).
- Applies audio effects (reverb, bass/treble boost, compression, chorus) via SoX for enhanced output.
- Plays audio seamlessly with `ffplay` (auto-exits after playback).
- Dependency checker with installation suggestions.
- Lightweight and local—requires an OpenAI API key.

## Requirements
- **OS**: Linux (tested on LMDE 6/Debian-based systems).
- **Dependencies** (checked and suggested by the script):
  - `xclip` (clipboard access)
  - `jq` (JSON handling)
  - `curl` (API requests)
  - `ffmpeg` and `ffplay` (audio processing/playback)
  - `sox` (audio effects)
  - `iconv` (UTF-8 handling)
  - `xdotool` (optional, for window management)
  - `sed` and `cut` (text processing)
- **API Key**: An OpenAI API key (set as `OPENAI_API_KEY` environment variable).
- **Hardware**: Works on any setup, but audio playback benefits from good speakers/headphones (e.g., on laptops with Intel audio).

Install dependencies on Debian/LMDE:  
```bash
sudo apt update
sudo apt install xclip jq curl ffmpeg sox iconv xdotool sed coreutils
```

## Installation
1. Clone or download this repo:  
   ```bash
   git clone https://github.com/yourusername/ttsclip.git  # Replace with your repo URL
   cd ttsclip
   ```

2. Make the script executable:  
   ```bash
   chmod +x ttsclip
   ```

3. (Optional) Add to your PATH (e.g., move to `~/.local/bin`):  
   ```bash
   mv ttsclip ~/.local/bin/
   ```

4. Set your OpenAI API key (add to `~/.profile` or `~/.bashrc` for persistence):  
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   source ~/.profile
   ```

## Usage
Run the script in a terminal:  
```bash
./ttsclip
```
- It grabs the current clipboard text, sends chunks to OpenAI TTS, applies effects, and plays the audio.
- If the clipboard is empty, it exits with an error.

**Example Workflow**:
1. Copy some text (e.g., from a browser or editor).
2. Run `./ttsclip`.
3. Audio plays automatically (with effects like reverb and chorus for a polished sound).

For long text: It auto-chunks and processes sequentially (e.g., "Total chunks: 3" shown in output).

## Configuration
- **Voice/Model**: Edit the script's `jsonstr` (e.g., change "nova" to "onyx" or model to "tts-1-hd").
- **Audio Effects**: Customize the SoX pipeline in the script (e.g., adjust reverb or bass levels).
- **API Key Security**: Never hardcode your key—use the environment variable.

## Versioning
This script follows semantic versioning (SemVer):
- **v1.0.0**: Initial release (clipboard TTS with chunking and effects).
- See Git tags (e.g., `git tag`) or commit history for changes.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Author
Steven - Hobbyist.  
Feel free to open issues or PRs on GitHub!
