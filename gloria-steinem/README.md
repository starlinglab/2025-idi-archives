# Gloria Steinem archive

In November 2025, Starling Lab took a SHA-256 fingerprint of every file in the Gloria Steinem archive held on Google Drive, before anything was selected for publication. This folder holds that list and the proofs that it existed by 25 November 2025.

The list has **35,586 entries** and **34,542 distinct hashes**. The difference is files that appear in more than one folder. It contains hashes only: no filenames, folder names or other text.

## What this proves / what it doesn't

A file whose SHA-256 hash appears in `sha256_hashes_no_shortcuts_full_sorted_public.txt` has these exact bytes, and they existed by 25 November 2025 and have not changed since.

That the list is the Steinem archive rests on Starling Lab's word, through the signatures below. The list does not say who made a file, when it was captured, or who holds the rights. Those claims, where published, are made by the foundation and recorded by Starling, and are labelled as such.

Note: a file that is **not** in the list has not been shown to be fake – its provenance is simply less certain.

## Files

| File | Published | Content |
|---|---|---|
| `sha256_hashes_no_shortcuts_full_sorted_public.txt` | yes | 35,586 hashes, sorted, one per line |
| `sha256_hashes_no_shortcuts_full_sorted_public.txt.ots` | yes | OpenTimestamps proof for the list above |
| `sha256_hashes_no_shortcuts_sorted_public.txt.ots` | yes | Proof for the first, shorter list (in git history only, commit `70bb36b`) |
| `sha256_hashes_no_shortcuts_full_sorted.txt` | no | Same hashes with file paths. Its own hash is recorded below. |

### Root hashes

SHA-256 of each list file, recorded in the signed commit `da7c71b`.

```
459a41c3a17c48ff3772d1555582be1b83b34711d22024e9dd49722fb93435df  md5_hashes_no_shortcuts.txt
81ebb55ea1491b60ab7dee64f7f1fed13232507e843b2b452716f002512a53f8  missing-hashes.txt
dd3bdc8ef6a8a2d72d75fcafc998a12e2c7615be70500c7aa3edd8ee3de3916e  remaining-hashes.txt
b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca  sha256_hashes_no_shortcuts_full_sorted_public.txt
54700e4354442f77b3d76a528eebc6ece6d8e18900a568644db0919172850daa  sha256_hashes_no_shortcuts_full_sorted.txt
495d4025e251b609e96eaf63cad4ad218c32affe8dd19346d4a7ddcdfb4579c3  sha256_hashes_no_shortcuts_sorted_public.txt
7876e804913259c6687984aa19f222fba47976e081bf7b77c4d4886939445450  sha256_hashes_no_shortcuts_sorted.txt
```

The path list is not published because the filenames carry personal names and internal notes. Its hash above commits to its content as of November 2025. Auditors can check it on request.

## Timestamps

