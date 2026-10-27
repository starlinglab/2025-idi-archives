# Gloria Steinem Archive

In November 2025, Starling Lab fingerprinted every file in the Gloria Steinem archive (hosted on Google Drive) using SHA-256 before publication. This folder contains the hash list and proofs of its existence by 25 November 2025.

The list has **35,586 entries** and **34,542 distinct hashes** (duplicates reflect files appearing in multiple folders). It contains *only* hashes—no filenames, folder names, or metadata.

## Proofs and Limits
A file whose SHA-256 hash appears in `sha256_hashes_no_shortcuts_full_sorted_public.txt` is proven to:
- Have these exact bytes;
- Have existed by **25 November 2025**;
- Be unchanged since then.

**Limitations:**
- The list’s authenticity rests on Starling Lab’s attestation (via signatures below).
- It does *not* confirm authorship, capture dates, or rights holders. Such claims (where published) are made by the foundation and recorded separately by Starling.
- **Absence from the list does not equate forgery.** Unlisted files may still be authentic; their provenance is simply unverified here.

## Files

| File | Published? | Content |
|------|------------|---------|
| `sha256_hashes_no_shortcuts_full_sorted_public.txt` | ✅ | 35,586 hashes (sorted, one per line). |
| `sha256_hashes_no_shortcuts_full_sorted_public.txt.ots` | ✅ | OpenTimestamps proof for the above. |
| `sha256_hashes_no_shortcuts_sorted_public.txt.ots` | ✅ | Proof for the shorter initial list (git history only; commit `70bb36b`). |
| `sha256_hashes_no_shortcuts_full_sorted.txt` | ❌ | **Same hashes + file paths (unpublished due to sensitive metadata).** Its hash is recorded below. |

### Root Hashes
SHA-256 of each list file (recorded in signed commit `da7c71b`):
```
459a41c3a17c48ff3772d1555582be1b83b34711d22024e9dd49722fb93435df  md5_hashes_no_shortcuts.txt
81ebb55ea1491b60ab7dee64f7f1fed13232507e843b2b452716f002512a53f8  missing-hashes.txt
dd3bdc8ef6a8a2d72d75fcafc998a12e2c7615be70500c7aa3edd8ee3de3916e  remaining-hashes.txt
b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca  sha256_hashes_no_shortcuts_full_sorted_public.txt
54700e4354442f77b3d76a528eebc6ece6d8e18900a568644db0919172850daa  sha256_hashes_no_shortcuts_full_sorted.txt
495d4025e251b609e96eaf63cad4ad218c32affe8dd19346d4a7ddcdfb4579c3  sha256_hashes_no_shortcuts_sorted_public.txt
7876e804913259c6687984aa19f222fba47976e081bf7b77c4d4886939445450  sha256_hashes_no_shortcuts_sorted.txt
```

**Auditors:** Request access to the path list (`sha256_hashes_no_shortcuts_full_sorted.txt`) for verification.

## Timestamps
Commits adding hash lists are PGP-signed with embedded [OpenTimestamps](https://opentimestamps.org/) proofs. The `.ots` files here are extracted and upgraded to Bitcoin attestations (no calendar servers required).

| Proof File | Target File | Commit | Earliest Bitcoin Block |
|------------|-------------|--------|------------------------|
| `sha256_hashes_no_shortcuts_full_sorted_public.txt.ots` | Current list | `da7c71b` | **925133** (25 Nov 2025, 15:13 UTC) |
| `sha256_hashes_no_shortcuts_sorted_public.txt.ots` | Initial list (git history) | `70bb36b` | **925054** (24 Nov 2025, 22:35 UTC) |

**Note:** The current proof also includes later attestations (blocks 925138, 925150, 925237). Any single attestation suffices.

## Attestations

### November 2025
Commits `70bb36b` and `da7c71b` were signed by Starling Lab’s engineer Cole Capilongo using this key:
```
E8B29C18EC22EEB84CE1548D7DE9FA10A6B58CA5
```

### October 2026
The list hash (`b724d1…`), its Bitcoin block, and `.ots` proof were recorded in Starling Lab’s [Authenticated Attributes](https://starlinglab.org/prototypes/authenticated-attributes/) database, signed with:
```
481c9ffcc9ed289391d61358eb5edf5098eabc25a6f1957fd6b3fe01cf56607e
```

## Verification Steps

1. **Verify the list:**
   ```bash
   sha256sum sha256_hashes_no_shortcuts_full_sorted_public.txt
   # Expected: b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca
   ```

2. **Verify the timestamp:**
   - With a Bitcoin node:
     ```bash
     ots verify sha256_hashes_no_shortcuts_full_sorted_public.txt.ots
     ```
   - Without a node: Use `ots info` to check block heights. The proof’s Merkle root (`c99cabad348e5487176348ee37dad991fa9d1291a7ea85f1f2e88bbe0b317477`) is in transaction [`cb8c7c24…73c22f`](https://mempool.space/tx/cb8c7c2477d081d25c93fb46ea41384932c22cbb667e68d64a7885935473c22f).

3. **Verify a file:**
   ```bash
   sha256sum "Gloria Steinem by Katie Lyman.jpg"
   grep -c bb5afa9d533a3c6b03e299f2e3eef9e5781c7fcd4587d23c66ec4d222dfab947 sha256_hashes_no_shortcuts_full_sorted_public.txt
   # Output: 1 (match found)
   ```

4. **Verify the commit signature:**
   ```bash
   git log --show-signature da7c71b
   ```

5. **Check Cardano registrations:**
   - Metadata for each transaction is under label `674`. Example:
     ```bash
     curl -s -X POST https://api.koios.rest/api/v1/tx_metadata \
       -H "content-type: application/json" \
       -d '{"_tx_hashes":["6c75d77f8a9f8561c10b9c7cb4589f1ce75b4a34ee0593c41f6b8f3178452ab5"]}'
     ```
   - **Note:** Metadata is split into 64-character strings; concatenate to reconstruct JSON.

## Published Items

| Item | SHA-256 | Cardano Registration (27 Oct 2026) |
|------|---------|------------------------------------|
| **Hash list** | `b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca` | [`a331be12…c50f72`](https://cardanoscan.io/transaction/a331be1223f534b4d7e27ee1063f5e8008909ebf7a99bef715f1c4abb8c50f72?tab=metadata) (Block 14122765). Includes Bitcoin block/transaction, signed commit, key, and entry counts. |
| **Portrait of Gloria Steinem** (Katie Lyman, June 2021) | `bb5afa9d533a3c6b03e299f2e3eef9e5781c7fcd4587d23c66ec4d222dfab947` | [`6c75d77f…452ab5`](https://cardanoscan.io/transaction/6c75d77f8a9f8561c10b9c7cb4589f1ce75b4a34ee0593c41f6b8f3178452ab5?tab=metadata) (Block 14122770). Includes credit, rights, and pointers to the list’s hash/CID/Bitcoin proof. |

**Details:**
- The photograph is **line 26,053** in the list. The published file matches the archive’s bytes exactly.
- **Credits/dates** are as provided by the foundation and recorded by Starling under CID `bafkreif3ll5j2uz2hrvqhyuz6lr656pfpaoh7tkfq7jdyzxmjurc36vzi4`.
- The list is recorded under CID `bafkreifxetiydpv5bsb2sh5x4eoln64dd56u6xv73kofxeyksr3hfeigzi`.
- **Rights note:** The on-chain record uses a placeholder (pre-licence wording). The foundation’s final wording is recorded in Authenticated Attributes (append-only; corrections are timestamped).

## Commands

How the lists were generated in November 2025.

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
