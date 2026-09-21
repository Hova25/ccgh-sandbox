---
title: Write down what it showed
order: 2
issue: 3
github:
  state: null
  pr: null
  merged_at: null
  synced_at: null
---

# Write down what it showed

Turn the transcript into the README of this repository: what was installed, what ran, what
broke, and where each break was repaired.

A trial whose result lives in someone's memory is a trial that has to be repeated. This is the
artefact the sandbox exists to produce, and the reason it stays after the iteration ships.

**Files**

- Modify: `README.md`

**Interfaces**

- Consumes: the transcript from task 1.
- Produces: nothing. The iteration ends here.

- [ ] **Write the failing test**

The README today says what this repository is for and nothing about what it found. The test is
reading it and asking whether someone who was not here could re-run the trial from it. Today
they could not.

- [ ] **Run it to verify it fails**

Not applicable.

- [ ] **Write the implementation**

Write, in order: how the plugin was installed, what `ccgh init` produced, what each gate did,
and a list of what broke with the repository and the change that repaired it. Include the
things that worked first time — a list of only the failures reads as if nothing else was
checked.

Say plainly what this does not prove: one machine, one account, one repository with no prior
workflows, run by the people who built the thing.

- [ ] **Run the tests to verify they pass**

Someone who was not here can read the README and re-run the trial.

- [ ] **Commit**
