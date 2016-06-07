# Pure

> Pretty, minimal and fast ZSH prompt

![screenshot](screenshot.png)

Originally by @sindresorhus, with modifications from @jez.

## Overview

Most prompts are cluttered, ugly and slow. I wanted something visually pleasing that stayed out of my way.

### Why?

- Comes with the perfect prompt character.  
  Author went through the whole Unicode range to find it.
- Shows `git` branch and whether it's dirty (using color).
- Prompt character turns a custom color if the last command didn't exit with `0`.
- Command execution time will be displayed if it exceeds the set threshold.
- Username and host only displayed when in an SSH session.
- Shows the current path in the title and the [current folder & command](screenshot-title-cmd.png) when a process is running.
- Makes an excellent starting point for your own custom prompt.


## Install

Can be instaled through Git. You may also want to see [Integrations](#integrations).

1. Clone this repo to your [`$fpath`][1]. Don't know what an `$fpath` is, or don't think you've set it up? Skip to [Setting up your fpath](#setting-up-your-fpath).

   ```
   git clone https://github.com/jez/pure <anywhere>
   ```
   
   For a personal recommendation, I have `~/.zfunctions` in my fpath, and I just cloned it there for convenience:
   
   ```
   git clone https://github.com/jez/pure ~/.zfunctions/pure
   ```
   
2. Symlink `pure.zsh` in that repo to somewhere in your `fpath` with the name `prompt_pure_setup`.
   
   As I mentioned, I have `~/.zfunctions` in my `fpath`, so I run

   ```
   ln -s ~/.zfunctions/pure/pure.zsh ~/.zfunctions/prompt_pure_setup
   ```
   
   Which links from the `fpath` directory into the `pure.zsh` file in pure's repo.
   
3. Configure zsh to use the prompt.

   ```zsh
   # .zshrc
   autoload -U promptinit && promptinit
   prompt pure
   ```

[1]: http://www.refining-linux.org/archives/46/ZSH-Gem-12-Autoloading-functions/

## Setting up your fpath

If you're in zsh, you can see what's in your `$fpath`:

```
echo $fpath
```

A good way to add things to your `$fpath` is to set them in your ~/.zshenv file. Open or create this file, then add the following:

```
fpath=( "$HOME/.zfunctions" $fpath )
```


## Options

### `PURE_CMD_MAX_EXEC_TIME`

The max execution time of a process before its run time is shown when it exits. Defaults to `5` seconds.

### `PURE_GIT_PULL`

Set `PURE_GIT_PULL=0` to prevent Pure from checking whether the current Git remote has been updated.

### `PURE_GIT_UNTRACKED_DIRTY`

Set `PURE_GIT_UNTRACKED_DIRTY=0` to not include untracked files in dirtiness check. Only really useful on extremely huge repos like the WebKit repo.

### `PROMPT_PURE_SKIP_DIRTY_CHECK`

Set `PROMPT_PURE_SKIP_DIRTY_CHECK` to skip the dirtyness check altogether.

### `PROMPT_PURE_DIR_COLOR`, `PROMPT_PURE_VCS_COLOR`, `PROMPT_PURE_EXEC_TIME_COLOR`, `PROMPT_PURE_SUCCESS_COLOR`,  and `PROMPT_PURE_FAILURE_COLOR`

Use these options to control the colors of various parts of the prompt. They take arguments of the form `"%F{...}"` where `...` is some color string. Usage examples: `"%F{blue}"` (i.e., one of the 8 ANSI color names), or `"%F{242}"` (i.e., an xterm256 color code).


## Tips

[Tomorrow Night Eighties](https://github.com/chriskempson/tomorrow-theme) theme with the [Droid Sans Mono](http://www.google.com/webfonts/specimen/Droid+Sans+Mono) font (15pt) is a beautiful combination, as seen in the screenshot above. Just make sure you have anti-aliasing enabled in your Terminal.

To have commands colorized as seen in the screenshot install [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting).


## Integrations

### [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

Symlink (or copy) `pure.zsh` to `~/.oh-my-zsh/custom/pure.zsh-theme` and add `ZSH_THEME="pure"` to your `.zshrc` file.

### [prezto](https://github.com/sorin-ionescu/prezto)

Symlink (or copy) `pure.zsh` to `~/.zprezto/modules/prompt/functions/prompt_pure_setup` alongside Prezto's other prompts. Then `set zstyle ':prezto:module:prompt' theme 'pure'` in `~/.zpreztorc`.

### [antigen](https://github.com/zsh-users/antigen)

Add `antigen bundle sindresorhus/pure` to your .zshrc file (do not use the `antigen theme` function).


## License

MIT © [Sindre Sorhus](http://sindresorhus.com)
