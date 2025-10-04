`rmdir` Command Documentation

## Overview

The `rmdir` program removes **empty directories**.

* If the directory is **not empty**, it prints an error and does nothing.
* If the path is not a directory, it also prints an error.
* With the `-v` flag, `rmdir` prints a confirmation message when a directory is successfully removed.

This behavior matches typical `rmdir`.

---

## Usage

```sh
rmdir [-v] DIR [DIR ...]
```

* `DIR [DIR ...]` – one or more directories to remove.
* `-v` – verbose mode, prints a message for each directory removed.

---

## Examples

```sh
# Remove an empty directory
$ mkdir emptydir
$ rmdir emptydir
# (no output, directory gone)

# Try removing a non-empty directory
$ mkdir full
$ echo hello > full/file.txt
$ rmdir full
rmdir: full: directory not empty

# Verbose mode
$ mkdir vdir
$ rmdir -v vdir
rmdir: removed directory 'vdir'

# Multiple arguments
$ mkdir d1 d2
$ rmdir d1 d2
# Both removed if empty
```

---

## Test Program

We provide `rmdirtest` to automatically check correctness.

Run it with:

```sh
$ rmdirtest
```

Expected output:

```
Test: remove one empty directory... OK
Test: remove multiple directories... OK
Test: refuse non-empty directory... rmdir: full: directory not empty
OK
Test: refuse non-directory... rmdir: afile.txt: not a directory
OK
Test: -v prints confirmation... OK
Manual: try `rmdir` with multiple args yourself in the shell.
```

---

## Notes

* `rmdir` in this implementation only removes empty directories..
* It can handle multiple directory arguments in a single call.
* The `-v` flag is optional and useful for scripts that want confirmation.
