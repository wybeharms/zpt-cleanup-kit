# What good looks like

A successful cleanup is proportional to the person's goal.

## Quick Cleanup

- A few clearly stale applications, installers, or large artifacts are understood.
- Only approved exact targets change.
- No folder restructuring or deep state cleanup occurs.

## Free Up Space

- The biggest defensible physical recoveries are prioritized.
- Active tools, environments, profiles, projects, credentials, and agent state remain intact.
- Rebuild and reinstall paths are documented.

## Organize Files

- Important areas have obvious homes and readable names.
- Current and proposed trees make the change understandable.
- Shared, cloud-synced, mixed-purpose, and unique folders are handled conservatively.
- Copies are verified before originals are retired.

## Full System Audit

- Filesystem layers, applications, packages, runtimes, caches, projects, cloud boundaries, credentials, and agent state have documented owners.
- Every candidate has importance, risk, and decision labels.
- Exact manifests and phase results are preserved for future agents.

## Universal standard

- The person chose the scope.
- Chat stayed concise.
- The investigation was deep enough for that scope.
- Nothing changed without approval.
- Uncertainty became Hold.
- Physical recovery was measured honestly.
- Protected data was verified after every phase.
- Harmless residue was allowed to remain when removal offered no meaningful benefit.

## Cache Boundary Checks

Use these cases to review a cache proposal before release:

- Spotify has large web caches and offline music: only the approved renderer-cache children are eligible, and offline-media files remain intact afterward.
- Claude Desktop or a Cowork helper is active: its cache group stays on Hold rather than stopping the app or deleting its enclosing support folder.
- npm has an active npx tool: a download-cache cleanup preserves the execution environment and installed packages.
- A staged app update has an active updater: the update stays on Hold, even when the staging directory is large or old.
- Another agent is running and a browser is explicitly excluded: neither its profile nor the excluded browser is silently added to the batch.
- A read-only audit requests package verification: a command that garbage-collects cache data is treated as a mutation and is not run without authorization.

Review the actual candidate contents, process and open-file evidence, planned targets, and protected-state checks. Passing a frontmatter validator alone does not establish these outcomes.
