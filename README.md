# ModClear (Diagnostic Tool)

![ModClear Badge](./docs/badge.png)

ModClear is an offline diagnostic tool for modded games.
Drag in a mod ZIP or r2modman profile export (.r2z) and get an instant, pasteable diagnosis of the file-level mod state — including loader status, installed mods, duplicates, missing dependencies, known conflicts, junk files, and dangerous configs.

ModClear doesn’t fix mods or run the game. It replaces guessing with clarity.

![Explainer Sketch](./docs/explainer.png)

## How ModClear Fits with BepInEx

BepInEx and ModClear serve different roles.

**BepInEx** is the loader. Its job is to load mods at runtime and report errors when something fails.

**ModClear** is the diagnostic engine. It statically scans a mod package (or profile export) before runtime to check:
- plugin identity (GUID + version)
- declared vs actual dependencies
- known risk signals (e.g. unreadable or obfuscated assemblies)
- duplicate mods or version conflicts
- junk files and dangerous configurations

ModClear does not run mods, sandbox code, or guarantee stability.

Think of it this way:
- **BepInEx** assumes mods are correct and tries to run them.
- **ModClear** checks whether mods are structured correctly before they are run.

This helps support helpers filter obvious structural problems early, before logs and crashes enter the loop.

## Quickstart (Support Flow)

1. **Drag & Drop** the mod ZIP, folder, or **r2modman export (.r2z)** onto `ModClear.exe`.
2. **Tool runs headlessly**: The scan completes and the summary is automatically copied to your clipboard.
3. **Paste into Discord**: Share the summary with helpers immediately to get structured support.

**Windows SmartScreen Notice:** Windows may show an "Unknown Publisher" warning because this tool is not digitally signed (which costs money). Click "More Info" -> "Run Anyway".

## Mental Model (The "Why")

- **Tool** = Mechanic (stable, deterministic)
- **Profiles** = Reference Manual (versioned, community-defined)
- **Report** = Diagnostic Chart (used in support workflows)

## "Blank Slate" profile.json (important)
This is an Example Profile (optional). Normal users do not need to download or edit this file for standard use.

The provided `profile.json` is intentionally a Blank Slate example:
- It demonstrates the format and lets communities define their own allow/block lists and severities.
- It is not claiming to be "the official rules" for any specific game/community.
- Users can populate allowlists/blocklists to match their local rules.

## Verdict semantics

We use simplified status semantics for scale:

- **CRITICAL** — Must be fixed. Deterministic errors preventing proper function.
- **WARNING** — Worth checking. Potential risks or configuration issues.
- **CLEAR** — Nothing obvious at file level. No static issues found.

(The report stays neutral and factual — no false authority.)