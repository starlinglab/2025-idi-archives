# Gloria Steinem archive

All available SHA-256 hashes from GDrive were collected into `sha256_hashes_no_shortcuts_full_sorted_public.txt`.

Total files: 35,586

## Root hashes

These are the SHA-256 hashes of all the hashes, representing the whole archive at once.

```
459a41c3a17c48ff3772d1555582be1b83b34711d22024e9dd49722fb93435df  md5_hashes_no_shortcuts.txt
81ebb55ea1491b60ab7dee64f7f1fed13232507e843b2b452716f002512a53f8  missing-hashes.txt
dd3bdc8ef6a8a2d72d75fcafc998a12e2c7615be70500c7aa3edd8ee3de3916e  remaining-hashes.txt
b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca  sha256_hashes_no_shortcuts_full_sorted_public.txt
54700e4354442f77b3d76a528eebc6ece6d8e18900a568644db0919172850daa  sha256_hashes_no_shortcuts_full_sorted.txt
495d4025e251b609e96eaf63cad4ad218c32affe8dd19346d4a7ddcdfb4579c3  sha256_hashes_no_shortcuts_sorted_public.txt
7876e804913259c6687984aa19f222fba47976e081bf7b77c4d4886939445450  sha256_hashes_no_shortcuts_sorted.txt
```

## Commands

How files were generated.

```bash
# Download hashes
rclone hashsum sha256 workdrive:/ARCHIVES -q --drive-shared-with-me --drive-skip-shortcuts | tee sha256_hashes_no_shortcuts.txt
# Get files without SHA-256 from GDrive
# https://github.com/rclone/rclone/issues/8996
grep '^   ' sha256_hashes_no_shortcuts.txt | cut -b67- > missing-hashes.txt
# Download missing hashes
rclone hashsum sha256 --files-from missing-hashes.txt --download drive:/ARCHIVES --drive-shared-with-me --drive-skip-shortcuts -q | tee remaining-hashes.txt
# Combine files
grep -v '^   ' sha256_hashes_no_shortcuts.txt | cat - remaining-hashes.txt > sha256_hashes_no_shortcuts_full.txt
# Sort hashes by hash (base16)
sort < sha256_hashes_no_shortcuts_full.txt > sha256_hashes_no_shortcuts_full_sorted.txt
# Remove file paths so only hashes are left
cut -d ' ' -f 1 sha256_hashes_no_shortcuts_full_sorted.txt > sha256_hashes_no_shortcuts_full_sorted_public.txt
```

