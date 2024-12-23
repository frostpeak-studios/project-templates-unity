# Project Templates for Unity

This repo contains our project templates for Unity. We use these templates to create new projects for our plugins.

## Installation

### Creating Template Package

1. Copy the contents of the template you want to use into a local folder named `package`
2. Use 7z or another archiving tool to create a `.tgz` archive of the `package` folder (zip format works fine,
   but the extension still must be `.tgz`).
3. Name the archive `com.unity.template.frostpeak-studios-1.[template-year].[template-version].tgz`
    - `com.unity.template.frostpeak-studios-1.2022.2.tgz`
    - `com.unity.template.frostpeak-studios-1.2021.2.tgz`

### Editor Path Installation

The simplest method is to install the template into the specific editor version's install path.

1. Move the archive to the `C:\Program Files\Unity\Hub\Editor\[version]\Editor\Data\Resources\PackageManager\ProjectTemplates` folder.
2. Restart Unity Hub

### Hub Path Installation

Alternatively, you can install the template into the Unity Hub's template folder and use it across various editor
versions.

1. Move the archive to `C:\Users\[username]\AppData\Roaming\UnityHub\Templates`
2. Modify the `manifest.json` file in that directory, adding the template to the desired version(s) under dependencies:
   - `"com.unity.template.frostpeak-studios": "1.2022.2"`
   - `"com.unity.template.frostpeak-studios": "1.2021.2"`
3. Restart Unity Hub

## Template Contents/Changes

The templates contain some basic project setup and configuration that we use in all of our projects. This includes:

- Project folder structure
- Project settings (IL2CPP, etc.)
- Scene template
- Scene hierarchy example with Febucci's custom hierarchy package included and configured
- Default packages we want to use:
    - Addressables
    - Code coverage
    - Input System
    - Localization
    - Memory Profiler (2022+)
    - Newtonsoft JSON.NET
    - Profile Analyzer
    - TextMeshPro (essentials installed)
    - URP
- Removes default packages we don't want:
    - Timeline
    - Version Control
    - Visual Scripting
- Upgrades all packages to latest compatible versions

## Compatibility

Unless stated otherwise, the templates are designed to work with the LTS version of the year, such as 2021.3, 2022.3,
etc. Compatibility with alpha, beta, or tech stream versions is not guaranteed.
