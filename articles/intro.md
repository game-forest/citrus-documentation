# Citrus Engine

Major engine components are named after Citrus fruits. In the repository you'll see various directories. Following is what they are about:

- Tangerine - scene editor
- Lime - core library
- Orange - cook game assets, build and run projects
- Examples - example projects also used as templates for new projects
- Yuzu - serialization library
- Kumquat - generates code from scenes
- Lemon - bindings for native 3rd party libraries.

In order to run Tangerine and Orange you'll need .NET5 runtime installed. Or you can use following scripts which are located in each example project directory:

- `./Examples/<project_name>/run-orange.ps1`
- `./Examples/<project_name>/run-tangerine.ps1`

They will install local .NET5 runtime in `./dotnet/` directory and run corresponding application with installed runtime.

Following scripts are for MAC OS and you'll need Visual Studio for Mac installed.

- `./Examples/<project_name>/run-orange.command`
- `./Examples/<project_name>/run-tangerine.command`

To write code you'll need visual studio for either windows or mac and .NET5 SDK.

Also if you have .NET5 installed you can also use `./Orange.bat` and `./Tangerine.bat`.

To create new project run Orange, open any example project and execute action 
`New Project`. First select project template from `./Examples` directory and in the next directory selection dialog choose directory for you new project.
