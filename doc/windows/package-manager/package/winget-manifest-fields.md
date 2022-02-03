---
title: Manifest Data Fields
description: A list of all the available fields within the manifest structure
ms.date: 02/02/2022
ms.localizationpriority: low
---

# Creating a Manifest

If you want to submit a software package to the [Windows Package Manager Community Repository](repository.md), you will need to [create a package manifest](manifest.md). Each YAML file within the manifest has different metadata fields that can be added to the manifest. It is best to fill out as much metadata as possible, even if the Windows Package Manager client (winget.exe) does not fully support it yet.

## Manifest Fields

### [Singleton Manifest](#tab/singleton/)
```YAML
PackageIdentifier: The unique identifier of the package
PackageVersion: The version of the package
PackageLocale: The BCP 47 localization code this metadata is written in (e.g. en-US)
Publisher: The publisher name
PublisherUrl: The publisher home page
PublisherSupportUrl: The publisher support page
PrivacyUrl: The page containing the privacy policy for the package or publisher
Author: The author of the package
PackageName: The name of the package
PackageUrl: The package home page
License: What terms the package is licensed under
LicenseUrl: The page containing the license for the package
Copyright: The package copyright
CopyrightUrl: The page containing the copyright for the package
ShortDescription: A short, meaningful description of what the package is used for or does
Description: The full description of the package
Moniker: A term that the package may be commonly referred to by. (e.g The moniker for Visual Studio Code is `vscode`)
Tags:
  - A list of tags
Agreements:
  - AgreementLabel: The label of the Agreement. i.e. EULA, AgeRating, etc.
    Agreement: |
      The agreement text content
    AgreementUrl: The page containing the agreement
ReleaseNotes: |
  The full set of release notes for the specified package version
ReleaseNotesUrl: The page containing the release notes for the specified package version
Channel: The distribution channel
Installers:
  - InstallerLocale: The BCP 47 localization code the installer runs in by default
  Platform: The operating system types supported by the installer
  MinimumOSVersion: The minimum version of the operating system this package requires
  Architecture: The installer target architecture
  InstallerType: The type of package the installer is delivered as
  Scope: Whether the package is installed at the machine level or user level
  InstallerUrl: The direct URL to download the installer
  InstallerSha256: The SHA256 hash of the installer file
  SignatureSha256: The SHA256 hash of the signature file inside of an appx or msix package
  InstallModes:
    - What modes the installer can run in. Values must match those defined in the manifest schema
  InstallerSwitches:
    Silent: The value passed to the installer when the user chooses a silent or quiet install
    SilentWithProgress: The value passed to the installer when the user chooses a non-interactive install
    Interactive: The value passed to the installer when the user chooses an interactive install
    InstallLocation: The value passed to the installer for setting a custom install location. The <INSTALLPATH> token can be used to represent the path the user provides
    Log: The value passed to the installer for setting a custom log location. The <LOGPATH> token can be used to represent the path the user provides
    Upgrade: The value passed to the installer when the user is performing an upgrade instead of a new install
    Custom: The values which will be passed to the installer along with all other installer switches
  InstallerSuccessCodes:
    - A list of additional non-zero installer success exit codes
  ExpectedReturnCodes:
    - InstallerReturnCode: Installer return code for an error
      ReturnResponse: Common error text the return code represents. Value must match one defined in the manifest schema
  UpgradeBehavior: Whether to install the package directly, or uninstall the previous version before installing the new version
  Commands:
    - A list of commands the package provides handlers for
  Protocols:
    - A list of protocols the package provides handlers for
  FileExtensions:
    - A list of file extensions the package provides handlers for
  Dependencies:
    WindowsFeatures:
      - A list of Windows Feature dependencies
    WindowsLibraries:
      - A list of Windows Library dependencies
    PackageDependencies:
      - PackageIdentifier: The package identifier of the dependency package
        MinimumVersion: The minimum version of the dependency
    ExternalDependencies:
      - A list of dependencies for packages outside of the Windows Package Manager
  PackageFamilyName: 
  ProductCode: The product code of the package being installed
  Capabilities:
    - A list of appx or msix installer capabilities
  RestrictedCapabilities:
    - A list of appx or msix installer restricted capabilities
  Markets:
    AllowedMarkets:
      - A list of target markets the package can be shown in
    ExcludedMarkets:
      - A list of target markets the package cannot be shown in
  InstallerAbortsTerminal: Indicates whether or not the installer will abort the terminal
  ReleaseDate: The date the specified package version was released
  InstallLocationRequired: Whether or not the user must provide an install location
  RequireExplicitUpgrade: Indicates whether the installer should be pinned by default from upgrade
  UnsupportedOSArchitectures:
    - A list of architectures the installer does not support
  AppsAndFeaturesEntries:
    - DisplayName: The DisplayName registry value for the package
      Publisher: The Publisher registry value for the package
      DisplayVersion: The DisplayVersion registry value for the package
      ProductCode: The product code for the package
      UpgradeCode: The upgrade code for the package
      InstallerType: The installer type for the package, which may differ from the installer type of the installer
  ElevationRequirement: The elevation requirement of the installer. Value must match one defined in the manifest schema
ManifestType: The manifest type, in this case, 'version'
ManifestVersion: The schema version to reference for manifest validation
```

### [Installer Manifest](#tab/installer/)

### [Default Locale Manifest](#tab/defaultLocale/)

### [Additional Locale Manifest](#tab/locale/)

### [Version Manifest](#tab/version/)
```YAML
PackageIdentifier: The unique identifier of the package
PackageVersion: The version of the package
DefaultLocale: The BCP 47 localization code for the default metadata (e.g. en-US)
ManifestType: The manifest type, in this case, 'version'
ManifestVersion: The schema version to reference for manifest validation
```