# ModForge Verify CLI (v0.1.0)

A deterministic static analysis tool designed to validate BepInEx mod packages against defined community structure standards.

* **Offline-First:** Operates entirely offline; makes no network calls by default.
* **Static Analysis:** Checks archive structure and metadata without executing code.

## How to Use

### 1. Scan a Single File
Drag and drop a mod `.zip` file directly onto `ModForgeVerify.exe`.

### 2. Batch Scan
Drag and drop a folder containing multiple `.zip` files onto the executable.

### 3. Output
* A **Discord-ready summary** is automatically copied to your clipboard (ready to paste).
* A detailed `report.html` is generated in the same directory.

## Configuration (`profile.json`)
The scanning rules are defined in `profile.json`.
* **allowed_guids**: Add trusted mod GUIDs here to whitelist them (optional).
* **blocked_guids**: Add known bad GUIDs here to automatically flag them as RED.
* **risk_signals**: Configure detection levels for code analysis (PInvoke, Unsafe).

> **Note on Profiles:** This release ships with a minimal "blank slate" profile by design. The engine performs deterministic structural and risk analysis out of the box (e.g., P/Invoke, unsafe code), while community-specific allow/deny rules (GUIDs, dependencies) are intentionally left to be defined by each community's own standards.

## Disclaimers

* **Static Analysis Only:** This tool checks file structure and manifest data. It does **not** execute mod code and cannot verify runtime behavior.
* **No Security Guarantees:** A passing scan does **not** guarantee the mod is safe, free of malware, or free of bugs. Always download mods from trusted sources.
* **As-Is:** This software is provided "as is", without warranty of any kind.
