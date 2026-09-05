# TacknWeld POS Updates

This public repository hosts only TacknWeld POS release installers and the small update manifest used by deployed applications. The Python source code and business data must not be uploaded here.

## Permanent manifest address

```text
https://raw.githubusercontent.com/deungriajimmy29/tacknweld-pos-updates/main/latest.json
```

## Publishing a new update

1. Build and test the new Windows Setup installer.
2. Give it a versioned name, for example `TacknWeldPOS-18.4.1-Setup.exe`.
3. In PowerShell, calculate its checksum:

   ```powershell
   Get-FileHash ".\TacknWeldPOS-18.4.1-Setup.exe" -Algorithm SHA256
   ```

4. Create a GitHub Release whose tag matches the version, for example `v18.4.1`.
5. Attach the Setup EXE to that Release.
6. Update `latest.json` with the exact version, asset URL, SHA-256, filename, byte size, date, and release notes.
7. Open the raw manifest URL and confirm it displays valid JSON before notifying deployed PCs.

## Safety rules

- Never publish a regular POS database, backup, password, Gmail App Password, Tailscale key, or PostgreSQL credential.
- Never place the Python source code in this public repository.
- Never reuse a version number for a different installer.
- Never publish a manifest until its SHA-256 exactly matches the uploaded installer.
- Keep `latest.json` on the `main` branch so its permanent address does not change.
