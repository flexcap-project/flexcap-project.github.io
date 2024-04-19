---
title: FlexCap
filename: fork-demo.md
--- 

# Multi-Process Application Support Demo

[Redis](https://valkey.io/) is a popular in-memory key-value store that offers the feature of saving the content of the database to disk.
This is achieved by having the main Redis server process `fork()` a child which will perform the database dump while the parent continues to serve database requests.
This feature is not supported in single address space operating systems due to the lack of support for POSIX `fork()`.

This is an attempt to save the database on disk with vanilla [Unikraft](https://unikraft.org/) (unikernel log on top, Redis admin console at the bottom):

<video src="assets/fork-demo/no-fork.mov" controls="controls" style="max-width: 900px;">
</video>

As Unikraft does not support `fork()` the operation fail.
We are working on enabling support for `fork()` and multi-process applications in Unikraft while maintaining its single address space fundamental property, by emulating processes with threads as well as enforcing isolation between emulated processes and rewriting properly memory references through the use of Morello's features.
With our early prototype, Redis is able to save its state to disk:

<video src="assets/fork-demo/with-fork.mov" controls="controls" style="max-width: 900px;">
</video>