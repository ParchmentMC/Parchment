# Data Migration

The _data migration system_ allows for migrating Parchment mapping data between Minecraft versions that's easy to use,
easy to automate, and retains more data through the use of technology which matches changed methods between versions.

Data migration is done using the [JAMMER/JarAwareMapping tool][jammer], through the Parchment-specific
[ParchmentJAM][parchmentjam] integration application. See the README for ParchmentJAM for more details on its operation.

## Usage

The data migration system's key task is the `migrateData` task under the `parchment` task group. This task is only
available when the migration system is configured. The output of the `migrateData` task is to the staging directory; use
the `promoteStagingToProduction` task to transfer the staging data to the production directory (i.e. `data/`).

There are two ways to configure the migration system:

1. Setting the `targetVersion` of the `migration` extension (within the `compass` project extension) to a valid
   Minecraft version:

    ```gradle
    compass {
        migration {
            targetVersion = '1.19.4'
        }
    }
    ```

2. Setting the `migration-targetVersion` project property to a valid Minecraft version, either through the
   `gradle.properties` file or (as more recommended) the command-line:

    ```sh
    ./gradlew -Pmigration-targetVersion="1.19.4" migrateData
    ```

Configuring the property through the extension overrides configuring the property through the project property.

The data migration system will migrate the data in steps between the current version (as defined in the `version`
property of the `compass` extension) and the target version (without any excluded versions, as noted below).
The target version may be earlier or later than the current version (but not the exact same).

The progression of versions to step through is printed to the console whenever the migration system is configured, for
ease of debugging.

After performing a data migration, the sanitation task (`sanitizeData`) and the validation task (`validateData`) should
be run to ensure removal of unwanted fragments of data

## Excluded Versions

The migration system will step through all versions between the current and the target version (the intermediate
versions), except those which are specifically **excluded**. This is to prevent unique versions (such as April Fools
versions) from causing data loss when the mapping data passes through those versions.

Versions may be excluded from being intermediate through either the `excludedVersions` set property of the
`migrationExtension` or the `migration-excludedVersions` project property (as a comma-separated list). By default, the
April Fools versions are excluded, which are (as of writing):[^skipped-years]

- `15w14a` - "The Love and Hugs Update", released on April 1, 2015;[^mc2.0]
- `1.RV-Pre1` - The "Trendy Update", released on March 31, 2016;
- `3D Shareware v1.34` - "Minecraft 3D", released on April 1, 2019;
- `20w14infinite` - "The Ultimate Content Update", released on April 1, 2020;
- `22w13oneblockatatime` - "One Block at a Time Update", released on April 1, 2022
- `23w13a_or_b` - "The Vote Update", released on April 1, 2023

The up-to-date list of versions can be seen at the [repository for the Compass plugin][excluded].

> [!NOTE]
> Setting the excluded versions through the extension or the project property will fully override the default set of
> excluded versions. The above April Fools will need to be respecified in the extension or project property.

[jammer]: https://github.com/marchermans/JarAwareMapping

[parchmentjam]: https://github.com/ParchmentMC/ParchmentJAM

[excluded]: https://github.com/ParchmentMC/Compass/blob/dev/src/main/java/org/parchmentmc/compass/MigrationConfiguration.java

[^skipped-years]: For April 2014, Mojang changed the skins of all players to be a villager skin. For April 2017, Mojang announced a
fictional console, the "Mine & Craft Digital Leisure Device". For April 2018, Mojang  published a re-texture of blocks
through their asset distribution system.
[^mc2.0]: The first publicly April Fools version is from 2015. Minecraft 2.0, despite being an April Fools version for
April 2013, was never published to the launcher, and therefore cannot be encountered by the migration system
(either as a target version or as an intermediate version).
