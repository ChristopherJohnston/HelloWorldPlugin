# HelloWorldPlugin

Example barebones plugin for developing JUCE plugins on Mac in VS Code.

This is based on the "[Hello World](https://docs.juce.com/master/tutorial_create_projucer_basic_plugin.html)" example on the JUCE tutorials site.

## Prerequisites

1. Juce should be installed and general familiarity with JUCE is assumed. See www.juce.com
2. A JUCE_FRAMEWORKPATH Environment variable should be defined (E.g. ~/JUCE). This is used to reference module source files and determine the location of the AudioPluginHost application. You can use vscode workspace settings to set the env or an environment management shell extension such as [direnv](https://direnv.net) and define the variable in an .envrc file.
3. The [C/C++ Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)

## Build Instructions

1. Clone the repository.
2. Open HelloWorldPlugin.jucer in the Jucer app.
3. Click the "Save and Open in IDE" button. Jucer will generate a "Builds/MacOSX" folder and an xcodeproj workspace, then open the project in XCode. Close xcode as we will be using vscode.
4. Open the repository base directory in VSCode.
5. Build the project using shortcut Cmd+Shift+B, or "Terminal -> Run Build Task...". This will begin a Debug build (which is the default build task)
6. Select a scheme to build (All is the default)

## Debug Instructions

1. Set a breakpoint in the paint method in PluginEditor.cpp
2. Start debugging by Pressing F5 or choosing "Run -> Start Debugging", select the VST3 scheme.
3. VS Code will compile the project and start the AudioPluginHost app.
4. The HelloWorldPlugin should be loaded in AudioPluginHost as we specify a .filtergraph file in the arguments.
5. Double click the HelloWorldPlugin and the breakpoint should be hit in VSCode.

## Key Files

There are 3 key files in the .vscode directory which enable this to work in VS Code.

### tasks.json

Here we define the Compilation tasks. These call xcodebuild to perform the compilation. We use a "pickList" input to allow the developer to choose which scheme to compile at build time. There is also a "Build All" task which will compile for all schemes.

### launch.json

Here we define the debug configurations. For this plugin we launch the JUCE AudioPluginHost application, passing in argument of HelloWorldPlugin.filtergraph, which tells the app to load this plugin.

### c_cpp_properties.json

Here we define the C++ include paths, which allows intellisense to find the library code. We force include the /JuceLibraryCode/JucePluginDefines.h in order to pre-load the relevant settings.

## Acknowledgements

Thanks to the contributions in [this JUCE forum page](https://forum.juce.com/t/visual-studio-for-mac/22358/20) for details of launch.json and tasks.json

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/cpjohnston)
