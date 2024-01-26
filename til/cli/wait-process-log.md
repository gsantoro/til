---
title: Wait for another to print a string into their logs
draft: true
tags: 

---
# Wait for another to print a string into their logs
I have had many occasions when a process needs to wait for another process to start.

To synchronise these two processes, we could wait for a specific string in the logs of the first process.

We can do this by using grep:

```bash
tail -f process_1.log | grep -m 1 "Process 1 has started"
```

This command will wait for the first occurrence of the string `Process 1 has started` and then continue as usual.

There is one small limitation in the previous command. If the log entry has already been written by the time the `grep` command starts, this grep command will wait indefinitely.

A nice modification is the following:

```bash
tail -f -n +1 process_1.log | grep -m 1 "Process 1 has started"
```

This command will instead read the log file from the beginning and then keep tailing the log file from the current position.

---

P.S. Notice that if you invert the order of the commands, grep might hand indefinitely since the tail process is still running

```bash
grep -m 1 "Process 1 has started" <(tail -f -n +1 process_1.log)
```