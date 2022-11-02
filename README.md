# gh-profile

[![Release](https://github.com/gabe565/gh-profile/actions/workflows/release.yml/badge.svg)](https://github.com/gabe565/gh-profile/actions/workflows/release.yml)
[![Go Report Card](https://goreportcard.com/badge/github.com/gabe565/gh-profile?v=1)](https://goreportcard.com/report/github.com/gabe565/gh-profile)

Work with multiple GitHub accounts using the [gh cli](https://cli.github.com/).

## Installation

```shell
gh extension install gabe565/gh-profile
gh extension install chiselscala/gh-profile
https://github.com/chiselscala/gh-profile.git

```

## Usage

See the [generated usage docs](./docs/profile.md), or see a summary of each
subcommand below.


### `gh profile create [NAME]`
Creates a new profile.

#### Params
- `NAME` is optional. If not set, command will run interactively.


### `gh profile switch [NAME] [--local-dir]`
Activates a profile.

#### Params
- `NAME` is optional. If not set, command will run interactively.
- `--local-dir`/`-l` activates the profile only for the current directory.
  - For this to work, you must install a per-directory env tool like
  [direnv](https://direnv.net).


### `gh profile rename [NAME] [NEW_NAME]`
Renames a profile.

#### Params
- `NAME` and `NEW_NAME` are optional. If not set, command will run interactively.


### `gh profile list`
Lists all profiles. Active profile will be bold with a green check.  


### `gh profile remove [NAME]`
Removes a profile.

#### Params
- `NAME` is optional. If not set, command will run interactively.


### `gh profile show`
Prints the active profile name. If no profile is active, nothing will be
printed. Useful as a [prompt element](#prompt-element).

## Prompt Element

`gh profile show` is useful for displaying the current profile in your
shell's prompt. This command will work for any prompt, but configuration
with [Powerlevel10k](https://github.com/romkatv/powerlevel10k) is provided
below.

### Powerlevel10k

Powerlevel10k ships with a custom formatter for `git` repositories. This
formatter can be easily modified to show the current profile.

1. Edit `~/.p10k.zsh`.
2. Find the `my_git_formatter` function
3. Find the line `local res`
4. Add the following below that line:
    ```shell
        local profile="$(gh profile show)"
        [[ -n "$profile" ]] && res+="$profile "
    ```

Now, the current profile will be shown when you are in a git repo!

#### Example

| Before | After |
|--------|-------|
| <img width="280" alt="Before" src="https://user-images.githubusercontent.com/114527278/199317857-876031b4-ac6f-45e5-84c5-304eadcbf5e6.png"> | <img width="345" alt="After" src="https://user-images.githubusercontent.com/114527278/199317888-7901518a-2a9c-40f8-8416-5c95cb62d60a.png"> |
