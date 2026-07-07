# Fable Mode — Claude Code plugin

Makes Claude (any model, including Opus 4.8) operate with the judgment, planning,
verification, and reasoning habits of Claude Fable 5: evidence before assertions,
outcome before detail, root cause before patch.

## Install

This repo is both the plugin and its marketplace, so installation is two commands
inside Claude Code:

**From GitHub** (after this repo is pushed, replace `<user>/<repo>`):
```
/plugin marketplace add <user>/<repo>
/plugin install fable-mode@darya-plugins
```

**From a local copy of this folder:**
```
/plugin marketplace add C:\path\to\fable-mode-plugin
/plugin install fable-mode@darya-plugins
```

## Use

Say one of these in any prompt:

- `fable mode — fix the crash in demo.py`
- `debug this like fable`
- `with fable: review this plan`

Claude then follows the Fable contract: verifies fixes by re-running the original
failure end to end, treats your diagnosis as a hypothesis, reports outcome-first
with faithful status (failures shown, not softened), and never ends on a deferred
promise.

## What's inside

```
.claude-plugin/
  plugin.json         # plugin manifest
  marketplace.json    # lets this repo double as its own marketplace
skills/
  fable-mode/
    SKILL.md          # the skill itself
```

The skill is plain markdown — outside Claude Code (API, claude.ai, other tools),
paste the body of `skills/fable-mode/SKILL.md` into the system prompt.

## Updating

Bump `version` in `.claude-plugin/plugin.json` when the skill changes; installed
copies update via `/plugin update fable-mode` (or automatically on marketplace
refresh).

## Uninstall

```
/plugin uninstall fable-mode
```
