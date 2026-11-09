# Cache Candidates On macOS

Updated November 9th, 2026.

Read this reference when the approved scope includes package downloads, application web caches, update leftovers, or large folders labelled as caches. These are investigation examples, not a deletion list. Layouts vary across versions, accounts, and installation methods. A missing example path is not permission to remove a nearby parent.

Use the evidence and approval rules in `mac-audit-guide.md` and `risk-and-approval.md`. Resolve examples to the actual account and literal paths before proposing a change. Establish ownership and scope before following symbolic links. Keep user exclusions throughout the run, including an instruction to leave a browser or active agent alone.

## Package Download Caches

Inspect the configured cache location and installed manager version. A directory under a cache root may instead be a live execution environment.

| Owner | Candidate Subtype | Preserve |
|---|---|---|
| npm | The configured cache's `_cacache` download store | `_npx` execution environments, global packages, `.npmrc`, installed Node versions, and project dependencies |
| pip | The configured HTTP and wheel caches | Virtual environments, installed Python versions, site-packages, private source, and configuration |
| Homebrew | Verified downloaded installer archives, often under `~/Library/Caches/Homebrew/downloads` | Cellar, Caskroom, active portable runtimes, command links, configuration, and downloads in progress |
| UV | Verified downloadable artifacts with a known rebuild source | Tools, environments, unpinned executions, and packages currently imported from the cache |

Prefer supported manager operations when their effect matches the approved targets. Check the installed implementation or current official documentation before execution:

- npm distinguishes its ordinary download cache from its npx cache. `npm cache clean --force` is a space-recovery action, not a routine repair requirement. `npm cache verify` can garbage-collect files, so it is not a read-only audit command.
- `pip cache purge` removes cached items rather than installed packages. Confirm the selected interpreter and cache directory first.
- Homebrew cleanup can remove old installed versions as well as downloads. A preview is useful, but approval for downloaded archives does not authorize every item in a broad cleanup preview. If no supported operation fits, propose only exact, verified archive paths.
- Preserving installed dependencies avoids unnecessarily stopping current work. It does not guarantee a later install can run offline after downloads are removed. Hold custom builds or artifacts whose only recovery source is the cache.

Check active installation, download, build, and open-file state immediately before removal. Do not delete temporary downloads that are still being written. Some manager information commands rotate logs; prefer filesystem metadata during a strictly read-only audit when it answers the question.

## Spotify Web Caches

Spotify stores streaming cache and intentionally downloaded offline media. A combined storage total is not a removable-cache estimate.

Prefer the application's current Clear Cache control when it can clear the approved subtype. Measure the result; do not assume it clears every web-renderer cache. Separately investigate these version-dependent macOS web-cache children when large:

- `~/Library/Caches/com.spotify.client/Browser/Cache`
- `~/Library/Caches/com.spotify.client/Default/Cache`

Before proposing a filesystem operation, inspect the actual children and confirm they are renderer cache data. Check Spotify and its helpers, open files, and custom storage locations. Quit the app normally before an approved filesystem cleanup; do not force-stop an application holding unsaved work.

Preserve account profiles, login state, preferences, offline music and podcasts, and the app's other storage. A path such as `~/Library/Application Support/Spotify/PersistentCache/Storage` can contain offline media. Neither `PersistentCache` nor the whole Spotify support or cache root is covered by approval for the two web-cache children.

Verify that the approved web caches are absent or small and that offline-media locations and account data remain. Cache files may regenerate, and the next load may be slower. Restart the app only when authorized and when doing so will not disrupt other work.

## Claude Desktop Web Caches

Investigate only demonstrated renderer cache data, commonly in these macOS children:

- `~/Library/Application Support/Claude/Cache`
- `~/Library/Application Support/Claude/Code Cache`

Confirm the owning application and current directory contents. An Electron-like name alone is insufficient evidence. Require Claude Desktop and relevant helpers to be closed, and check for open files before an approved filesystem cleanup. Desktop and command-line installations may have different owners and live state.

Preserve the enclosing support directory, IndexedDB, Local Storage, Session Storage, account data, conversation and agent-session folders, Cowork virtual-machine bundles, runtime installations, and exports. Preserve the separate `~/.claude` configuration, skills, memory, sessions, plugins, and scheduled tasks. Clearing a web cache is not a reset, reinstall, or history cleanup.

Verify protected state separately from the removed cache. Do not claim that conversations, sign-in, or the full application were functionally tested merely because protected files still exist. Cache cleanup on one computer does not prove these paths or effects for every release.

## Update And Runtime Install Leftovers

Agents may find large staged application updates under an updater's cache, or an archive beside a runtime installer staging directory. Distinguish the downloaded payload from installed software and from an update still in progress.

Record the owner, version, source, exact artifact, active updater or installer, open files, references, and installed replacement. A staged app bundle may still be the next update or even be running from its staging path. Hold it while installation is active. Do not stop another agent's app or updater just to reclaim space.

An installed runtime can live beneath a directory named `.cache`. Do not remove that directory to clear one old archive. An isolated installer payload is only a candidate after its active installer and references are excluded and the retained runtime is verified.

## Large Data To Hold

- Browser cache partitions can also contain cookies, profiles, sign-in state, or tool sessions. Classify exact children; never clear a whole browser or agent profile based on its location under Caches.
- Agent transcripts and history databases are working data. Archival names, dates, compression, or size do not make them disposable. Account for compressed copies and changed layouts before judging a backup redundant.
- Meeting and dictation apps may keep a large live database, recordings, and a separate recovery database. A recent database backup is not a duplicate merely because it is similar in size to the live database.
- Virtual machines, custom models, offline media, generated deliverables, and project dependencies require their own decision and authority. Do not absorb them into cache cleanup.

## Verification And Reporting

Keep candidate allocation, space moved to Trash, and measured free-space change separate. Moving files to local Trash normally does not release their storage. Never empty unrelated Trash contents to complete a cache-only task. Permanent removal of proven rebuildable data needs the corresponding explicit scope and consequence recorded.

Recheck active use immediately before each approved group. Stop or skip a changed target and complete unaffected approved work. Compare protected data and tool availability afterward without opening private databases or changing running sessions. Report failed and partially completed groups explicitly. On a busy computer, concurrent builds, copy-on-write sharing, and app activity can make a volume-wide free-space delta differ from allocation removed; do not count that difference as extra recovery.

## Official References

Manager semantics and Spotify's storage distinction were checked November 9th, 2026. Exact Claude cache children and updater examples are inspection patterns, not vendor guarantees. Recheck current versions and documentation before applying them elsewhere.

- [npm Cache](https://docs.npmjs.com/cli/v11/commands/npm-cache/)
- [pip Cache](https://pip.pypa.io/en/stable/cli/pip_cache/)
- [Homebrew Cleanup](https://docs.brew.sh/Manpage#cleanup-options-formulacask-)
- [Spotify Storage](https://support.spotify.com/us/article/storage-information/)
