---
title: Get PID by command args
draft: true
tags: 

---
# Get PID by command
If you need to get the PID of a process by the command or the command args use this command

```
pgrep -f "node scripts/functional_test_runner" > {{.KIBANA_FTR_RUNNER_PID}}
```

If you also want to do nothing if the process is not found but not fail the command, you can run instead

```
pgrep -f "node scripts/functional_test_runner" > {{.KIBANA_FTR_RUNNER_PID}} || true
```