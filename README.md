# iTerm 2 + Fish Shell + Fisherman + Themes\Plugins

This guide is targeted for those, who wants to have a nice UI in the terminal with the rich features.

Please, raise your issue if something strange happened.
I'd like to improve this script, so it could work without any errors during the installation.

## The Problem

Every time, I've re-installed my operating system, I spend around ~30 minutes to set up my terminal environment again.
I bored of it, so I decided to make a list of all actions I doing, when setting it up, alongside with automatic script to do so, and share it with you all.

## Screenshots

There are a lot of screenshots available [here](./SCREENSHOTS.md).

## Key Features

- Installs Command Line Tools, Homebrew, iTerm2, Fish, Fisherman.
- Installs Material Design color preset for iTerm2 and patched Meslo Nerd Font.
- Theme `bobthefish`, which is based on popular `agnoster`.
- Completions for `brew`, `git`, `./node_modules/.bin` and so on, so on...
- Installs a lot of useful plugins, explained below.
- `await` function that waits for background jobs to finish with a nice spinner. i.e. `sleep 5 & await`.
- `bass` plugin that makes easy to use utilities written for Bash Shell in Fish Shell.
- `battery` function shows current level of the battery.
- Plugin `done` that notifies you when the process is finished. i.e. you can run `npm install` command and switch back into your browser. When `npm install` is done, you will get OSX notification.
- `errno-grep` function allows to search POSIX error codes and their messages.
- `fzy` plugin adds a hotkey <key>Ctrl</key>+<key>R</key> that allows to show and search in your command history.
- `license` function for generating GitHub license in your current folder.
- Plugin `pisces` that helps to you work with paired symbols like `()` or `''` in the command line.
- `pj` function allows to easily jump between your favorite directories. It installs with configured `~/Library/Projects` folder, so you can jump to any of your projects by calling `pj <PROJECT_FOLDER_NAME>`.
- `shark` function build sparklines right in your terminal.
- `fuck` function, I believe, everyone heard of it and what's doing.
- `upto` function gets you to a parent folder. I.e. you're inside `a/b/c/d/e/`, calling `upto b` will navigate you into `a/b`.
- `z` function shows the most recent and frequently visited folders, so you can go there without typing `cd` everytime.

## How To Setup

