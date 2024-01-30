---
title: Tmux with multiple panes
draft: true
tags: 

---
# Tmux with multiple panes
Run two commands in parallel in two different panes thanks to Tmux

```
tmux new-session -d -s my_session
tmux split-window -h -t my_session
tmux send-keys -t my_session:0.0 'first_command' C-m
tmux send-keys -t my_session:0.1 'second_command' C-m
tmux attach-session -t my_session
```
Once you are in the Tmux session you can:

- Switch windows with `CTRL+B, <- or -> arrow keys`
- Scroll up in the current window `CTRL+B, [`

Using Tmux is a better alternative to solutions like [multitail](https://www.tecmint.com/view-multiple-files-in-linux/) that allow you to tail more than a single log file but don't give the interactivity of a shell.