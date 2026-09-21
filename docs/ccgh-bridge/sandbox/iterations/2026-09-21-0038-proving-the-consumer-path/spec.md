---
title: Proving the consumer path
status: shipped
depends_on: []
impacts: []
validated_by: hovannes
validated_at: '2026-09-21T00:39:42.372Z'
launched_by: hovannes
launched_at: '2026-09-21T00:40:20.050Z'
launched_tasks:
  - tasks/01-run-the-sequence.md
  - tasks/02-write-down-what-it-showed.md
---

# Proving the consumer path

## Problem

This repository installed a plugin and ran a command, and that is all anyone knows. The
lifecycle it exists to exercise — scaffold, write, validate, promote, launch, mirror, close,
ship — has never run anywhere except the repository that wrote it, where every step was
reached through a local path.

Something already went wrong and it is worth stating as evidence rather than as a worry: the
first push, immediately after `ccgh init`, failed. The workflow resolved the action from the
tag and ran it correctly; `ccgh validate` refused because there was no content yet. A
repository that has just installed the plugin therefore has a red build before it has done
anything wrong.

## Goals

One iteration here reaching `status: shipped`, written by the bridge, with its issues created
and closed by the workflows rather than by hand.

Every step of that sequence observed and written down, including the ones that worked, because
"it worked" is only useful when someone recorded what it looked like.

The defects it exposes named, with the repository where each was repaired.

## Non-goals

**Repairing the plugin from here.** A defect in `ccgh-bridge` is repaired in `ccgh-bridge`,
where its tests are. This iteration names them.

**Testing the plugin's features.** They have tests already. What has no test anywhere is the
sequence, reached through an installed plugin and a tagged action.

**Publishing a site.** This repository has nothing worth publishing yet, and `ccgh init`
writes no pages workflow for a repository that has not said where it publishes.

## Contract

The sequence, in order, and what each step must produce:

| Step | Must produce |
| --- | --- |
| `ccgh scaffold iteration` | a brainstorm, a specification, and a reference |
| `ccgh validate` | acceptance of the written content |
| `ccgh promote … --to ready` | `status: ready`, an approval prompt, `validated_by` |
| `ccgh promote … --to active` | `status: active`, and a push the bridge reacts to |
| `ccgh-push` | one issue per task, and their numbers written back |
| closing the issues | `ccgh-sync` mirroring the state |
| the last one closed | `status: shipped`, written by the bridge |

Nothing in this repository is configured beyond `ccgh.json`, which carries only `action`. If a
step needs more, that is a finding.

## Failure modes

**An empty repository fails its own validation.** Observed. Recorded in the plugin's
repository; the repair is not here.

**The bridge has no token.** The action supplies one by default. If a consumer has to add
anything, that is a finding.

**The bridge writes to a branch that is gone.** It opens `bot/ship/<reference>` instead, which
a human merges. Worth seeing once here rather than reading about it.

## Risks

**One repository, one machine, one account.** Nothing here proves the path works for someone
else's Bun, someone else's permissions, or a repository with existing workflows.

**The sequence is being run by whoever built it**, which is the weakest kind of user test. It
catches what is broken; it cannot catch what is merely confusing.

## Open questions

None blocking.
