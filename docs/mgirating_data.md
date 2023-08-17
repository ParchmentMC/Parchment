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

## Excluded Versions

The migration system will step through all versions between the current and the target version (the intermediate
versions), except those which are specifically **excluded**. This is to prevent unique versions (such as April Fools
versions) from causing data loss when the mapping data passes through those versions.

Versions may be excluded from being intermediate through either the `excludedVersions` set property of the
`migrationExtension` or the `migration-excludedVersions` project property (as a comma-separated list). By default, the
April Fools versions are excluded, which are (as of writing)[^1]:

- `15w14a`
- `1.RV-Pre1`
- `3D Shareware v1.34`
- `20w14infinite`
- `22w13oneblockatatime`
- `23w13a_or_b`

The up-to-date list of versions can be seen at the [repository for the Compass plugin][excluded].

> **Note**
> Setting the excluded versions through the extension or the project property will fully override the default set of
> excluded versions. The above April Fools

[jammer]: https://github.com/marchermans/JarAwareMapping

[parchmentjam]: https://github.com/ParchmentMC/ParchmentJAM

[excluded]: https://github.com/ParchmentMC/Compass/blob/dev/src/main/java/org/parchmentmc/compass/MigrationConfiguration.java

[^1]: Minecraft 2.0, despite being an April Fools version, was never published to the launcher, and therefore cannot be
encountered by the migration system (either as a target version or as an intermediate version). 
