# Risk and approval model

Each candidate receives three independent labels. Do not collapse them into one judgment.

## Importance

| Label | Meaning | Default treatment |
|---|---|---|
| Critical | Active, unique, credential-bearing, personal, legally important, or required by a current project or agent | Keep |
| Useful | History, preferences, an older project, a profile, or state that may still matter | Keep or Hold |
| Replaceable | Reinstallable or reproducible from a verified source | Candidate for Remove |
| Negligible | Empty shell, stale pointer, ordinary log, or confirmed technical residue | Remove or Ignore |

Size and age do not determine importance.

## Removal risk

| Label | Typical target | Required treatment |
|---|---|---|
| Low | Old installer, exact abandoned-app cache, ordinary log | Exact path, ownership and active-state check |
| Medium | Application settings, runtime, virtual environment, editor history, redundant repository copy | Rebuild or backup evidence plus explicit approval |
| High | Database, virtual disk, browser profile, Keychain item, credential, unique history, cloud-synced archive | Separate approval and irreversible-loss statement |
| Prohibited | Current project, personal document, active credential, whole Library, whole home folder, system root, broad wildcard | Stop unless the person gives a new exact scope |

Risk measures the consequence of a mistake. A tiny credential can be High risk. A large installer can be Low risk.

## Decision

| Label | Meaning |
|---|---|
| Keep | Active, useful, unique, protected, or intentionally retained |
| Remove | Exact obsolete target with understood consequences and approval |
| Hold | Dependency, purpose, backup, or owner intent remains unclear |
| Ignore | Harmless residue whose cleanup benefit is smaller than the risk or effort |

Unknown defaults to Hold. Protected categories default to Keep.

## Approval gates

1. Approve the deep read-only investigation boundary and package.
2. Approve the proposed execution phases.
3. Approve each exact change manifest.
4. Approve each High-risk target separately.
5. Approve administrator-owned work separately, after the exact privileged paths and expected dialog are shown.
6. Reapprove any target whose contents, state, or consequence changed after the manifest was prepared.

A broad phrase such as “remove technical residue” applies only to the exact audited manifest presented with it. It never authorizes newly discovered paths, adjacent documents, credentials, databases, or shared registries.

## Manifest template

```markdown
### <component>

- Exact target: `<literal path or identifier>`
- Physical size: <allocated size>
- Contents: <plain description>
- Importance: <Critical / Useful / Replaceable / Negligible>
- Removal risk: <Low / Medium / High / Prohibited>
- Decision: <Keep / Remove / Hold / Ignore>
- Active-state evidence: <application, process, service, reference, open-file findings>
- Irreversible loss: <exact consequence or none>
- Exclusions: <similar paths that remain protected>
- Prerequisite: <stop app, unload service, authenticate, export, or none>
- Recovery: <reinstall, rebuild, backup restore, or none>
- Approval: <pending or exact approved batch>
```
