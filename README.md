# irc-logs
This space intentionally left blank.

# HexChat Log Backup Scripts

Welcome to a small but mighty collection of backup scripts designed specifically for HexChat logs.
This repo reflects a progression of backup strategies, starting simple and gradually leveling up
with smarter log management for long-term sanity.

---

## 🧠 Philosophy

IRC logs are digital fossils—sometimes hilarious, sometimes haunting, always worth preserving.
But without structure, those `.log` files pile up like forgotten pizza boxes. This project is all
about:

- 🔒 Keeping consistent backups of key channels
- 📦 Compressing older logs to save space
- ♻️ Rotating backups to avoid infinite log bloat
- 🧹 Keeping the most useful, minimal set of versions for everyday access and historical needs

---

## 📂 Script Overview

### `Hexchat Log Backup`
The OG script. Simple `cp` operation backing up two key log files to a static location.
No timestamps, no compression—just overwriting the existing file each run.

### `Hexchat Log Backup (rsync)`
An efficient upgrade. Uses `rsync --inplace` to only copy changed parts of the file,
ideal for large, append-only IRC logs. Lightweight and fast.

### `Hexchat Log Backup (rotated)`
Introduces **rotation**:
- Keeps a `.log` for the current version
- Backs up older versions as `.1.log`, `.2.log`, ... up to a configurable max (default: 5)
- Replaces special characters in filenames to ensure compatibility

### `Hexchat Log Backup (rotated + Compressed)`
The final form (for now):
- Rotates and **compresses** older logs with `.gz`
- Keeps a clean `file.log` for the latest copy
- Also makes a **dated** version (e.g., `#channel_2025-05-21.log`) to archive daily snapshots

---

## 📛 About the Numbering

Backup numbering is classic log rotation style:
- `file.log` = today's backup
- `file.1.log.gz` = yesterday's
- `file.2.log.gz` = two days ago
- etc.

This format keeps things predictable and script-friendly while saving space via compression.

---

## ⚙️ Customizing
Each script is self-contained and editable. You can tweak:
- Number of backups to keep (`MAX_BACKUPS`)
- Source log file paths
- Destination folder
- Whether to use compression or not

---

## 🧪 Future Additions
Possible features down the line:
- Auto-trimming logs past X days
- Git integration for versioned commits
- Email or push notifications when logs are backed up

---

## ✍️ Author
oldtowneast  
📍 Wisconsin-based command line crusader and meat department philosopher  
😸 Sidekick: Shadow the rescue kitten  

---

## ☕ License
DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE

---

Stay nerdy, stay organized. o7