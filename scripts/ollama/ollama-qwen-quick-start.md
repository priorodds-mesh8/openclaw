# Ollama Qwen 2.5 Quick Start Guide (Mac Pro M3)

## Starting the Ollama Server

The Ollama server typically runs as a background service on macOS. To ensure it's running:

```bash
# Check if ollama is already running
ps aux | grep ollama

# If not running, start it manually
ollama serve
```

Once started, the server runs on `http://localhost:11434` by default.

## Running Qwen 2.5

### Basic Chat Interaction

Open a new terminal window/tab and run:

```bash
ollama run qwen2.5
```

This starts an interactive chat session. Type your prompts and press Enter. Type `exit` or `quit` to leave.

### Running with Specific Parameters

```bash
# Run with custom temperature (0-1, lower = more deterministic)
ollama run qwen2.5 --temperature 0.7

# Run without keeping the model in memory
ollama run qwen2.5 --nokeep
```

## Common Commands

```bash
# List installed models
ollama list

# Pull a specific model variant (if using different sizes)
ollama pull qwen2.5

# Remove a model to free space
ollama rm qwen2.5

# Show model information
ollama show qwen2.5

# Check server status
curl http://localhost:11434/api/tags
```

## Using Qwen via API (for developers)

If you want to call Qwen programmatically:

```bash
# Using curl
curl http://localhost:11434/api/generate -d '{
  "model": "qwen2.5",
  "prompt": "What is machine learning?",
  "stream": false
}'

# Using Python
# First: pip install requests
# Then create a script with:
# import requests
# response = requests.post('http://localhost:11434/api/generate',
#   json={"model": "qwen2.5", "prompt": "Your question here", "stream": False})
# print(response.json()['response'])
```

## Performance Tips for M3 Mac with 8GB RAM

- **Keep it lean**: Close unnecessary apps before running Qwen to maximize available RAM
- **Use smaller context**: Keep prompts concise; longer contexts use more memory
- **Monitor memory**: Use `top` or `Activity Monitor` to watch RAM usage
- **Streaming responses**: Add `"stream": true` to API calls for faster perceived response times

## Stopping the Server

To cleanly shut down:

```bash
# Stop ollama serve (if running in current terminal)
# Press Ctrl+C

# Or kill the background process
pkill ollama
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `Error: connection refused` | Ollama server isn't running; start with `ollama serve` |
| `Out of memory errors` | Close other apps; try shorter prompts; reduce batch size |
| `Model not found` | Run `ollama pull qwen2.5` to download it |
| `Slow responses` | Normal on 8GB—M3 is capable but RAM-constrained for LLMs |

## Check Your Setup

```bash
# Verify ollama is installed
which ollama

# Check version
ollama --version

# Verify qwen2.5 is installed
ollama list | grep qwen2.5
```

---

**Note**: Qwen 2.5 is memory-efficient, but on 8GB RAM, you may experience slower inference. Consider using smaller quantizations if available, or running with context limits for optimal performance.
