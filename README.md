## 🚀 Getting Started with Git, GitHub, Pyenv, Poetry for project management on Python

Follow these steps to set up Git locally, connect it to GitHub using SSH, work with repositories, set up and manage Python projects. Use terminal on your computer. To go through this process I used Mac terminal. The process for Linux is the same. The process for Windows is hopefully the same too, but maybe may differ. If you have any problems copy-paste your errors and my instructions to ChatGPT

---

## One-time set up of all apps and packages on COMPUTER
Follow these steps to set up everything you need to professionally work on Python projects via your computer

### 🛠 Step 1. One-Time Setup of Git & GitHub on your computer

Firstly, one should set up Git and GitHub for their projects. Git is stored locally for project management on computer. GitHub is extension of Git that helps to manage projects online.

<details>
<summary><strong>1. Install Git</strong></summary>

Run this in your Terminal (macOS):
```bash
brew install git
````

</details>

<details>
<summary><strong>2. Configure Git</strong></summary>

Set your name and email for commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

This tells Git who you are when you make commits.

* **Git** = version control tool on your computer (local)
* **GitHub** = online storage for Git repositories (remote)

</details>

<details>
<summary><strong>3. Create an SSH Key</strong></summary>

Generate an SSH key (replace with your email):

```bash
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
```

* When it asks for a **passphrase**, just press **Enter** (no passphrase).
* Press **Enter** again to accept the default location.

List your SSH keys:

```bash
ls ~/.ssh/id_rsa*
```

Copy the public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Copy the **entire output** (your SSH public key).

</details>

<details>
<summary><strong>4. Add SSH Key to GitHub</strong></summary>

1. Go to GitHub
2. Click your profile picture → **Settings**
3. Go to **SSH and GPG keys**
4. Click **New SSH key**
5. Paste your public key, give it a name (e.g., "My MacBook"), and click **Add SSH key**

</details>

### 🖥 Alternative Step 1: GitHub Desktop [easier for non-programmers]

If you prefer a graphical interface over Terminal, you can use [GitHub Desktop](https://desktop.github.com/).  
It allows you to manage repositories, commits, and pushes with clicks instead of commands. It is also more intuitive

<details>
<summary><strong>1. Install GitHub Desktop</strong></summary>
- Download and install from: [https://desktop.github.com/](https://desktop.github.com/)
</details>

<details>
<summary><strong>2. Sign in to GitHub</strong></summary>
- Open GitHub Desktop  
- Go to **File → Options (or Preferences on Mac)**  
- Sign in with your GitHub account.
</details>

<details>
<summary><strong>3. Create a New Repository on GitHub</strong></summary>

1. Go to [GitHub](https://github.com)
2. Click **New repository**
3. Give it a name (e.g., `telegram-bot`)
4. Copy the SSH URL (looks like `git@github.com:USERNAME/REPO-NAME.git`)

</details>

<details>
<summary><strong>4. Clone a Repository</strong></summary>
- In GitHub Desktop, click **File → Clone Repository**  
- Select your repository from GitHub or paste its SSH/HTTPS link.  
- Choose a local folder where the repo will be stored.

**Note:** not sure if this is enough for SSH public-private key set up, I did everything via Terminal. At a glance should be fine
</details>

💡 You can switch between **Terminal** and **GitHub Desktop** at any time — both work with the same repository.

### 🐍 Step 2. One-time set up of Python Version & Dependency Management on computer (pyenv + Poetry)

One can add **pyenv** to control the Python version and **Poetry** to manage dependencies and virtual environments of projects. 
This will allow to avoid problems with python libarary dependencies once they are installed and updated. 
Additionally, this allows to keep many projects with different versions at once on 1 computer.

<details>

<summary><strong>6. Install pyenv & Poetry on your computer</strong></summary>

```bash
brew install pyenv
curl -sSL https://install.python-poetry.org | python3 -
```
</details>

<details>
<summary><strong>7. Configure Poetry to create virtual environments inside the project folder</strong></summary>

```bash
poetry config virtualenvs.in-project true
```
</details>

<details>
<summary><strong>8. Install and set the Python version</strong></summary>
  
```bash
pyenv install 3.11.9           # install required Python version
pyenv global 3.11.9            # set it as global default
```

You can now check your versions with:
```bash
pyenv versions
pyenv global
```
</details>


## One-time set up of all inner documentations and dependencies for NEW PROJECT
Follow these steps to professionally set up a new project and dependencies for ut on your computer

### 📂 Step 1. Setup of New Project at GitHub

To create new project on GitHub and manage it via local computer do the following:

<details>
<summary><strong>1. Create a New Repository on GitHub</strong></summary>

1. Go to [GitHub](https://github.com)
2. Click **New repository**
3. Give it a name (e.g., `telegram-bot`)
4. Copy the SSH URL (looks like `git@github.com:USERNAME/REPO-NAME.git`)

</details>

<details>
<summary><strong>2. Clone the Repository to Your Computer</strong></summary>

Locate to where you want to store your project, create folder, and locate (go) into it. In the example below i choose to store my GitHub projects in folder named 'Projects' on Desktop:

```bash
cd ~/Desktop      # go into Desktop via terminal
mkdir Projects    # create folder 'Projects'
cd Projects       # go to projects via terminal
```

Clone the repository:

```bash
git clone git@github.com:USERNAME/REPO-NAME.git
```

Move into the project folder:

```bash
cd REPO-NAME
```

</details>

### 🐍 Step 2. Add Poetry and Python version control to the project

After creating the project you need to download 1 version of python and add control for future libraries that will be used. This is essential to avoid problems when some libraries will be updated.

<details>
<summary><strong>1. Locate (move) to your project </strong></summary>

Move into the project folder:

```bash
cd REPO-NAME
```
For example, if our project is named 'telegram-bot' and is located in Desktop/Projects folders one should run:

```bash
cd Projects/telegram-bot
```
</details>

<details>
<summary><strong>2. Initialize Poetry </strong></summary>

```bash
poetry init
````

