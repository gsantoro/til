# UV - Alternative to pip, venv, poetry, virtualenv

## Alternative to Pipx 
Isolated global environment.

Create symlinks into `~/.local/bin` to the isolated virtual environment created by Uv so to not interfere with .venv in the local dir.

```bash
uv tool install <package>
```

If you instead want to use the command without installing it, you can use:

```bash
uvx <package>
```