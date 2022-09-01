# Orange CLI arguments and options

## Table of Contents

  - [SYNOPSIS](#synopsis)
  - [ARGUMENTS](#arguments)
  - [OPTIONS](#options)
  - [FLAGS](#flags)
  - [COMMANDS](#commands)

## SYNOPSIS
Orange.CLI.exe `[-? | -h |--help] [--command:<command>] [--target:<target>] [--bundles:<bundles>] [--android-sdk:<android-sdk>] [--passargs:<passargs>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets] [<project>]`

## ARGUMENTS
`<project>`

<div style="margin-left: 20px; margin-bottom: 20px;">

Path to the .citproj file.\
`<project>` can be defined as follows: `["path-to-citproj"]`
</div>

## OPTIONS
`-? | -h | --help`

<div style="margin-left: 20px; margin-bottom: 20px;">
Display help information about Orange.CLI. 
</div>

`--target:<target>`

<div style="margin-left: 20px; margin-bottom: 20px;">

Target defines various parameters of the project build.\
`<target>` can be defined as follows: `[Win|Mac|iOS|Android]`
</div>

`--command:<command>`

<div style="margin-left: 20px; margin-bottom: 20px;">

The command to execute.\
The available commands are described in the [COMMANDS](#commands) section.\
`<command>` can be defined as follows: `["command-name"]`
</div>

`--bundles:<bundles>`
<div style="margin-left: 20px; margin-bottom: 20px;">

The list of the bundles used by the command.\
`<bundles>` can be defined as follows: `["bundle"|"bundle-1, bundle-2, .., bundle-n"]`
</div>

`--android-sdk:<android-sdk>`

<div style="margin-left: 20px; margin-bottom: 20px;">

Android SDK location.\
Used to search for ADB when deploying game to a device.\
`<android-sdk>` can be defined as follows: `["path-to-android-sdk-directory"]`
</div>

`--passargs:<passargs>`

<div style="margin-left: 20px; margin-bottom: 20px;">

Redirects arguments to the game.\
`<passargs>` can be defined as follows: `["args-and-options-for-game"]`
</div>

## FLAGS

`--unpack_bundles`

<div style="margin-left: 20px; margin-bottom: 20px;">

Performs unpacking of bundles.
</div>

`--delete-tancache`

<div style="margin-left: 20px; margin-bottom: 20px;">

Deletes TangerineCacheBundle.
</div>

`--disable-asset-cache`

<div style="margin-left: 20px; margin-bottom: 20px;">

Asset cache will not be used.
</div>

`--disable-build-plugin-targets`

<div style="margin-left: 20px; margin-bottom: 20px;">

Targets specified in "PluginAssemblies" will not be built.
</div>


## COMMANDS
This section describes the standard commands.\
CitrusPlugin on projects can provide custom commands.

**`"Build"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Build" --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Builds the game, cook assets.
</div>

**`"Build and Run"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Build and Run" --target:<target> [--bundles:<bundles>] [--android-sdk:<sdk-path>] [--passargs:<passargs>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Builds the game, cook assets and performs the deployment of the game to the device.
</div>

**`"Rebuild Game"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Rebuild Game" --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Rebuilds the game, cook assets.
</div>

**`"Run Tangerine"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Run Tangerine" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Builds the scene editor and runs it if successful.
</div>

**`"New Project"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Works only from Orange.GUI.

**DESCRIPTION**\
Creates a new project.
</div>

**`"Cook Game Assets"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Cook Game Assets" --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Prepares assets for the game.
</div>

**`"Generate Lime Deserializers And Cloners"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `--command:"Generate Lime Deserializers And Cloners"`

**DESCRIPTION**\
Generates Lime deserializers and cloners.
</div>

**`"Generate Project Deserializers And Cloners"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Generate Project Deserializers And Cloners" [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Generates project deserializers and cloners.
</div>

**`"Generate Lime Persistence Schema"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `--command:"Generate Lime Persistence Schema"`

**DESCRIPTION**\
Generates Lime Persistence Schema.
</div>

**`"Delete Unpacked Bundles"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Delete Unpacked Bundles" --target:<target> [--bundles:<bundles>]  [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Deletes unpacked bundles.
</div>

**`"Optimize PNGs"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Optimize PNGs" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Invokes PngOptimizerCL on png with option not to optimize idat chunk.\
It removes all unwanted chunks like itxt and text.
</div>

**`"Unpack Bundle"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Works only from Orange.GUI.

**DESCRIPTION**\
Unpack the selected bundle.
</div>

**`"Update Localization Dictionary"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Update Localization Dictionary" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Updates localization dictionary.
</div>

**`"Show Duplicate Assets in Bundles"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Show Duplicate Assets in Bundles" --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Cook assets and outputs a list of duplicate files.\
Duplicates are calculated separately for each bundle.
</div>

**`"Analyze Resources"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Analyze Resources" --target:<target> [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Analyzes resources for:
- Cross Bundle Dependencies
- Missing Resources
- Unused Images
- Unused Sounds
- Suspicious Textures
</div>

**`"Save deduced cooking rules"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Works only from Orange.GUI.

**DESCRIPTION**\
Save deduced cooking rules.
</div>

**`"Synchronize documentation"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `--command:"Synchronize documentation"`

**DESCRIPTION**\
Creates Documentation directory in\
...\Citrus\Tangerine\Tangerine\\...
</div>

**`"Validate Assets"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Analyze Resources" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Performs validation of assets.
</div>

**`"Collect statistics for persistent data"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Collect statistics for persistent data" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Creates file "persistent_data_statistics.csv".\
This file contains various statistics for each scene.

</div>

**`"Migrate and Resave Citrus Assets"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Migrate and Resave Citrus Assets" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Migrates all scenes to the current version and saves.
</div>

**`"Show Duplicate Assets in Assets Directory"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Show Duplicate Assets in Assets Directory" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Outputs a list of duplicate files in ...Project\Data\\...
</div>

**`"Convert Dictionary.txt to the New Format`"**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Convert Dictionary.txt to the New Format" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Converts localization dictionary to the new format.
</div>

**`"Invalidate Fonts"`**

<div style="margin-left: 20px; margin-bottom: 20px;">

**SYNOPSIS**\
Orange.CLI.exe `<project> --command:"Invalidate Fonts" [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]`

**DESCRIPTION**\
Update charsets and generate fonts.
</div>
