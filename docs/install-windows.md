# Installing PageForge on Windows

Status: current for v0.13.0. These builds are **not code-signed yet** (a signing certificate has been
applied for). Windows will therefore show a warning the first time you run them; the steps below
explain it and how to check that the files are genuine.

Download from <https://github.com/sarayunova/PageForge-rs/releases/latest>:

| File | What it is |
|---|---|
| `pageforge-<version>-windows-x64.msi` | Installer (all users, needs administrator rights) |
| `pageforge-<version>-windows-x64-portable.zip` | No installer: unzip and run. Keeps settings beside the program |
| `SHA256SUMS.txt` | Checksums of the files above |

Windows 10 or 11, 64-bit. The command-line tool inside is still called `pdfcraft-cli.exe`.

## 1. Check the download (recommended)

In PowerShell, in the folder you downloaded to:

```powershell
Get-FileHash .\pageforge-<version>-windows-x64.msi -Algorithm SHA256
```

The hash must match the line for that file in `SHA256SUMS.txt`. If it does not, delete the file and
download it again.

## 2a. Install with the MSI

1. Double-click the `.msi`.
2. Windows SmartScreen may say **"Windows protected your PC"** because the file is unsigned. Choose
   **More info**, then **Run anyway**. (If you see a "User Account Control" question, answer Yes: the
   installer installs for all users.)
3. Follow the wizard. The optional choices are shortcuts and the right-click entries "Edit with
   PageForge" (PDF files) and "Create PDF with PageForge…" (images).
4. Start PageForge from the Start menu. PageForge appears under "Open with" for PDF files; to make it
   the default, use Settings ▸ Apps ▸ Default apps. The installer never changes your default itself.

To uninstall: Settings ▸ Apps ▸ Installed apps ▸ PageForge ▸ Uninstall. Your settings stay in
`%APPDATA%\PdfCraft` (the folder keeps its old name so existing settings carry over).

## 2b. Or use the portable zip

1. Right-click the zip ▸ **Extract All…** to a folder you own (for example `C:\Tools\PageForge`).
   Do not run `pageforge.exe` from inside the zip.
2. If SmartScreen warns, choose **More info** ▸ **Run anyway**. If the program will not start at all,
   right-click the zip before extracting ▸ **Properties** ▸ tick **Unblock** ▸ OK, then extract again.
3. Run `pageforge.exe`.

Because `portable.txt` sits beside the program, settings, logs and recovery files are kept in a
`PdfCraftData` folder next to it and nothing is written to `%APPDATA%`. Delete `portable.txt` to use
the normal per-user folders instead. To remove PageForge, delete the folder.

## Updates

Help ▸ Check for updates asks GitHub for the latest release when you choose it, and links to the
download page. It never installs anything by itself. Nothing else in the program contacts the internet.

## Problems

- Antivirus blocks or deletes the file: unsigned programs are sometimes flagged on first sight. Check
  the SHA-256 as in step 1, then restore it or add an exception for the install folder.
- Anything else: open an issue at <https://github.com/sarayunova/PageForge-rs/issues> and attach the
  log files from the `PdfCraft` folder under `%LOCALAPPDATA%` (or `%APPDATA%`), or from `PdfCraftData`
  for the portable zip.
