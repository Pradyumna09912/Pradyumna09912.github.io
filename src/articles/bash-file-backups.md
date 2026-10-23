---
title: Backing Up Files with Bash
description: Learn how to create a simple file backup script using Bash.
category: LINUX · BASH
readingTime: 3
articleType: Practical Guide
---

## Why automate backups?

Manually copying files can become repetitive and easy to forget. A Bash script can automate routine file operations and make them more consistent.

## A simple example

Suppose you have a directory containing text files and want to add a backup prefix to their filenames.

```bash
#!/bin/bash

for file in "$1"/*.txt
do
    [ -e "$file" ] || continue
    mv -- "$file" "$1/backup_${file##*/}"
done
```

The script loops through `.txt` files in the directory supplied as the first argument. It adds `backup_` to each filename.

For example, `notes.txt` becomes `backup_notes.txt`.

## Test carefully

The `mv` command renames files rather than creating copies. For a real backup, copying files with `cp` or using a dedicated backup tool may be more appropriate.

Always test scripts on sample files before using them on important data.

