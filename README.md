# llm-cli
Dead simple shell script for a terminal command LLM AI assistant that runs locally.  100% private, no data over the internet.

Once installed you type in your terminal like so:
```sh
llm "Find all files containing the word meditation"
```
and it answers with:
```sh
find . -type f -exec grep 'meditation' {} \;
```
You can then copy/paste and run the command

## Install
These nstructions are for Ubuntu but it can be adapted to work on any machine.
1. Install curl and jq if you dont already have them
``` sh
sudo apt install curl jq
```
2. Install ollama
```sh
curl -fsSL https://ollama.com/install.sh | sh
```
3. Download my `llm` script from this repo and make sure its accessible on your PATH, and that it is exectuable
```sh
curl -fsSL https://raw.githubusercontent.com/vijay-prema/llm-cli/main/llm
chmod +x llm
```

## Run ollama server
**You need the ollama server always running the background for the script to work.**  Read about [ollama here](https://github.com/ollama/ollama). It is possible to use different models other than gemma2, based on the spec of your PC.
```sh
ollama run gemma2
```
The first time it will take a while to start as it is downloading the several GB model.

## Run a query in terminal
Simple:
```sh
llm "Find all files containing the word meditation"
```
It always gives you the raw command with no explanation. Now you can run it at your own risk!
