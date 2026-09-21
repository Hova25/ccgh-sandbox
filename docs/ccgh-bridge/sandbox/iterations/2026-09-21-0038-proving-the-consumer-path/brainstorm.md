---
title: Proving the consumer path
date: 2026-09-21
participants:
  - hovannes
  - claude
---

# Proving the consumer path

## What prompted this

A repository was created to be a user of `ccgh-bridge`, and being a user means carrying at
least one iteration the whole way. Until that happens, everything installed here is untested in
the only way that counts: the lifecycle running end to end in a repository that did not write
it.

The plugin's own repository cannot do this. There the action resolves from the checkout, the
plugin loads from a directory, and the command is on the PATH because the directory is the
plugin. Here none of that holds, and each had to work for the first time.

## What was considered

**What this first iteration should be about.** A placeholder would prove that files can be
written and nothing else. The work chosen is the only work this repository has: recording what
it is for, and what its own existence proved about the plugin. That is genuinely useful here,
and it is what any repository's first iteration looks like — writing down what it is before
writing anything else.

**Whether to test the plugin's features or its lifecycle.** The features already have tests in
the repository that owns them; running them again here would duplicate without adding. What has
no test anywhere is the sequence: scaffold, write, validate, promote, launch, mirror, close,
ship, in a repository reached through an installed plugin and a tagged action. That sequence is
the subject.

**Where a defect found here gets repaired.** Not here. A defect in the plugin is repaired in
the repository that owns its tests; this iteration records what was observed and names where
the repair went. Fixing someone else's code from inside their user is how a workaround becomes
permanent.

## Not settled here

Whether this repository keeps existing after the path is proved. It costs nothing, and it is
the only place the consumer path can be re-tested when the plugin changes, so the default is
that it stays.

Whether a consumer should be expected to enable GitHub Pages, supply a token, or do anything
else by hand before the workflows work. This iteration finds out; nobody knows yet.