Then answer the prompts (press **Enter** where noted):

```bash
Package name [Name of The project]: <Press "Enter" or name of the project>
Version [0.1.0]: <Enter>
Description []: Enter here description of your project
Author []: <Press "Enter" or Name Surname <your_mail@email.com>>
License []: <Enter>
Compatible Python versions [^3.x]: ^3.11 (use version that you set up via pyenv install 3.11.9 before. For 3.11.9 use 3.11)
Would you like to define your main dependencies interactively? (yes/no) [no]: no
Would you like to define your dev dependencies interactively? (yes/no) [no]: no
Do you confirm generation? (yes/no) [yes]: yes
```

As a result of your actions `pyproject.toml` file will appear in the project folder

</details>

### 🗂️ Step 3. Create inner file structure for your project

Your project can have many different files, but typically every project should have a folder 'app' or 'api' and file 'test' that contain other files. 'app' containts folders with python codes, and 'test' contains files for running unit tests.

<details>
<summary><strong>1️⃣ Create a basic folder structure</strong></summary>
In your project root (for example, telegram-bot-cars-banks):

```bash
mkdir app                # creates folder 'app'
mkdir tests              # creates folder 'tests'
touch app/__init__.py    # creates file __init__.py in folder 'app'
touch app/bot.py         # creates file bot.py in folder 'app'
```

The file bot.py is an example file for project to create telegram bot. Your files can be different. You can also create any other structure you want and change it later.

You can run
```bash
tree
```

To see your current project structure. It will typically look like this:
```bash
.
├── LICENSE
├── README.md
├── app
│   ├── __init__.py
│   └── bot.py
├── pyproject.toml
└── tests
```
If you observe mistake then tree command is not installeed on your COMPUTER. To install it run

```bash
brew install tree
```
</details>

<details>
<summary><strong>2️⃣ Install development tools</strong></summary>

You need some other development tools apart from poetry to control the code structure. They are:

- **black** → automatic code formatter (very important for working in team)
- **pytest** → testing framework for unit tests
- **isort** → automatically sorts your Python imports into a clean, consistent order
- **flake8** → catches mistakes early

To install them run:

```bash
poetry add --group dev black isort flake8 pytest
```

</details>

<details>
<summary><strong>3️⃣ Update pyproject.toml</strong></summary>

Open pyproject.toml in your editor and scroll to the bottom.
If these sections don’t exist yet, add them:

```bash
[tool.black]
line-length = 88           # max characters per line before wrapping
target-version = ['py311'] # optimize for Python 3.11 syntax

[tool.isort]
profile = "black"         # make isort match black’s style automatically

[tool.flake8]
max-line-length = 88      # same as black to avoid conflicts
extend-ignore = E203      # avoid conflict with black's spacing rules
```

Save the file.

These changes will control all future written codes. You can consult GPT on how to set up this file more properly. There is a plenty of rules that you can add.

</details>

### 🤖 Step 4. Final Project Review with AI in Cursor

