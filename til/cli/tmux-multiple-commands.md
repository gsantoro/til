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