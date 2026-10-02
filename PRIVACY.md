# MicaPDF Privacy Policy

**Last updated:** 2 October 2026  
**Publisher:** TCDev  
**Product:** MicaPDF (Windows PDF viewer)  
**Contact:** [email@tcdev.xyz](mailto:email@tcdev.xyz) · [GitHub Issues](https://github.com/TCDev10/MicaPDF/issues)

This policy describes how MicaPDF handles document content, passwords, local data, and network activity. It is written for Windows Package Manager reviewers and for people who install the app.

## Summary

MicaPDF is designed to keep your documents on your device. It does **not** upload PDF contents to TCDev servers, does **not** require an account, and does **not** collect analytics or advertising telemetry.

## Document content

- PDF files you open remain under your control on disk (or wherever you stored them).
- MicaPDF reads documents locally to display pages, search text, outline structure, print, and export annotated copies when you choose those features.
- Document bytes are **not** sent to TCDev. The only optional network call is a GitHub release check described below; that request does not include your PDF content.

## PDF passwords

- If a PDF is password-protected, you may enter the password in the app so MicaPDF can open it.
- Passwords are used in memory to decrypt the file for viewing. They are **not** written to settings files, recent-file metadata, annotation sidecars, or remote services by MicaPDF.
- For some protected files, MicaPDF may create a temporary decrypted copy under `%LocalAppData%\MicaPDF\temp\` so the Windows PDF APIs can load it. That temp file is deleted when opening finishes or when the app cleans up; it is not uploaded.

## Data stored on your device

Unless you uninstall the app or delete the folders yourself, MicaPDF may keep the following under `%LocalAppData%\MicaPDF\`:

| Data | Location (typical) | Purpose | Retention |
| --- | --- | --- | --- |
| Recent files list | `recent.json` | Paths, last page, zoom, last opened time | Up to 6 entries; older entries drop off; you can remove items in the UI |
| Recent cover thumbnails | `covers\` | Small local PNG previews of recent files | Removed when the matching recent entry is removed |
| Annotation sidecars | `annotations\` | Ink and text annotations keyed to a document path and size | Kept until you clear annotations for that file or delete the sidecar; not sent to TCDev |
| App settings | local settings / exportable JSON | Theme, language, zoom limits, and similar preferences | Until you change, reset, or uninstall |
| Diagnostic logs | `logs\` (`mica-*.log`) | Local troubleshooting (info/warn/error); may include file names and error text | Rotating; at most 3 log files retained |
| Temporary decrypted PDFs | `temp\` | Short-lived open of password-protected documents | Deleted after use when possible |

Uninstalling MicaPDF removes the program files. LocalAppData folders above may remain until you delete them manually.

## Export, print, and annotations you choose to save

- **Export / print:** When you export an annotated PDF or print, content leaves the app through the file or printer you select. That is under your control.
- **Annotation sidecars:** Annotations are stored locally as described above. They are separate from the original PDF unless you export an annotated document.

## Network activity (update check)

- MicaPDF can check GitHub for a newer release by requesting `https://api.github.com/repos/<owner>/<repo>/releases/latest` for the configured repository.
- That request uses a generic `MicaPDF` user agent. It does **not** send PDF contents, passwords, recent-file lists, annotations, settings, or logs.
- No other TCDev telemetry, crash-reporting, or advertising endpoints are used by the app as shipped for this policy.

## What we do not collect

- No user accounts or sign-in with TCDev
- No analytics SDKs or advertising identifiers
- No remote storage of your documents or annotations on TCDev infrastructure

## Children

MicaPDF is a general-purpose desktop utility. It is not directed at children and does not knowingly collect personal information from children.

## Changes

We may update this policy when product behavior changes. The “Last updated” date at the top will change when we do. Continued use after an update means you accept the revised policy for that version.

## Contact

Questions about this policy: [email@tcdev.xyz](mailto:email@tcdev.xyz) or open an issue at [TCDev10/MicaPDF](https://github.com/TCDev10/MicaPDF/issues).
