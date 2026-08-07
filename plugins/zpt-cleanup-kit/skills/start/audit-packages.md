# Cleanup packages

Packages make the journey proportional to the person's goal. They are investigation scopes, not promises to delete anything.

## Quick Cleanup

Best for a person who wants a small win without reorganizing the computer.

Includes:

- stale-looking applications in `/Applications` and the account's Applications folder;
- obsolete installers in Downloads;
- a short list of obvious large files or folders inside the approved boundary;
- abandoned application residue only when its owner is clear and the application is absent.

Excludes by default:

- broad Library, hidden-folder, package-cache, credential, agent-state, and project scans;
- Python, Java, Node, Conda, Docker, database, or virtual-machine removal;
- folder restructuring.

## Free Up Space

Best when storage recovery matters more than folder organization.

Includes Quick Cleanup plus:

- application support and container data;
- package-manager download caches;
- exact project build caches;
- old language runtimes and dependent virtual environments;
- containers, virtual disks, local databases, models, and browser payloads;
- large logs and reproducible artifacts.

High-risk data stays separate even when it is large. Databases, virtual disks, browser profiles, credentials, and unique histories need explicit acknowledgment.

## Organize Files

Best when the problem is confusing locations rather than disk pressure.

Includes:

- selected Desktop, Documents, Downloads, cloud-storage, project, or personal roots;
- duplicate top-level names, scattered copies, loose files, and unclear archives;
- redundant code copies and repository backup checks;
- current and proposed high-level folder trees;
- optional renames, copies, moves, merges, or archival after approval.

Excludes application state, packages, runtimes, and broad cache cleanup unless the person adds them.

Copy before move when a new structure is being tested. Keep originals until the new location is verified. Cloud-synced moves and deletions may propagate.

## Full System Audit

Best when the person wants to understand the entire Mac and is comfortable with a multi-phase investigation.

Includes:

- every earlier package;
- filesystem layers and storage ownership;
- shared and account Applications and Libraries;
- hidden configuration, package state, scheduled tasks, integrations, and agent state;
- credentials and cloud-account locations without reading secret values;
- project repositories, remotes, redundant copies, and backup coverage;
- current and proposed structure;
- a durable maintenance record and future-agent handoff.

Full means broad investigation, not mandatory cleanup. Every candidate can still be Keep, Hold, or Ignore.

The default proposed boundary on a single-account Mac is `/Applications`, `/Library`, `/Users/Shared`, the current account's home folder, `/opt`, `/usr/local`, and mounted data volumes. `/System` and macOS-owned internals receive only a high-level integrity and storage review. Other account home folders, Keychain contents, secret values, personal-document contents, active databases, and browser-profile contents remain excluded unless the person gives a narrower explicit reason. Show this boundary and obtain approval before scanning it.

## Custom scope

Packages can be combined or narrowed. Examples:

- Quick Cleanup plus old Python versions
- Free Up Space without browser profiles or project folders
- Organize Files for Documents only
- Full System Audit with Mail, Photos, and cloud accounts excluded

Record the final boundary before the deep investigation begins.