Once your environment is fully set up, we recommend running an **AI-assisted code check** in [Cursor](https://cursor.com/) (AI-powered fork of VS Code).  
This ensures your project is clean, dependencies are up to date, and files are properly configured.

<details>
<summary><strong>1️⃣ Open Your Project in Cursor</strong></summary>
1. Install **Cursor** (a VS Code fork with AI agents).
2. Link your **GitHub account** inside Cursor.
3. Open your project folder (e.g., `telegram-bot-cars-banks`) from your local computer.

</details>

<details>
<summary><strong>2️⃣ Run AI Code Review</strong></summary>
In Cursor, open the **AI command palette** and run: "check all files, are there any errors or incorrect set ups"

The AI agent will:
- **Simplify** and ensure your `bot.py` file starts with a minimal functional structure.
- **Update** `.gitignore` to avoid pushing unnecessary local files.
- **Adjust** `pyproject.toml` with the latest stable versions of development tools (`black`, `isort`, `flake8`, `pytest`).
- **Refine** formatting/linting configurations for best practices.
- **Update** `poetry.lock` if dependency versions change.

</details>

<details>
<summary>Recommendation:</summary>
Run this AI review **at the very end of your setup**.  
It acts as a **final checklist** before starting actual coding, making sure:
- Your environment is consistent.
- Your formatting & linting tools are set up correctly.
- Your GitHub repo ignores unneeded local files.
- As of **12 August 2025**, the most reliable AI agent for this is **SONET 3.5**.  

</details>

## 🔄 Typical Workflow Commands:

Here I show all regular commands for Git, GitHub, and Poetry that one may need to advance their project. Use Terminal while typing those commands.

<details>
<summary><strong>▶️ How to begin and end session correctly step by step (Git + Poetry)</strong></summary>

#### ▶️ Begin Session

1. Go to your project folder
```bash
cd /path/to/your/project
````

2. Pull the latest code

```bash
git pull
```

Or use GitHub Desktop to pull changes

3. Install dependencies

```bash
poetry install
```

4. (Optional) Add or remove libraries for this project

```bash
poetry add <package>             # add a runtime dependency
poetry add --group dev <package> # add a dev-only dependency
poetry remove <package>          # remove a dependency
```

> When you add/remove, **commit** the updated `pyproject.toml` and `poetry.lock`.

5. Run your app/tools inside the venv

```bash
poetry run python app/bot.py
```

---

#### ⏹ End Session

1. Run formatting & linting commands to clean up the code and detect errors

```bash
poetry run black app tests      # rewrite code following consistent style rules
poetry run isort app tests      # clean and order python imports logically
poetry run flake8 app tests     # check for syntax errors, unused vars, style issues
```

2. Check what changed

```bash
git status
```

3. Stage & commit your work

```bash
git add .
git commit -m "Describe what you changed"
```

4. Push to GitHub

```bash
git push
```

Alternative to 2-3-4: Use GitHub Desktop to commit changes and push files

---

#### ℹ️ Poetry Update

* Use **`poetry update`** when you intentionally want to upgrade packages to the **newest versions allowed** by `pyproject.toml`.
* This is **not** a daily step. Run it occasionally (e.g., weekly/monthly or before a release). It can break some parts of code if liabraries change a lot

```bash
poetry update
git add poetry.lock pyproject.toml
git commit -m "Update dependencies"
git push
```
</details>
<details>
<summary><strong>Typical GitHub Terminal Workflow</strong></summary>

Download project changes from GitHub and update it:
```bash
git pull
```

Add all changed files to staging:
```bash
git add .
```

Save your staged changes on local with a message:
```bash
git commit -m "Describe your changes"
```

Upload your local commits to GitHub:
```bash
git push
```

**Advice:** always start your session with "git pull" and finish with "git commit" or "git push". It is essential to store your changes

**To add in future:**
1) How to work with forks
2) How to merge changes when current version of code on computer is different from branch online
3) black for formatting
4) unit tests

</details>

<details>
<summary><strong>🖥 Typical GitHub Desktop Workflow [easier for non-programmers!]</strong></summary>

If you use graphical interface do this:

1. Edit files of project in your preferred code editor (Cursor, VS Code, etc.).  
2. Begin your work by pressing 'Fetch Origin' button. If there are changes of files been made press 'pull' to download all updates
3. After you made changes in code on your local computer write 'Summary' and 'Description' of your commit, press 'Commit' on the right top button, and then 'Push'


**To add in future:**
1) How to work with forks
2) How to merge changes when current version of code on computer is different from branch online
3) black for formatting
4) unit tests

</details>


<details>
<summary><strong>🐍 Typical Poetry Workflow</strong></summary>

Use these commands in your project folder (where `pyproject.toml` lives).

**Start of session (after `git pull`)**
```bash
poetry install         # install deps from pyproject.toml / poetry.lock
````

**Add / remove / update dependencies**

```bash
poetry add <package>                   # add runtime dependency (new library)
poetry add --group dev <package>       # add dev-only dependency (e.g., black, pytest)
poetry remove <package>                # remove dependency (remove library)
poetry update                          # update to newest allowed versions and refresh lock (update libraries)
```

**Run your app / tools inside the venv**

```bash
poetry run python app/bot.py           # runs file 'app/bot.py'
poetry run pytest                      # run tests (if using pytest). this should be typically used before commiting and pushing files
poetry run black .                     # format code (if black installed). this formats all the code
```

</details>

