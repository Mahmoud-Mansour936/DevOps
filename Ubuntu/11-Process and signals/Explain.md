# Explain

## Processes

- Every program you run creates **Process**
- Each process has **PID**
- When process crates another process → it’s called P**arent process**, and the created one called **Child process**
- Parent has **less PID**
- there is 3 types of processes [ shell - daemons - kernel]
 ,  ,

### Types

1. shell: for Processes started by a **user**
2. daemons: Background services that **start automatically** (or manually) and **run continuously**
3. kernel: Processes started and managed **by the Linux kernel**, not by users.

### Difference between Orphan and Zombie process

1. Zombie process : 
- A **process that has finished running** (exited),
- But its **parent hasn't read its exit status** yet using `wait()` or `waitpid()`.

1. Orphan process : 
- A **child process whose parent died** or was killed.

| Feature | Zombie Process | Orphan Process |
| --- | --- | --- |
| Alive? | ❌ No (already exited) | ✅ Yes (still running) |
| Parent Alive? | ✅ Yes | ❌ No |
| Cleanup Needed? | ✅ Yes (by parent) | ✅ Yes (by init) |
| Harmful? | ⚠️ Yes if many | ❌ No |
| Shown as `<defunct>` | ✅ Yes | ❌ No |

## Signals

- Message is sent to perform certain action

### Types

1. Sigterm : terminate the process and can be ignored or interrupted
2. Sigkill : forced terminate the process and can’t be ignored like (alt +f4 ) in windows 
3. Sigstop : pause the process 
4. Sigcont : continue the process