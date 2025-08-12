# RECOVERY.md — Recovery & Long-term Safety (Personal Vault)

**Do not store your passphrase in this repo.** Print this file and store offline.

## Immediate steps (do now)
1. Pick a strong master passphrase (length ≥ 16, use a passphrase of random words or a high-entropy password manager-generated secret). Write it down and store it in a safe place.
2. Create **three** encrypted backups of your vault (use the Export button):
   - Local encrypted file on your computer (in an encrypted disk or container).
   - Push the exported `.json` to a **private** GitHub repository (ciphertexts only). Enable 2FA.
   - Copy the exported `.json` onto an encrypted USB drive and store in a fire-safe or deposit box.
3. Verify each backup using the `Verify Backups` button (unlock with passphrase and run verify).

## Emergency recovery
- If you lose access to all devices but have an encrypted export + passphrase, you can restore by:
  1. Clone the repo containing `personal-vault-index.html` and `libsodium-wrappers.min.js` to a machine.
  2. Open `personal-vault-index.html` in a modern browser.
  3. Use the Import button to import your exported manifest `.json` (ciphertext only).
  4. Enter your passphrase and unlock — you can then download decrypted files.

## Long-term best practices (10+ years)
- Store at least one export on physical media (USB) and replace that media every 3–5 years.
- Re-encrypt (migrate) vault every ~5 years with stronger KDF params (invoke `vault.migrateToNewParams(ops, mem)` in the browser console while unlocked).
- Keep a copy of `libsodium-wrappers.min.js` alongside the HTML; do not rely on remote CDNs.
- Maintain `BUILD.md` in the repo with pinned versions and exact build commands so the site can be rebuilt in the future.

## Notes
- If you forget your passphrase and have no escrowed key, your data is unrecoverable by design (this is intentional — it's zero-knowledge client-side encryption).
- If you want a recovery escrow, consider encrypting a copy of the vault with a second passphrase held by a trusted person (store that copy offline).
