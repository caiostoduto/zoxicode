# zoxicode

Open VS Code in your most-used directories with just a few keystrokes — powered by [zoxide](https://github.com/ajeetdsouza/zoxide).

## What is it?

`zoxicode` wraps the `code` CLI with zoxide's smart directory resolver. Instead of typing a full path, you can jump to any directory you've visited before by typing just a fragment of its name.

```sh
# Instead of this:
code ~/projects/my-very-long-project-name

# You can do this:
zoxicode my-project
```

If the argument is an existing path, it opens directly. Otherwise, zoxide queries its frecency database to find the best match and opens that in VS Code.

## Requirements

- [zoxide](https://github.com/ajeetdsouza/zoxide)
- [VS Code](https://code.visualstudio.com/) with the `code` CLI available in your `PATH`

## Installation

### Homebrew (recommended)

```sh
brew tap caiostoduto/tap
brew install zoxicode
```

### Manual

Download the `zoxicode` script and place it somewhere in your `PATH`:

```sh
curl -o /usr/local/bin/zoxicode https://raw.githubusercontent.com/caiostoduto/zoxicode/main/zoxicode
chmod +x /usr/local/bin/zoxicode
```

## Usage

```sh
zoxicode <query>
```

| Argument | Behavior |
|---|---|
| A valid path (e.g. `./my-dir`, `/home/user/project`) | Opens that path directly in VS Code |
| A partial name (e.g. `zoxi`, `my-proj`) | Resolves the best match via `zoxide` and opens it in VS Code |

## How it works

```
zoxicode <query>
     │
     ├─ path exists? ──yes──▶ code <query>
     │
     └─ no ──▶ zoxide query <query> ──▶ code <result>
```

The more you use `zoxide` to navigate your terminal, the smarter the suggestions become.

## License

[GNU General Public License v3.0](LICENSE)