The commits that added the hash lists are PGP-signed with an [OpenTimestamps](https://opentimestamps.org/) proof embedded in the signature (made with `ots-git-gpg-wrapper`). The `.ots` files next to this README are those proofs extracted per file and upgraded to their Bitcoin attestations, so they verify without the calendar servers.

| Proof | File | Commit | Earliest Bitcoin block |
|---|---|---|---|
| `sha256_hashes_no_shortcuts_full_sorted_public.txt.ots` | current list | `da7c71b` | 925133 (2025-11-25 15:13 UTC) |
| `sha256_hashes_no_shortcuts_sorted_public.txt.ots` | first list, only in git history | `70bb36b` | 925054 (2025-11-24 22:35 UTC) |

The current proof also carries later attestations at blocks 925138, 925150 and 925237 from other calendar servers. Any one of them is enough.

## Who witnessed the list

**November 2025.** The commits `70bb36b` and `da7c71b` were signed by the key below, held by the Starling Lab engineer who ran the hashing.

```
E8B29C18EC22EEB84CE1548D7DE9FA10A6B58CA5
```

**From October 2026.** The list hash `b724d1…`, its Bitcoin block and its `.ots` proof are recorded in Starling Lab's [Authenticated Attributes](https://starlinglab.org/prototypes/authenticated-attributes/) database, which signs and timestamps every entry with the key below.

```
481c9ffcc9ed289391d61358eb5edf5098eabc25a6f1957fd6b3fe01cf56607e
```

## How to verify

1. **Check the list.** Download `sha256_hashes_no_shortcuts_full_sorted_public.txt` and confirm its hash.
   ```bash
   sha256sum sha256_hashes_no_shortcuts_full_sorted_public.txt
   # b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca
   ```
2. **Check the timestamp.** With the [OpenTimestamps client](https://github.com/opentimestamps/opentimestamps-client) and access to a Bitcoin node:
   ```bash
   ots verify sha256_hashes_no_shortcuts_full_sorted_public.txt.ots
   ```
   Without a node, `ots info` shows the Bitcoin block heights the proof commits to, and any block explorer shows their dates. The branch ending in block 925133 goes through transaction [`cb8c7c24…73c22f`](https://mempool.space/tx/cb8c7c2477d081d25c93fb46ea41384932c22cbb667e68d64a7885935473c22f), whose `OP_RETURN` output is `c99cabad348e5487176348ee37dad991fa9d1291a7ea85f1f2e88bbe0b317477`, the Merkle root the proof derives from the list hash.
3. **Check a file.** Hash the file you have and look it up in the list.
   ```bash
   sha256sum "Gloria Steinem by Katie Lyman.jpg"
   grep -c bb5afa9d533a3c6b03e299f2e3eef9e5781c7fcd4587d23c66ec4d222dfab947 sha256_hashes_no_shortcuts_full_sorted_public.txt
   # 1
   ```
4. **Check the commit signature.** `git log --show-signature da7c71b` shows the PGP signature and the embedded timestamp.
5. **Check the Cardano registrations.** Each transaction below carries, under metadata label 674, a JSON record with the file's SHA-256 and the attributes listed. Explorers show it under the transaction's metadata tab. It can also be read without an account:
   ```bash
   curl -s -X POST https://api.koios.rest/api/v1/tx_metadata -H "content-type: application/json" \
     -d '{"_tx_hashes":["6c75d77f8a9f8561c10b9c7cb4589f1ce75b4a34ee0593c41f6b8f3178452ab5"]}'
   ```
   The record is split into 64-character strings; join them to get the JSON.

## Published items

| Item | SHA-256 | Cardano mainnet registration (27 Oct 2026) |
|---|---|---|
| This hash list | `b724d181bebd0c83a91fb7e11cb6fb831f7d4f5ebfda9c5b930a9476729106ca` | [`a331be12…c50f72`](https://cardanoscan.io/transaction/a331be1223f534b4d7e27ee1063f5e8008909ebf7a99bef715f1c4abb8c50f72?tab=metadata), block 14122765. Carries the Bitcoin block, transaction and `OP_RETURN` above, the signed commit and key, and the entry counts. |
| Portrait of Gloria Steinem by Katie Lyman, June 2021 (according to the foundation) | `bb5afa9d533a3c6b03e299f2e3eef9e5781c7fcd4587d23c66ec4d222dfab947` | [`6c75d77f…452ab5`](https://cardanoscan.io/transaction/6c75d77f8a9f8561c10b9c7cb4589f1ce75b4a34ee0593c41f6b8f3178452ab5?tab=metadata), block 14122770. Carries the credit, the rights, and a pointer to this list's hash, CID and Bitcoin proof. |

The photograph is line 26,053 of the list. The published file is byte-for-byte the file in the archive. Its credit and date are as given by the foundation, recorded by Starling in Authenticated Attributes under the CID `bafkreif3ll5j2uz2hrvqhyuz6lr656pfpaoh7tkfq7jdyzxmjurc36vzi4`. The list is recorded under `bafkreifxetiydpv5bsb2sh5x4eoln64dd56u6xv73kofxeyksr3hfeigzi`.

The `rights` field in the photograph's on-chain record holds a placeholder written before the foundation's licence wording was received. On-chain records cannot be edited. The foundation's wording is recorded in Authenticated Attributes, which is append-only, so the correction and its date are visible there.

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
