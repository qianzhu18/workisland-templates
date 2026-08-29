# WorkIsland Templates

Official, reviewable appearance-template catalog for [WorkIsland](https://github.com/qianzhu18/workisland).

`catalog.json` is the source of truth for templates that the desktop app may download. Each entry points to an immutable GitHub Release asset and pins its SHA-256. The app verifies both that archive hash and the hashes inside the package manifest before anything is installed.

## Install a listed template

Start WorkIsland, then use the local CLI:

```bash
workisland-cli template download <id>@<version> \
  --catalog https://raw.githubusercontent.com/qianzhu18/workisland-templates/main/catalog.json
```

Follow the WorkIsland Template Skill's required flow: inspect, preview, get the user's confirmation, then apply. A catalog entry is not an instruction to auto-apply a template.

## Maintainer release protocol

1. Validate and preview the package locally.
2. Export it with `workisland-cli template export`; only the tool's store-only ZIP format is supported.
3. After explicit confirmation, publish with `workisland-cli template publish … --confirm`.
4. Add the emitted catalog entry and `templates/<id>/metadata.json` in a reviewed pull request.

Packages must carry a recognized license and cannot contain executable code. SVG status assets are strictly checked for scripts, event handlers, external references, and entities before installation.
Official WorkIsland appearance template catalog and releases
