---
title: 🐚 Weekly Summary — Shell Programming in UNIX
summary: A report on Lab #12 — advanced bash scripting with semaphores, a custom man command, and a random letter generator
date: 2026-05-11

image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'

cover:
  image: "https://images.unsplash.com/photo-1629654297299-c8506221ca97?q=80&w=2560"
  position:
    x: 50
    y: 40
  overlay:
    enabled: true
    type: "gradient"
    opacity: 0.4
    gradient: "bottom"
  fade:
    enabled: true
    height: "80px"
  icon:
    name: "🐚"

authors:
  - me

tags:
  - Shell
  - UNIX
  - Bash
  - OS

featured: true
---

This week I completed Lab #12 — Advanced Shell Programming in UNIX. The work focused on writing complex bash scripts using logical control structures and loops.

{{< toc mobile_only=true is_open=true >}}

## Goal

Study the basics of programming in the UNIX shell. Learn to write more complex shell scripts using logical control constructs and loops.

## Task 1: Semaphore Mechanism

I wrote a shell script implementing a simplified semaphore mechanism. The script:

- waits up to time `t1` for a resource to become free, printing status messages throughout
- once the resource is free, uses it for time `t2 ≠ t1`, also printing that the resource is in use

The script was launched in one virtual terminal in the background with output redirected to another terminal (`> /dev/tty#`). The same script was run in the second terminal in normal mode. This demonstrated how two processes compete for the same shared resource.

The program was then extended to support interaction of three or more concurrent processes through a single semaphore.

## Task 2: Custom `man` Command

I implemented the `man` command as a shell script. The script:

- accepts a command name as a command-line argument
- searches `/usr/share/man/man1/` for the corresponding archive
- if found, displays the help page using `less`
- if not found, outputs a message indicating missing documentation

## Task 3: Random Letter Generator

Using the built-in `$RANDOM` variable (which produces pseudo-random numbers in the range 0–32767), I wrote a script that generates a random sequence of Latin alphabet letters. The letter was computed as:

```bash
code=$(( RANDOM % 26 + 65 ))
letter=$(printf "\\$(printf '%03o' $code)")
```

## Conclusions

Through this lab I gained practical experience with:

- process synchronization using file-based semaphores
- working with the `/usr/share/man/` directory structure and documentation format
- arithmetic operations and the `$RANDOM` variable in bash
- redirecting I/O between terminals

Shell scripting is a powerful tool for system-level automation that is difficult to replace with higher-level languages in certain scenarios.
