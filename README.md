# psig
Print linux process signal information.

## Set up:
```
curl -O https://raw.githubusercontent.com/erikdw/psig/master/psig
chmod +x psig
```

## Usage:
```
# Print signal info for a specific PID
./psig -p <PID>

# Print signal info for all PIDs
./psig -a

# Print blocked signals for a specific PID
./psig -p <PID> -b

# See other options:
./psig -h

```

## [Taco Bell Programming](http://widgetsandshit.com/teddziuba/2010/10/taco-bell-programming.html) Examples:
```
# Print caught signals from all threads (subtasks) of a specific PID
ls -d /proc/<PID>/task/[0-9]* | cut -d/ -f5 | xargs -I{} ./psig -c -p {}

# Print ignored signals from all 'processname' processes (using [] trick to prevent inclusion of grep process)
ps aux | grep processnam[e] | awk '{print $2}' | xargs -I{} ./psig -s -p {}
```

## Actual Output Example
```
% ./psig -a
[     1] Signals Queued: 8/773737
[     1] Signals Pending:
[     1] Signals Pending (Shared):
[     1] Signals Blocked:
[     1] Signals Ignored: SIGPIPE
[     1] Signals Caught: SIGHUP,SIGINT,SIGABRT,SIGUSR1,SIGSEGV,SIGALRM,SIGTERM,SIGCHLD,SIGPWR
...
[ 31001] Signals Queued: 0/773737
[ 31001] Signals Pending:
[ 31001] Signals Pending (Shared):
[ 31001] Signals Blocked: SIGHUP,SIGINT,SIGQUIT,SIGILL,SIGTRAP,SIGABRT,SIGBUS,SIGFPE,SIGUSR1,SIGUSR2,SIGPIPE,SIGALRM,SIGTERM,SIGSTKFLT,SIGCHLD,SIGCONT,SIGTSTP,SIGTTIN,SIGTTOU,SIGURG,SIGXCPU,SIGXFSZ,SIGPROF,SIGWINCH,SIGIO,SIGPWR,SIGSYS,SIGRTMIN,SIGRTMIN+1,SIGRTMIN+2,SIGRTMIN+3,SIGRTMIN+4,SIGRTMIN+5,SIGRTMIN+6,SIGRTMIN+7,SIGRTMIN+8,SIGRTMIN+9,SIGRTMIN+10,SIGRTMIN+11,SIGRTMIN+12,SIGRTMIN+13,SIGRTMIN+14,SIGRTMIN+15,SIGRTMAX-14,SIGRTMAX-13,SIGRTMAX-12,SIGRTMAX-11,SIGRTMAX-10,SIGRTMAX-9,SIGRTMAX-8,SIGRTMAX-7,SIGRTMAX-6,SIGRTMAX-5,SIGRTMAX-4,SIGRTMAX-3,SIGRTMAX-2,SIGRTMAX-1,SIGRTMAX
[ 31001] Signals Ignored: SIGHUP,SIGINT,SIGQUIT,SIGPIPE,SIGXFSZ
[ 31001] Signals Caught: SIGBUS,SIGUSR1,SIGSEGV,SIGUSR2,SIGALRM,SIGTERM,SIGVTALRM
```
