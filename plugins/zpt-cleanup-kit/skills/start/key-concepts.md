# Key concepts

Use these explanations only when relevant. Keep each teaching moment to two or three lines.

## Root and home are different

`/` is the Mac's filesystem root. `~` is one account's home folder, such as `/Users/<account>`. Shared Applications and Library folders live near root; account-specific versions live inside the home folder.

## Library is not junk

`~/Library` mixes caches with settings, histories, databases, cloud containers, and sandboxed documents. `/Library` contains shared frameworks, helpers, and services. `/System/Library` is protected operating-system content.

## Application files are distributed

An application can leave support data, containers, preferences, helpers, command links, and launch jobs outside its application bundle. A complete uninstall follows one verified owner across those locations.

## Hidden folders are normal

Development and agent tools use hidden folders for configuration, sessions, package state, credentials, and project permissions. A leading period says nothing about value.

## Cache is a location label, not a safety label

A cache can be a downloadable archive, an active execution environment, a browser profile, a model, or agent session state. Rebuild source and active use determine whether removal is safe.

## Cloud sync changes the consequence

Deleting or moving an item in iCloud, Dropbox, OneDrive, or Google Drive can propagate to other devices and collaborators. Local Trash behavior may not be the only recovery path.

## Logical size and physical size differ

Virtual disks and sparse files can claim a large logical capacity while occupying less physical storage. Report actual allocated recovery whenever possible.

## Local tools can support cloud applications

A local command or MCP can help inspect or administer a service that runs in AWS, Google Cloud, or another platform. Local presence does not prove that production runs on the Mac, and local deletion can still break a workflow.

## Agent state is working data

Agent configuration, sessions, attachments, memory, plugins, and scheduled tasks are not generic clutter. Protect them unless the owning product and consequence are understood.
