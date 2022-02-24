# SUID executable core dump

**Situation :** A SUID executable reads a file into memory that you lack permission to read. The executable has coredump generation enabled (Source code contains `prctl(PR_SET_DUMPABLE, 1)` or hinted at by a valgrind file).

**Note :** Using GDB to debug the SUID executable will result in the executable not gaining privilege as GDB uses your current permission level.

**Exploit :** Run the SUID executable to the point that it reads the file. Once read, background the process with `ctrl + Z` , use `ps` to locate the executables' PID, and then send `SIGSEGV` to cause a segmentation fault (`kill -SIGSEGV [PID]`). Finally, execute `fg` to resume (and crash) the file, resulting in a crash file appearing (`/var/crash/_path_to_executable.uid.crash`).

Use `apport-unpack` to unpack the crash information into a new folder apport-unpack `/tmp/_path_to_executable.uid.crash /tmp/mycrash`. Switch to the `/tmp/mycrash` directory.

Explore the content of the `CoreDump` using a command such as `strings CoreDump`. Hopefully, the file content you are looking for will appear.

### Exemple de code vulnérable

```
-rwsr-xr-x 1 root root 17824 Oct  7 10:03 count
```

```c
// drop privs to limit file write
setuid(getuid());
// Enable coredump generation
prctl(PR_SET_DUMPABLE, 1);
```