You can achieve the same setup as mine, by manually setting up the environment ([following the guide](#manual-installation) below) or automatically [by executing the installer](#automatic-installation) `install.sh`.

## Automatic Installation

__Highly recommended__ to run the script below under Bash session in default Terminal.app.
I can not guarantee proper installation outside of Terminal.app + Bash Shell.

```shell
$ bash <(curl -s https://raw.githubusercontent.com/ghaiklor/iterm-fish-fisherman-osx/master/install.sh)
```

## Manual Installation

### iTerm2

#### Install iTerm 2

- [Download](http://www.iterm2.com/downloads.html) and install iTerm2 (it has better color fidelity than the built in Terminal).

```shell
$ brew cask install iterm2
```

#### Install Color Scheme

Get the iTerm color settings:

- [Material Design Theme](https://raw.githubusercontent.com/MartinSeeler/iterm2-material-design/master/material-design-colors.itermcolors)
- [More themes @ iterm2colorschemes](http://iterm2colorschemes.com)

Just save it somewhere and open the file(s).
The color settings will be imported into iTerm2.
Apply them in iTerm through iTerm -> Preferences -> Profiles -> Colors -> Load Presets.
You can create a different profile, other than Default if you wish to do so.

#### Install Patched Font

- [Meslo LG M DZ Regular Nerd Font Complete Mono](https://raw.githubusercontent.com/ryanoasis/nerd-fonts/master/patched-fonts/Meslo/M-DZ/complete/Meslo%20LG%20M%20DZ%20Regular%20Nerd%20Font%20Complete%20Mono.otf)
- [Others @ powerline fonts](https://github.com/ryanoasis/nerd-fonts)

Open the downloaded font and press "Install Font".

Set this font in iTerm2 (iTerm -> Preferences -> Profiles -> Text).

- Regular Font -> "Change Font"
- Non-ASCII Font -> "Change Font"

Restart iTerm2 for all changes to take effect.

### Fish Shell

#### Install Fish Shell

Download and install [Fish Shell](https://fishshell.com).

```shell
$ brew install fish
$ echo "/usr/local/bin/fish" | sudo tee -a /etc/shells
$ chsh -s /usr/local/bin/fish
```

#### Install Fisherman

[Fisherman](https://fisherman.github.io) is a plugin manager for Fish Shell.

```shell
$ curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher
```

#### Install Themes and Plugins

```shell
$ fisher anicode
$ fisher await
$ fisher edc/bass
$ fisher omf/battery
$ fisher omf/theme-bobthefish
$ fisher laughedelic/brew-completions
$
$ brew install terminal-notifier
$ fisher done
$
$ fisher Shadowigor/plugin-errno-grep
$
$ brew install fzy
$ fisher fzy
$
$ brew install grc
$ fisher omf/grc
$
$ brew install jq
$ fisher omf/license
$
$ fisher omf/node-binpath
$ fisher laughedelic/pisces
$
$ fisher omf/pj
$ set -U PROJECT_PATHS ~/Library/Projects
$
$ fisher shark
$
$ fisher omf/thefuck
$ brew install thefuck
$
$ fisher upto
$ fisher z
```

- [Anicode](https://github.com/fisherman/anicode)

Find arbitrary unicode characters matching a search pattern.
The last result match will be copied to your clipboard.

- [Await](https://github.com/fisherman/await)

Wait for background jobs.

- [Bass](https://github.com/edc/bass)

Bass makes it easy to use utilities written for Bash in fish shell.

- [Battery](https://github.com/oh-my-fish/plugin-battery)

OS X and Linux compatible battery utility.

- [Bob The Fish](https://github.com/oh-my-fish/theme-bobthefish)

A Powerline-style, Git-aware fish theme optimized for awesome.

- [Brew Completions](https://github.com/laughedelic/brew-completions)

Fish shell completions for Homebrew.

- [done](https://github.com/fisherman/done)

A fish plugin to automatically receive notifications when long processes finish.

- [errno-grep](https://github.com/Shadowigor/plugin-errno-grep)

Search for error codes, labels or messages via `errno-grep`.

- [fzy](https://github.com/fisherman/fzy)

`fzy` picks up history item and adds it to your shell.
You need to execute manually.

Run `fkill` and type process you want to kill.
`fkill` kills immediately.
Press enter and process will be killed.

- [GRC](https://github.com/oh-my-fish/plugin-grc)

Generic Colouriser is yet another colouriser for beautifying your logfiles or output of commands.

- [License](https://github.com/oh-my-fish/plugin-license)

Fish Shell plugin for generating GitHub licenses.

- [Node BinPath](https://github.com/oh-my-fish/plugin-node-binpath)

Automatically add `node_modules/.bin` to `PATH` when present.

- [pisces](https://github.com/laughedelic/pisces)

pisces is a plugin for fish that helps you to work with paired symbols like `()` and `''` in the command line.
Just as in your favorite text editor!

- [PJ](https://github.com/oh-my-fish/plugin-pj)

`pj` allows you to easily jump between your favourite directories in a predictable manner.
You tell pj where to look for your projects, and it will allow you to jump to them easily with tab completion.
It even provides a convenient ability to open an editor in that directory from anywhere!

- [Shark](https://github.com/fisherman/shark)

Shark is a sparkline generator for fish.

- [The Fuck](https://github.com/oh-my-fish/plugin-thefuck)

This plug-in creates the necessary function to be used with The Fuck.

- [upto](https://github.com/fisherman/upto)

Gets you to a parent folder, heavily inspired by the plugin upto made by driv.

- [z](https://github.com/fisherman/z)

`z` tracks the directories you visit.
With a combination of frequency and recency, it enables you to jump to the directory in mind.

## License

[MIT](./LICENSE)
