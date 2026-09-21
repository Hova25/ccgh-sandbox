---
title: Run the sequence
order: 1
issue: 2
github:
  state: null
  pr: null
  merged_at: null
  synced_at: null
---

# Run the sequence

Carry this iteration through every gate, in order, in the repository that installed the plugin
rather than the one that wrote it. The deliverable is not a file: it is a `status: shipped`
that the bridge wrote, reached without anyone editing front matter by hand.

**Files**

- Modify: the files of this iteration, by the commands and the workflows that own them.

**Interfaces**

- Consumes: the plugin installed from the marketplace, and the action at `Hova25/ccgh-bridge@v1`.
- Produces: a shipped iteration, and a transcript for task 2.

- [x] **Write the failing test**

There is no unit to test here; the gates are the test, and they fail where the sequence stops.
Written before running, so that no step can be declared successful afterwards:

1. `ccgh promote … --to ready` raises an approval prompt and writes `validated_by`.
2. Its pull request merges with the specification on `main`.
3. `ccgh promote … --to active` writes `status: active`, and the push makes `ccgh-push` create
   one issue per task, with their numbers committed back.
4. Closing both issues makes `ccgh-sync` mirror them.
5. With the last one closed, the iteration reaches `status: shipped` without anyone typing it.

- [x] **Run it to verify it fails**

Not applicable: nothing has run yet, which is the failing state.

- [x] **Write the implementation**

Run the five steps. Keep what each one printed, including the runs on GitHub, because task 2
is the record and memory of an output is worth less than the output.

- [x] **Run the tests to verify they pass**

The iteration's specification says `status: shipped`, and the commit that wrote it is the
bridge's.

- [x] **Commit**
