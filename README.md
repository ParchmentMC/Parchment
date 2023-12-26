Parchment Mappings
==================
[![Discord server badge](https://img.shields.io/discord/851855518398152725?color=5865F2&label=discord&logo=discord&logoColor=white)](https://discord.parchmentmc.org/)
[![Minecraft version badge](https://img.shields.io/badge/mc%20version-1.20.3-3b8526)](#)
&nbsp;
[![Latest release version badge](https://img.shields.io/maven-metadata/v?color=forestgreen&label=release&metadataUrl=https%3A%2F%2Fldtteam.jfrog.io%2Fartifactory%2Fparchmentmc-internal%2Forg%2Fparchmentmc%2Fdata%2Fparchment-1.20.3%2Fmaven-metadata.xml)](#)
[![CI release build status](https://buildsystem.ldtteam.com/app/rest/builds/buildType:(id:ParchmentMC_Mappings_Release),branch:1.20.x/statusIcon)](#)

[![Latest nightly version badge](https://img.shields.io/maven-metadata/v?color=orange&label=nightly&metadataUrl=https%3A%2F%2Fldtteam.jfrog.io%2Fartifactory%2Fparchmentmc-snapshots%2Forg%2Fparchmentmc%2Fdata%2Fparchment-1.20.3%2Fmaven-metadata.xml)](#)
[![CI nightly build status](https://buildsystem.ldtteam.com/app/rest/builds/buildType:(id:ParchmentMC_Mappings_Nightly),branch:1.20.x/statusIcon)](#)
&nbsp;
[![Latest bleeding version badge](https://img.shields.io/maven-metadata/v?color=red&label=bleeding&metadataUrl=https%3A%2F%2Fldtteam.jfrog.io%2Fartifactory%2Fparchmentmc-bleeding%2Forg%2Fparchmentmc%2Fdata%2Fparchment-1.20.3%2Fmaven-metadata.xml)](#)
[![CI bleeding build status](https://buildsystem.ldtteam.com/app/rest/builds/buildType:(id:ParchmentMC_Mappings_Bleeding),branch:1.20.x/statusIcon)](#)

Welcome to the Parchment mappings repository!

Parchment is an open community-sourced modloader-neutral set of mappings of parameter names and javadocs, to augment
the official names released by Mojang. This repository contains the files which make up the Parchment mapping set, with
the build tool to manage the mappings and generate exports for publishing.

### Want to use Parchment in your workspace? See the [Getting Started](https://parchmentmc.org/docs/getting-started) page at the website.

## Contributing
See the [`docs/CONTRIBUTING.md` file](docs/CONTRIBUTING.md) for information on contributing. Also look at the 
[repository wiki](https://github.com/ParchmentMC/Parchment/wiki) for more information, such as links to the mapping 
standards and PR review process documents.

## Tools and Libraries
Our mappings system makes use of the following open-source tools and libraries:
- [Compass](https://github.com/ParchmentMC/Compass), the Gradle plugin powering the validation and input systems.
- [Feather](https://github.com/ParchmentMC/Feather), a data object and parsing library used by ParchmentMC projects.
- [Enigma](https://github.com/FabricMC/enigma), a tool for deobfuscation and mapping of Java bytecode.
- [Moshi](https://github.com/square/moshi), a modern JSON parsing library.

## Support
Want to ask a question? Get help on how to use these mappings? Or tips on contributing to the mappings? Head over to
our [public Discord server](https://discord.parchmentmc.org/)!

## Licensing
Parchment mappings are released under the terms of the CC0 1.0 Universal (CC0 1.0), see the [`LICENSE.txt`](LICENSE.txt) 
for the full legal text.
