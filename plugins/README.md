# PKA Plugin Authoring Guide

PKA plugins add optional capabilities without modifying core PKA files.
Each plugin is self-contained under `plugins/<name>/` and declares what it
requires and provides through `plugin.yaml`.

## Layout

```text
plugins/
  registry.yaml
  <name>/
    plugin.yaml
    README.md
```

## Registry

Installed plugins are tracked in `plugins/registry.yaml`.

```yaml
plugins:
  - name: example
    version: 0.1.0
    category: integration
    path: plugins/example
```

An empty registry is valid:

```yaml
plugins: []
```

Plugin stubs may exist in `plugins/` without being installed. A plugin is
installed only when it appears in `registry.yaml`.

## Manifest

Each plugin provides `plugins/<name>/plugin.yaml`.

```yaml
name: string
version: semver
description: string
category: communication | memory | compute | ui | integration
platform: any | windows | linux | mac
requires:
  - type: python | node | env
    value: string
provides:
  agents: []
  hooks: []
  scripts: []
  capabilities: []
entry: optional/path/to/install-or-setup-script
docs: README.md
```

## Rules

- Plugins never edit core PKA files directly.
- Plugins declare all new agents, hooks, scripts, and capabilities in the
  manifest before installation.
- Plugins may be platform-specific, but the manifest must say so.
- Plugin setup scripts are optional and must be idempotent.
- Plugin docs must explain what the user gets, how to install it, and how to
  validate it.
- Core PKA validation must remain green after installing or removing a plugin.

## Categories

- `communication` — messaging, terminal, voice, or interaction channels
- `memory` — external memory, RAG, retrieval, or knowledge integrations
- `compute` — model runtimes, workers, queues, or execution backends
- `ui` — dashboards, trays, browser surfaces, or local interfaces
- `integration` — third-party APIs, CLIs, sync tools, or glue systems
