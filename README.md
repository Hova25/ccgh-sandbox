# ccgh-sandbox

A repository whose only purpose is to be a consumer of
[ccgh-bridge](https://github.com/Hova25/ccgh-bridge), so that its install path is exercised by
something other than itself.

It was created empty, on purpose. A fork would have inherited the plugin repository's settings,
content tree and workflows — which is the coupling the trial exists to test against.

## How it was installed

```
/plugin marketplace add Hova25/ccgh-bridge
/plugin install ccgh@ccgh-bridge
ccgh init
```

Nothing else. No clone of the plugin, no path configured, no token supplied. `ccgh init` wrote
five workflows pointing at `Hova25/ccgh-bridge@v1` and recorded that reference in `ccgh.json`.

## What worked the first time

The plugin installed from the marketplace by name, and `ccgh` answered in a session here with
no flags. Its dependencies were installed with it: the command runs from
`~/.claude/plugins/cache/ccgh-bridge/ccgh/1.0.0`, which has its own `node_modules`.

`ccgh validate` refused and named **this** repository's path, which is the proof that it
resolved the project it was run in rather than the directory it lives in.

The five workflows resolved `Hova25/ccgh-bridge@v1` on GitHub's runners. The action installed
Bun, installed its own dependencies, and ran `ccgh` — the consumer's checkout is not a
JavaScript project and never needed to be.

The bridge created one issue per task and committed their numbers back onto the iteration
branch. It supplied its own token: nothing here was configured for it.

## What broke

**A repository that has just run `ccgh init` has a red build.** The first push after
initialising fails, because `ccgh validate` refuses a repository with no content directory —
which is every repository that has just started. Repaired in `ccgh-bridge`, not here: a defect
in someone else's code fixed from inside their user is how a workaround becomes permanent.

## What this does not prove

One machine, one account, one repository that had no workflows of its own. Bun was already
installed. And the trial was run by the people who built the thing, which catches what is
broken and cannot catch what is merely confusing.
