A nightly build from the [master](https://github.com/Microsoft/TypeScript/tree/master) branch is published nightly to NPM and NuGet. Here is how you can get it and use it with your tools.

## Using npm

```shell
npm install -g typescript@next
```

## Using NuGet with MSBuild:

> Note: You'll need to configure your project to use the NuGet packages instead of any other installations.

The nightlies are available on https://www.myget.org/gallery/typescript-preview

There are two packages:

* `Microsoft.TypeScript.Compiler`: Tools only (`tsc.exe`, `lib.d.ts`, etc.) .
* `Microsoft.TypeScript.MSBuild`: Tools as above, as well as MSBuild tasks and targets (`Microsoft.TypeScript.targets`, `Microsoft.TypeScript.Default.props`, etc.)


## Visual Studio Code 

1. Install the npm package `npm install typescript@next`, to your local `node_modules` folder.
2. Update, `.vscode/settings.json` with the following:

   ```json
   "typescript.tsdk": "<path to your folder>/node_modules/typescript/lib"
   ```

## Sublime Text

> Note: This is currently a manual process. See the [relevant issue](https://github.com/Microsoft/TypeScript-Sublime-Plugin/issues/370) which tracks automating the process.

1. Install the npm package `npm install typescript@next`, to a local `node_modules` folder, then
2. Go to your Packages folder
    * Mac/Linux: `~/"Library/Application Support/Sublime Text 3/Packages`
    * Windows: `%APPDATA%\Sublime Text 3\Packages`
3. Copy:
 * `<path to your folder>/node_modules/typescript/lib/tsserver.js` to `<Packages>/TypeScript/tsserver/`
 * `<path to your folder>/node_modules/typescript/lib/lib.d.ts` to `<Packages>/TypeScript/tsserver/`

More information is available at: https://github.com/Microsoft/TypeScript-Sublime-Plugin#installation

## Visual Studio 2013 and 2015

> Note: Most changes do not require you to install a new version of the VS TypeScript plugin in.

The nightly build currently does not include the full plugin setup, but we are working on publishing an installer on a nightly basis as well.

1. First, install the npm package with `npm install typescript@next` to a local `node_modules` folder, then
2. Download the [VSDevMode.ps1](https://github.com/Microsoft/TypeScript/blob/master/scripts/VSDevMode.ps1) script.

   > Also see our wiki page on [using a custom language service file](https://github.com/Microsoft/TypeScript/wiki/Dev-Mode-in-Visual-Studio#using-a-custom-language-service-file).
3. From a poweshell command window, run:
   * VS 2015:

     ```posh
     VSDevMode.ps1 14 -tsScript <path to your folder>/node_modules/typescript/lib
     ```
   * VS 2013:

     ```posh
     VSDevMode.ps1 12 -tsScript <path to your folder>/node_modules/typescript/lib
     ```