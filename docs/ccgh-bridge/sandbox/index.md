---
title: Sandbox
summary: What this repository is for — being a consumer of ccgh-bridge, so that the install path is exercised by something that did not write it.
---

This repository has no product. Its work is to be someone else's user: it installs the plugin
from the marketplace, runs the workflows `ccgh init` writes for it, and carries iterations
through the lifecycle the same way any project would.

That matters because the plugin's own repository cannot test this. There, the action resolves
from the checkout, the plugin loads from a directory and the command is on the PATH because the
directory is the plugin. Here, none of that is true, and each of them had to work for the first
time.
