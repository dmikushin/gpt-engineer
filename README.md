# GPT Software Engineer

This command-line AI software engineering assistant lets you:

* Specify software in natural language
* Sit back and watch as an AI writes and executes the code
* Ask the AI to implement improvements

https://github.com/dmikushin/gpt-engineer/assets/4467025/40d0a9a8-82d0-4432-9376-136df0d57c99


## Installation

User installation:

```
python3 -m venv ./venv
source ./venv/bin/activate.fish
pip install git+https://github.com/dmikushin/gpt-engineer.git
```

Developer installation:

```
python3 -m venv ./venv
source ./venv/bin/activate.fish
git clone https://github.com/dmikushin/gpt-engineer.git
cd gpt-engineer
pip install -e .
```


## Setup

Choose **one** of:

* Export env variable (you can add this to .bashrc so that you don't have to do it each time you start the terminal)
    - `export OPENAI_API_KEY=[your api key]`
* .env file:
    - Create a copy of `.env.template` named `.env`
    - Add your OPENAI_API_KEY in .env
* Custom model:
    - See [docs](https://gpt-engineer.readthedocs.io/en/latest/open_models.html), supports local model, azure, etc.

**Other ways to run:**

* Use Docker ([instructions](docker/README.md))


## Usage

### Create new code (default usage)

* Create an empty folder for your project anywhere on your computer
* Create a file called `prompt` (no extension) inside your new folder and fill it with instructions
* Run `gpte <project_dir>` with a relative path to your folder
  - For example: `gpte projects/my-new-project` from the gpt-engineer directory root with your new folder in `projects/`

### Improve existing code

* Locate a folder with code which you want to improve anywhere on your computer
* Create a file called `prompt` (no extension) inside your new folder and fill it with instructions for how you want to improve the code
* Run `gpte <project_dir> -i` with a relative path to your folder
  - For example: `gpte projects/my-old-project -i` from the gpt-engineer directory root with your folder in `projects/`


## Features

### Pre Prompts

You can specify the "identity" of the AI agent by overriding the `preprompts` folder with your own version of the `preprompts`. You can do so via the `--use-custom-preprompts` argument.

Editing the `preprompts` is how you make the agent remember things between projects.

### Vision

By default, gpt-engineer expects text input via a `prompt` file. It can also accept image inputs for vision-capable models. This can be useful for adding UX or architecture diagrams as additional context for GPT Engineer. You can do this by specifying an image directory with the `—-image_directory` flag and setting a vision-capable model in the second CLI argument, e.g:

```
gpte projects/example-vision gpt-4-vision-preview --prompt_file prompt/text --image_directory prompt/images -i
```

### Open source, local and alternative models

By default, gpt-engineer supports OpenAI Models via the OpenAI API or Azure OpenAI API, as well as Anthropic models.

With a little extra setup, you can also run with open source models like WizardCoder. See the [documentation](https://gpt-engineer.readthedocs.io/en/latest/open_models.html) for example instructions.

