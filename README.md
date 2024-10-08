# llm-cli
I want to interact with my terminal using natural language instead of obscure commands, in a simple, safe and 100% private way.

This is a dead simple shell script providing an in-terminal "natural language to terminal command interface" using an LLM that runs locally (using ollama).

Once installed, you type what you want to do in your terminal, like so:
```sh
llm "Find all files containing the word meditation"
```
and it answers with the actual command that will do it:
```sh
grep -r 'meditation'
```
You can then (optionally inspect 🤠) copy and paste to run the command.

## Install
These instructions are for Ubuntu but it can be adapted to work on any machine.
1. Install `wget`, `curl` and `jq` if you dont already have them
``` sh
sudo apt install wget curl jq
```
2. Install ollama
```sh
curl -fsSL https://ollama.com/install.sh | sh
```
3. Download my `llm` script from this repo and make sure its accessible on your PATH, and that it is exectuable
```sh
wget https://raw.githubusercontent.com/vijay-prema/llm-cli/main/llm
chmod +x llm
```

## Usage
### Run ollama server
**You need the ollama server always running the background for the script to work:**
```sh
ollama run gemma2
```
*The first time it will take a while to start as it is downloading the several GB model.
Read about [ollama here](https://github.com/ollama/ollama). It is possible to use different models other than gemma2, based on the spec of your PC.*

On Linux, you can close ollama cli by typing `/bye` and my script will still run, because ollama continues to run as a background service.  You can see the background service by typing `sudo systemctl status ollama.service`.

Now you can use the script to generate a terminal command from natural language:
```sh
llm "Find all files containing the word meditation"
```
It always gives you the raw command with no explanation, for the highest level of clean simplicity.

## Optional: change ollama model

If you PC is slow, answers could take a while. Try a smaller/faster ollama model if needed.  If you have a GPU, try a model that can work on your GPU.

You can change to any model listed in the [ollama model library](https://github.com/ollama/ollama?tab=readme-ov-file#model-library) by:
1. Running `ollama run <model-name>`
2. Editing the line in the `llm` script `"model": "<model-name>"`
