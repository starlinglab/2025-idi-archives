# Gloria Steinem archive

Work in progress.

All available SHA-256 hashes from GDrive were collected into `sha256_hashes_no_shortcuts_sorted_public.txt`.

That file contains many empty lines at the end (for now), for all the files without SHA-256 hashes. These are Google Workspace files, or files Google just didn't hash for some reason. This is 688 files out of the total.

Total files (including errors): 35,585

## Root hashes

These are the SHA-256 hashes of all the hashes, representing the whole archive at once.

```
459a41c3a17c48ff3772d1555582be1b83b34711d22024e9dd49722fb93435df  md5_hashes_no_shortcuts.txt
495d4025e251b609e96eaf63cad4ad218c32affe8dd19346d4a7ddcdfb4579c3  sha256_hashes_no_shortcuts_sorted_public.txt
7876e804913259c6687984aa19f222fba47976e081bf7b77c4d4886939445450  sha256_hashes_no_shortcuts_sorted.txt
```

## Commands

How files were generated.

```bash
# Download hashes
rclone hashsum sha256 workdrive:/ARCHIVES -q --drive-shared-with-me --drive-skip-shortcuts | tee sha256_hashes_no_shortcuts.txt
# Sort hashes by hash (base16)
sort < sha256_hashes_no_shortcuts.txt > sha256_hashes_no_shortcuts_sorted.txt
# Remove file paths so only hashes are left
cut -d ' ' -f 1 sha256_hashes_no_shortcuts_sorted.txt > sha256_hashes_no_shortcuts_sorted_public.txt
```

