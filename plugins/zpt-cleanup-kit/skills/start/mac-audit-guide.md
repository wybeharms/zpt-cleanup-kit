# macOS audit guide

Use only the modules included in the approved cleanup package. Version 1 is macOS-specific.

## Evidence rules

- Prefer read-only filesystem metadata when it answers the question.
- Record allocated physical size, not only logical size.
- Report totals as lower bounds when macOS privacy controls block parts of the scan.
- Never print secret values, private keys, tokens, cookies, database contents, or browser history.
- Search references by exact path, application identifier, package identifier, executable name, and configuration owner.
- Check processes, open files, launch services, background items, package receipts, command links, scheduled tasks, and project references where relevant.
- Resolve symbolic links. A link alone does not prove that its target exists.
- Recheck every proposed target immediately before a change.

## Module A: Mac and storage map

Explain and map:

```text
/
├── Applications/       shared application bundles
├── Library/            shared frameworks, support, helpers, and services
├── System/             protected macOS components
└── Users/<account>/
    ├── Applications/   account-only applications
    ├── Desktop/        possibly cloud-synced
    ├── Documents/      possibly cloud-synced
    ├── Downloads/
    ├── Library/        account application data and state
    └── hidden folders  tool configuration, caches, histories, and credentials
```

Record the data-volume free-space baseline, cloud-synced roots, backup methods, and privacy-limited areas.

## Module B: Applications and residue

For every stale-looking application candidate:

1. Confirm whether the application bundle exists and where.
2. Check recent use only as context, never as proof.
3. Check running processes, open files, login items, launch agents, launch daemons, privileged helpers, system extensions, command links, and package receipts.
4. Follow the owner into account and shared Application Support, Containers, Group Containers, Caches, Preferences, Logs, HTTP storage, WebKit, saved state, and crash reports.
5. Search for unique recordings, exports, profiles, presets, databases, histories, and local documents.
6. Separate shared registries from owner-specific files. Do not reset LaunchServices or Background Items to erase one cosmetic record.
7. Ask a targeted use question only after the evidence suggests that the application is stale.

Dragging an application bundle to Trash is not a complete uninstall, but application residue must still be individually verified.

## Module C: Installers and packages

Review exact installer artifacts in Downloads and other approved locations. Distinguish an installer from an installed application and preserve intentional offline installers.

For package managers, separate:

- installed tools and runtimes;
- downloadable package caches;
- transient execution environments;
- package receipts and command links;
- active project dependencies;
- shared package metadata.

Preview supported cleanup when possible. A whole-cache cleanup is acceptable only when every included subtype has been reviewed and the person approves that scope.

## Module D: Python and other runtimes

For each old Python, Java, Node, Ruby, Conda, or similar runtime:

1. Identify the exact installation owner and mechanism.
2. Enumerate command links, shell path entries, package receipts, launch jobs, and scheduled tasks.
3. Find every virtual environment or project that points to that exact runtime.
4. Confirm a working replacement where appropriate.
5. Classify dependent environments separately. Removing an interpreter can silently break a retained environment.
6. Preserve operating-system shims and unrelated runtimes.

An inactive runtime may still be required by an active local tool.

## Module E: Caches and large rebuildable data

Classify cache-like paths by function:

| Category | Default |
|---|---|
| Download or artifact cache | Review for removal after rebuild source is verified |
| Exact project build cache | Review when ignored, untracked, and inactive |
| Active transient environment | Keep until pinned or replaced |
| Installed tool or runtime | Audit as software, not cache |
| Browser profile or session | Hold as unique user state |
| Public model or checkpoint | Review only after custom data is excluded |
| Agent or application state | Keep or Hold |

For project caches, verify Git tracking, ignore rules, lockfiles, active builds, and open files. Removing an exact `.next` or `node_modules/.cache` child never authorizes removing the surrounding source or dependency tree.

For an approved cache investigation, read [Cache Candidates On macOS](cache-candidates.md) as needed. It distinguishes package downloads from installed environments, Spotify web caches from offline media, Claude Desktop web caches from agent state, and inactive installer payloads from active updaters. Example paths are candidates to inspect, not preapproved removal targets. Preserve explicit exclusions and other running agent sessions.

## Module F: Folder structure and duplicates

Start with top-level counts and sizes. Read deeper only where a naming collision, large allocation, scattered copy, or unclear owner justifies it.

Check:

- duplicate names with different purposes;
- redundant source copies versus current Git repositories;
- archives that mix code with contracts, credentials, images, or business records;
- app-created scratch versus active scheduled-task pointers;
- unexpected Desktop, Documents, Downloads, or cloud-storage project roots;
- hardcoded paths that would break after a move;
- cloud or Git backup coverage.

Show current and proposed trees before any reorganization. Copy before move, verify the new location, and keep the original until the person approves retirement. Never reorganize a shared repository or team folder without its owners' context.

## Module G: Hidden folders, Libraries, integrations, and agent state

Hidden does not mean useless. Determine the owner and function of each reviewed path.

Protect by default:

- global and project agent instructions, sessions, memory, plugins, skills, and task state;
- application databases, profiles, cookies, histories, and sandbox documents;
- credentials, Keychain data, cloud configuration, and authentication archives;
- active MCP configuration, scheduled tasks, and local tool environments;
- Mail, Messages, Photos, Safari, and privacy-protected application data.

Multiple project-level `.claude` or similar folders can be normal scoped configuration. A nested hidden folder can also be an empty artifact. Inspect contents and references before classifying it.

## Module H: Credentials and cloud boundaries

Record only credential category, owner, account, path, permissions, and active references. Never record secret values.

Deleting a local credential removes local access but does not revoke the external grant. Those are separate decisions. Application cleanup does not authorize Keychain cleanup.

An archived cloud configuration can mix disposable virtual environments with credential databases and authentication logs. Preserve the parent and target only the exact reproducible child when purposes differ.

## Module I: Verification

After every approved batch:

- confirm every exact target is absent or record the exact remnant;
- confirm every named exclusion still exists;
- confirm removed jobs and helpers are not running;
- confirm retained tools report working versions;
- confirm protected environments, profiles, credentials, repositories, and agent state remain;
- inspect repository working trees for unintended tracked changes;
- measure physical storage again;
- record failures, protected metadata shells, and cosmetic shared-registry entries without broadening cleanup.
