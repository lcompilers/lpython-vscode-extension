# lpython-vscode-extension
LPython extension for VSCode

<img src="https://user-images.githubusercontent.com/68434944/183258400-5bd2bc4e-594d-4339-aaa9-0d033215ca58.gif" height=400/>

There are no pre-packaged versions of this extension, but will be packaging the extension to VS Code market place very soon. 

## Key Features

1. Linting: highlights errors and warnings in your LPython code which helps you to identify and correct programming errors.
2. Document Symbol Lookup: You can navigate symbols inside a file with `Ctrl + Shift + O`. By typing `:` the symbols are grouped by category. Press Up or Down and navigate to the place you want.
3. Syntax Highlight: Coloring and styling of source code displayed in vscode editor using [TextMate grammars](https://macromates.com/manual/en/language_grammars).

## Language Server

- The Language Server is written in TypeScript, which uses [Microsoft’s official language server module](https://github.com/microsoft/vscode-languageserver-node). 
- Communication between the language server and LPython Compiler is done with 
    ```bash
        const stdout = await runCompiler(text, "<flags>", settings); 
    ```

## Usage

1. Install LPython: Refer to [lpython documentation](https://github.com/lcompilers/lpython#installation) (build as usual, but ensure `-DWITH_LSP=yes` in cmake).

2. Install npm, for example via Conda:
```
conda create -n npm nodejs
conda activate npm
```

3. Clone the repository:
```bash
git clone https://github.com/lcompilers/lpython-vscode-extension
```

4. Build the extension:
```bash
cd lpython-vscode-extension && npm install && npm run compile
```

5. Create the package locally:
```bash
npm install vsce -g
vsce package
```
Say "Y" to the question "Using `*` activation is usually a bad idea as it impacts performance. Do you want to continue?".

This will generate a `lpyth-1.0.0.vsix` file in your current directory, which
can then be imported as an extension in VSCode:
* Go to extensions (on the left)
* Click on the `...` on the top right
* Click on "Install from VSIX" and select the `lpyth-1.0.0.vsix`
* Select the `lpyth` extension in your installed extensions
* Click on the Settings button -> Extension Settings
* Search for "lpyth"
* Change "LPython Language Server › Compiler: Executable Path" to the correct
  path to the `lpython` binary on your system

The extension should now work. Create a new file `a.py` and put `x = 5` in
there. The `x` should get highlighted with an error message that `x` is not
declared (you have to change it to `x: i32 = 5` to work).


In the settings for `lpyth` extension: set the path as your binary path.

<img src="https://user-images.githubusercontent.com/68434944/183254852-0a68e08c-6094-4c9a-b63b-c2aec83bce3e.png" height=300/>

## Contributing

We welcome contributions from anyone, even if you are new to open source. 

1. To contribute, submit a PR against your repository at: https://github.com/lcompilers/lpython-vscode-extension
2. Please report any bugs you may find at our issue tracker: https://github.com/lcompilers/lpython-vscode-extension/issues

We welcome all changes, big or small! 
