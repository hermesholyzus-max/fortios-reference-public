---
name: fortios-reference
description: "Use when configuring FortiOS 7.4.13."
version: 1.0.0
author: Sora
license: Internal reference
metadata:
  hermes:
    tags: [fortigate, fortios, 7.4.13, networking, firewall, vlan, dhcp, vpn]
---

# FortiOS 7.4.13 Reference

Use this skill for general FortiOS 7.4.13 configuration, verification, and troubleshooting across FortiGate models.

## Retrieval rule

Do not load the complete guide into context. Read `references/index.md`, identify the relevant topic and page range, then search or read only that topic's `.txt`/PDF reference. Treat the live FortiGate configuration as authoritative when it conflicts with the guide.

## Scope

- Source guide: FortiOS 7.4.13 Administration Guide
- Official source URL is recorded in `references/index.md`.
- Topic references are generated from the official PDF and retain original page numbers.
- Use the guide to verify syntax and GUI paths; inspect live configuration before changing anything.

## Safety

Before a state-changing FortiGate operation: preserve a rollback path, make the smallest change, read the exact object back, and test management access, interfaces, routes, and policy behavior. Never copy a full configuration between different FortiGate models without adapting interfaces, device-specific settings, secrets, certificates, and topology.

## Shared reference library

The shared Google Drive reference library is:
`https://drive.google.com/drive/folders/1rgjbKhBiBb9hg9gXX5-nIYm_MRfGRVjV`

Treat the shared Drive URL as the `fortios-reference` root itself; do not invent an additional `FortiOS Reference/FortiOS 7.4.13` parent path or a `topic-pdfs/` directory. Open `START_HERE.md` first, then use `AGENT_USAGE.md` for the shared-agent procedure and `HERMES_AGENT_PROMPT.md` as the copy-ready context prompt for another Hermes agent. Start with `references/index.md`, then read only the relevant `.txt` topic file; use the matching PDF only for GUI screenshots, tables, or exact visual layout. The root should contain `START_HERE.md`, `AGENT_USAGE.md`, `HERMES_AGENT_PROMPT.md`, `SKILL.md`, `references/`, `scripts/`, and `source/`; the original guide is under `source/`, while each topic `.txt` and `.pdf` is directly under `references/`.

When verifying a Drive share, inspect the rendered file listing rather than trusting page text alone because Drive virtualizes its rows. Confirm the root contains the manuals plus `references/` and `source/`, then inspect the nested folders and open/download at least one text manual and one reference listing before declaring the library usable. Treat folder listing access and file-content access as separate checks: a session may see names while still lacking a usable file-content path. Before editing, verify write access: if New/upload controls are disabled or a document shows `Request edit access`, treat the session as read-only and do not claim the Drive update succeeded. For each agent that will use the library, verify its own authenticated browser/connector session by opening `START_HERE.md` and `references/index.md`; if it can only list files, give it the copy-ready prompt or direct file-download paths rather than assuming the reference is readable. A logged-in browser can open Markdown files in Drive's Docs viewer, while an anonymous or browser-only agent may need an authenticated session or direct download URL.

The shared reference architecture is split by artifact type: use GitHub as the versioned source of truth for Markdown, prompts, `SKILL.md`, text references, and scripts; use Google Drive for the original Administration Guide, topic PDFs, and archive copies. Keep the two trees structurally aligned, but do not duplicate large PDFs into GitHub unless Git LFS is explicitly chosen. When validating a mirror, verify both the repository tree and the Drive file-content path; a folder listing or a successful browser login alone is not enough.

## Repository validation workflow

When an agent is given the GitHub repository, validate access and reading in this order:

1. Open the repository root while authenticated; treat a private-repository login wall as an access failure, not as permission to infer contents.
2. Open and read `START_HERE.md`.
3. Open and read `HERMES_AGENT_PROMPT.md`.
4. Open and read `AGENT_USAGE.md`.
5. Open and read `references/index.md`.
6. Follow the topic map and open at least one relevant `.txt` file; verify that its content renders, not merely that its filename appears in the tree.
7. If any step fails, report the exact inaccessible path and stop reference-based advice rather than guessing.

For local artifact checks, compile `scripts/build_reference.py`, then assert that all eight topic `.txt`/`.pdf` pairs exist, each text file contains a `FortiOS 7.4.13 PDF page` marker, and representative routing terms are present in the expected topic files. Run the same ordered file-content check against every authenticated agent session that will consume the private repository; one successful browser session does not prove access for another agent.

The deterministic topic-splitting script is `scripts/build_reference.py`; use it as a direct script to regenerate the topic PDFs/text and update `references/index.md` when the source guide version changes. Its current implementation uses fixed local paths and does not provide a reliable CLI option interface, so do not assume `--help`, `--source`, or `--output` flags exist. Keep each FortiOS version in its own reference tree.

## Keep the reference model-neutral

This library is a general FortiOS 7.4.13 guide, not a record of one user's devices. Before publishing or syncing, scan Markdown, prompts, skill metadata, and `references/index.md` for user-specific model names, hostnames, IP addresses, ports, topology constraints, and device-state assumptions; replace them with generic verification rules. Do not remove ordinary example addresses from the official topic extracts merely because they look private: preserve them when they are part of the source guide and are not user-specific.

## Sync and verification workflow

1. Edit and review the local source tree first; scan Markdown and prompts for user-specific models, addresses, hostnames, topology, and embedded cloud links before publishing.
2. Create a fresh staging directory from the current edited tree. Print staged paths and hashes before any browser upload; never reuse a stale upload directory because the browser file picker can remember it silently.
3. Upload root files from the repository root and `references/index.md` from inside `references/`, because GitHub preserves the current upload directory rather than the local source tree.
4. Commit each logical batch with a descriptive message.
5. Read the committed GitHub files back and confirm the actual rendered wording and links; a successful upload page or new commit alone is not proof that the intended file contents were uploaded.
6. For Google Drive, first determine whether the opened folder is writable: disabled New/upload controls or `Request edit access` means read-only. Do not claim an update succeeded and do not create duplicate files in that folder.
7. If the user wants an independently editable Drive copy and the shared folder is read-only, leave the original shared folder untouched, create a clearly named folder in the authenticated account's My Drive, upload the current local reference tree there, and verify the resulting root, nested folders, and at least one rendered manual.
7. Update every embedded Drive URL in the local Markdown to the new owned folder before the final sync, then replace the corresponding GitHub files and re-open them. Verify Drive and GitHub separately; matching names or timestamps are not content verification.
8. If other agents must consume the owned Drive copy without a shared-account login, set the folder's general access to `Anyone with the link` / `Viewer`, copy the exact folder URL, and verify the sharing dialog shows the new access state before reporting it as usable. Do not grant Editor access unless collaborative editing is explicitly required.
9. If uploading a whole local directory creates an outer wrapper folder plus the intended reference root, link and document the actual inner root that contains `START_HERE.md`; do not embed the wrapper URL while claiming the root is directly below it.
10. Treat the original user-owned shared folder as a separate source: leave it untouched when it is read-only, and never delete it merely to avoid confusion. The independently owned copy becomes the maintained distribution target.

## Topic routing

- Interfaces/VLAN/DHCP/routing: `references/network.txt`
- Firewall/address objects: `references/policy-and-objects.txt`
- Security profiles: `references/security-profiles.txt`
- IPsec VPN: `references/ipsec-vpn.txt`
- SSL VPN: `references/ssl-vpn.txt`
- Administrators/SSH/backups/system: `references/system.txt`
- Diagnostics: `references/troubleshooting.txt`
- Beginner workflow: `references/getting-started.txt`
