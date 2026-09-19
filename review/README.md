# Twenty Australian historical birds - local review pack

Prepared on 19 September 2026 against Fugleramme `11b54d2884a857702284d1e3fc2629b6c655bc79`. Nothing has been committed, pushed, sent or submitted.

Open `index.html` to review all twenty birds, three arrangements in paper and six-colour software output, and the unsent introduction/PR drafts. The payload is exactly twenty WebP files (2,294,926 bytes), twenty manifest entries and the necessary work attribution. Application code is unchanged. The original ten WebP files remain byte-for-byte identical to the earlier reviewed batch.

The magpie now uses a complete independent historical scan. The myna uses a historical plate with normal yellow facial skin. Per-bird source and regional-form qualifications remain explicit in `provenance.json`; the lorikeet preserves its original overlapping pair. All images use historical artist pixels, ordinary masking and proportional resizing, with paper backing prepared for the stock renderer. No generated bird imagery is included. The Tawny Frogmouth is cut closely around its original visible legs, toes and claws; the broad stump is removed without reconstructing hidden anatomy.

The proposed files are under `payload/` with their repository-relative paths. For a local checkout at the pinned revision:

```sh
git apply --check fugleramme-australian-historical-20.patch
git apply fugleramme-australian-historical-20.patch
```

The binary patch reproduces all 22 reviewed file hashes against clean baseline files. Rebase and repeat checks if upstream has moved; do not overwrite a newer complete manifest with this snapshot.

Validation: four current artwork tests, unchanged-file checks, patch round-trip and package integrity pass. [Prior complete-suite evidence](evidence/prior-twenty-tests.json) is preserved as historical; it was not rerun for this image-only correction. Physical panel and Linux runtime remain untested.

`CREDITS.md`, `provenance.json` and `evidence/source-rights/` retain artist credit and saved source terms. Evidence includes path-redacted logs. `CHECKSUMS.sha256` covers portable files. The wider 453-bird library and earlier 10-bird ZIP remain separate preserved snapshots; neither is silently replaced or certified by this preparation.
