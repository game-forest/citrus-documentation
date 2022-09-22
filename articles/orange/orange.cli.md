# Orange command line interface

## Usage

```
Orange.CLI.exe [command] [arguments] [options]
```

## Commands

- `show-actions`

    Show all actions.
    `--project` can be specified to also show the commands belonging to the project.
    ```
    Orange.CLI.exe show-actions [--project:<project>]
    ```

- `show-action-help`
    
    Show help for specific action.
    `--project` can be specified to also show the commands belonging to the project.
    ```
    Orange.CLI.exe show-action-help <action> [--project:<project>]
    ```

## Arguments

- `<project>`
    
    Path to a .citproj file.

## Options

It is also possible to pass custom options.
Options format `--option-name[:value]`

- `-? | -h | --help`

    Display help information about Orange.CLI.
- `--target:<target>`

    Target defines various parameters of the project build.
    Possible values of `<target>` are: `[Win|Mac|iOS|Android]`
- `--action:<action>`

    The action to execute in new format (build, cook_game_assets, ...).
    The available actions are described in the [actions](#actions) section.
- `--command:<command>`

    The action to execute in old format ("Build", "Cook Game Assets", ...).
    The available actions are described in the [actions](#actions) section.
    > obsolete (exists for compatibility with existing scripts)
- `--bundles:<bundles>`

    The list of the bundles used by the action.
    Possible format of `<bundles>` is `["bundle"|"bundle-1, bundle-2, .., bundle-n"]`.
- `--android-sdk:<android-sdk>`

    Path to android SDK directory.
    Used to search for ADB when deploying game to a device.
- `--passargs:<passargs>`

    Arguments and options that will be redirected to the game.
- `--unpack_bundles`

    Performs unpacking of bundles.
- `--delete-tancache`

    Deletes TangerineCacheBundle.
- `--disable-asset-cache`

    Asset cache will not be used.
- `--disable-build-plugin-targets`

    Targets specified in "PluginAssemblies" will not be built.
- `--disable-filesystem-watcher`

    Required for virtual machine based macOS because FileSystemWatcher is crashing under such conditions.

## Actions

This section describes the standard actions.
CitrusPlugin on projects can provide custom actions.

### `build`

Builds the game, cook assets.

```
Orange.CLI.exe <project> --action:build --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]
```

### `build_and_run`

Builds the game, cook assets and run the game.

```
Orange.CLI.exe <project> --action:build --target:<target> [--android-sdk:<sdk-path>] [--passargs:<passargs>] [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]
```

### `rebuild`

Rebuilds the game, cook assets.

```
Orange.CLI.exe <project> --action:build --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]
```

### `run_tangerine`

Builds the scene editor and runs it if successful.

```
Orange.CLI.exe <project> --action:run_tangerine [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `cook_game_assets`

Prepares assets for the game.

```
Orange.CLI.exe <project> --action:cook_game_assets --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]
```

### `generate_lime_deserializers_and_cloners`

Generates Lime deserializers and cloners.

```
Orange.CLI.exe --action:generate_lime_deserializers_and_cloners
```

### `generate_project_deserializers_and_cloners`

Generates project deserializers and cloners.

```
Orange.CLI.exe <project> --action:generate_project_deserializers_and_cloners [--delete-tancache] [--disable-build-plugin-targets]
```


### `generate_lime_persistence_schema`

Generates Lime Persistence Schema.

```
Orange.CLI.exe --action:generate_lime_persistence_schema
```

### `delete_unpacked_bundles`

Deletes unpacked bundles.

```
Orange.CLI.exe <project> --action:delete_unpacked_bundles --target:<target> [--bundles:<bundles>]  [--delete-tancache] [--disable-build-plugin-targets]
```

### `optimize_pngs`

Invokes PngOptimizerCL on png with option not to optimize idat chunk.
It removes all unwanted chunks like itxt and text.

```
Orange.CLI.exe <project> --action:optimize_pngs [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `update_localization_dictionary`

Updates localization dictionary.

```
Orange.CLI.exe <project> --action:update_localization_dictionary [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `show_duplicate_assets_in_bundles`

Cook assets and outputs a list of duplicate files.
Duplicates are calculated separately for each bundle.

```
Orange.CLI.exe <project> --action:show_duplicate_assets_in_bundles --target:<target> [--bundles:<bundles>] [--unpack_bundles] [--delete-tancache] [--disable-asset-cache] [--disable-build-plugin-targets]
```

### `analyze_resources`

Analyzes resources for:
- Cross Bundle Dependencies
- Missing Resources
- Unused Images
- Unused Sounds
- Suspicious Textures

```
Orange.CLI.exe <project> --action:analyze_resources --target:<target> [--delete-tancache] [--disable-build-plugin-targets]
```

### `synchronize_documentation`

Creates Documentation directory in ...\Citrus\Tangerine\Tangerine\\...

```
Orange.CLI.exe --action:synchronize_documentation
```

### `validate_assets`

Performs validation of assets.

```
Orange.CLI.exe <project> --action:validate_assets [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `collect_statistics_for_persistent_data`

Creates file "persistent_data_statistics.csv".
This file contains various statistics for each scene.

```
Orange.CLI.exe <project> --action:collect_statistics_for_persistent_data [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `migrate_and_resave_citrus_assets`

Migrates all scenes to the current version and saves.

```
Orange.CLI.exe <project> --action:migrate_and_resave_citrus_assets [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `show_duplicate_assets_in_assets_directory`

Outputs a list of duplicate files in ...Project\Data\\...

```
Orange.CLI.exe <project> --action:show_duplicate_assets_in_assets_directory [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `convert_dictionary_txt_to_the_new_format`

Converts localization dictionary to the new format.

```
Orange.CLI.exe <project> --action:convert_dictionary_txt_to_the_new_format [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```

### `invalidate_fonts`

Update charsets and generate fonts.

```
Orange.CLI.exe <project> --action:invalidate_fonts [--target:<target>] [--delete-tancache] [--disable-build-plugin-targets]
```
