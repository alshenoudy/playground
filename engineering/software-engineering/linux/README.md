# Linux

Your models run on Linux servers. Understanding the OS — not just surviving on it — makes you faster at debugging, better at writing efficient code, and less dependent on someone else to fix things when they break.

---

## Goal

- Navigate and operate a Linux system confidently, including remote servers and HPC clusters
- Understand what the OS is doing when your training job runs
- Diagnose performance problems at the system level, not just the Python level
- Write shell scripts that are reliable, not just "works on my machine"

---

## Prerequisites

- Basic command line usage (you already have this)
- A Linux machine or WSL2 environment to practice on

---

## Learning Path

### 1. The Shell
- [ ] Bash fundamentals: variables, quoting rules (when to use `"`, `'`, no quotes), command substitution `$()`
- [ ] Pipes and redirection: `|`, `>`, `>>`, `2>`, `2>&1`, `/dev/null` — understand each
- [ ] Exit codes: `$?`, `set -e`, `set -o pipefail` — writing scripts that fail loudly
- [ ] Conditionals and loops: `if`, `for`, `while`, `case` — with real file/string/numeric tests
- [ ] Functions in bash: scope, `local`, return values (they're exit codes, not return values)
- [ ] `$@`, `$#`, `$0`, `$1` — argument handling in scripts
- [ ] **Project:** Write a dataset preprocessing script — takes a source directory, validates files, runs preprocessing, logs errors to a file, exits non-zero on failure. Robust enough to run in CI.

### 2. Core Tools
Master these to the point where reaching for them is instinctive.

- [ ] `find`: by name, type, size, modification time, with `-exec`
- [ ] `grep` / `ripgrep`: regex search, `-r`, `-l`, `-n`, fixed strings vs regex
- [ ] `awk`: field splitting, pattern matching, `NR`, `NF`, basic arithmetic — know enough to replace a Python one-liner
- [ ] `sed`: in-place substitution, line deletion, regex replacement
- [ ] `xargs`: turning output into arguments, parallelism with `-P`
- [ ] `sort`, `uniq`, `cut`, `wc`, `head`, `tail` — composing pipelines from small tools
- [ ] `jq`: parsing JSON from the command line (model configs, API responses)
- [ ] **Implementation:** Given a directory of NIfTI files, write a one-liner pipeline that: finds all `.nii.gz` files, extracts filenames, counts them, and outputs a summary of how many belong to each patient ID (assumed to be the filename prefix before `_`)

### 3. Processes and Jobs
- [ ] `ps aux`, `pgrep`, `pkill`: finding and sending signals to processes
- [ ] `kill` and signals: `SIGTERM` vs `SIGKILL` vs `SIGINT` — what each does and when to use each
- [ ] `nice` and `renice`: adjusting process priority — useful when running training alongside other jobs
- [ ] Background jobs: `&`, `jobs`, `fg`, `bg`, `disown`
- [ ] `tmux`: sessions, windows, panes — a setup you use every time you SSH into a server
- [ ] `nohup`: keeping jobs alive after logout — and why `tmux` is usually better
- [ ] **Implementation:** A `tmux` config and session setup script — starts a session with named windows for: training, monitoring, and a scratch terminal

### 4. System Monitoring
Know what your training job is doing at the OS level.

- [ ] `htop`: CPU per core, memory, swap, load average — read it fluently
- [ ] `nvidia-smi`: GPU utilisation, memory, running processes, `nvidia-smi dmon` for continuous monitoring
- [ ] `iostat`: disk I/O — diagnosing DataLoader bottlenecks when GPU utilisation is low
- [ ] `nethogs` / `iftop`: per-process network usage — useful in distributed training
- [ ] `free -h`: memory usage, understanding buffers/cache vs used
- [ ] `df -h`, `du -sh`: disk space — before your training run fills the disk at 3am
- [ ] `dmesg`: kernel messages — where GPU errors and OOM kills get logged
- [ ] **Implementation:** Write a monitoring script that samples `nvidia-smi`, CPU%, and disk I/O every 30 seconds and appends to a log file. Run it alongside a training job and analyse the output.

### 5. Files, Permissions, and the Filesystem
- [ ] Permissions: `rwx`, `chmod`, `chown`, octal notation — understand, don't guess
- [ ] Hard links vs symbolic links: when each is appropriate, how `ln` works
- [ ] `/proc` filesystem: `/proc/PID/` — reading process memory maps, open files, CPU stats
- [ ] `/dev/shm`: shared memory filesystem — relevant for fast DataLoader with `multiprocessing`
- [ ] `inode`: what it is, `ls -i`, why running out of inodes is a different problem from running out of space
- [ ] File descriptors: `lsof -p PID`, why too many open files is a real error you will encounter

### 6. Networking Basics
- [ ] `ssh`: key-based auth, `~/.ssh/config` — setting up a clean multi-server config
- [ ] `scp` and `rsync`: moving data to/from servers; `rsync` for incremental syncs of large datasets
- [ ] `curl` and `wget`: fetching data, testing APIs from the command line
- [ ] `netstat` / `ss`: what ports are open, what's listening — useful when a service won't start
- [ ] `/etc/hosts`: local hostname resolution — handy in multi-node training setups
- [ ] `ping`, `traceroute`, `mtr`: diagnosing network issues between training nodes

### 7. HPC and Cluster-Specific
Specific to running experiments on university or cloud clusters.

- [ ] SLURM basics: `sbatch`, `squeue`, `scancel`, `sinfo` — submitting and managing jobs
- [ ] Writing a SLURM job script: `#SBATCH` directives, GPU allocation, memory, time limits
- [ ] Array jobs: running the same script with different parameters (`--array=1-20`)
- [ ] Module system: `module load`, `module avail` — managing CUDA versions on HPC
- [ ] **Project:** Write a SLURM job template for a training run — handles GPU allocation, logs stdout/stderr separately, emails on failure, and supports array jobs for hyperparameter sweeps

---

## Projects

| Project | Key concepts |
|---|---|
| Dataset preprocessing script | Bash scripting, error handling, exit codes |
| NIfTI pipeline one-liner | `find`, `awk`, `xargs`, composing tools |
| `tmux` setup script | Session management, remote work setup |
| System monitoring script | `nvidia-smi`, `iostat`, logging |
| SLURM job template | HPC job submission, array jobs |

---

## Resources

**Books**
- *The Linux Command Line* — William Shotts (free online, thorough)
- *Linux System Programming* — Robert Love (if you want to go deep on syscalls and the kernel)

**Reference**
- `man` pages — for anything in section 1 (commands) and section 2 (syscalls), the man page is the source of truth
- `tldr` — community-maintained cheat sheets for common commands, faster than man pages for quick lookups
- explainshell.com — paste a shell command and see each part explained

---

## Progress

- [ ] The shell
- [ ] Core tools
- [ ] Processes and jobs
- [ ] System monitoring
- [ ] Files, permissions, and the filesystem
- [ ] Networking basics
- [ ] HPC and cluster-specific
- [ ] Project: Dataset preprocessing script
- [ ] Project: NIfTI pipeline one-liner
- [ ] Project: `tmux` setup script
- [ ] Project: System monitoring script
- [ ] Project: SLURM job template
