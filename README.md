# React-JUCE-Examples

## ATTENTION
This repo is currently a work in progress pushed publicly for the purposes of testing CI workflows whilst
it's initial structure is completed. This message will be removed once `react-juce-examples` is ready 
for general use.

A collection of example plugins/apps built with the [React-JUCE](https://github.com/JoshMarler/react-juce) framework.

### TODO:
Add instructions for building JS bundles in Debug/Release as well as hot-reloading.

## Examples

#### GainPlugin

[GainPlugin](examples/GainPlugin)
A simple GainPlugin showing the basics of a React-JUCE implementation.

## Building the Examples

### CMake

React-JUCE-Examples supports CMake as a build system. 
To build the examples simply run CMake against the root directory/CMakeLists.txt 
and use your preferred generator.

We suggest performing an out-of-source build by creating a build directory adjacent 
to your react-juce-examples checkout. 

Run the following in Powershell/Cmd on Windows or Terminal on Mac.

```
mkdir react-juce-examples-build
cd react-juce-examples
```

##### CMake Build Via Ninja (Mac + Linux + Windows)

```
# Change to -DCMAKE_BUILD_TYPE=Release to see react-juce's
# Release build performance.
cmake ../react-juce-examples -G Ninja -DCMAKE_BUILD_TYPE=Debug .

# Build the example plugin you want to test.
# You can append _Standalone to the plugin target name if you just
# want to test a standalone version rather than making the example
# plugin available in your DAW/Host of choice.
ninja -j8 GainPlugin_Standalone

# If building standalone plugin variant run the following
# from the react-juce-examples-build directory to launch.
examples/GainPlugin/GainPlugin_artefacts/Debug/Standalone/ReactJUCEGainPlugin
```

##### CMake Build Via XCode (Mac)

```
# Change to -DCMAKE_BUILD_TYPE=Release to see react-juce's
# Release build performance.
cmake ../react-juce-examples -G Xcode -DCMAKE_BUILD_TYPE=Debug .

# Open the generated XCode project in XCode IDE and build/run
cmake --open .
```

##### CMake Build Via Visual Studio (Windows)

### TODO: Finish up instructions. Generic invocation for VS generator?
```
# Change to -DCMAKE_BUILD_TYPE=Release to see react-juce's
# Release build performance.
cmake ../react-juce-examples -G -DCMAKE_BUILD_TYPE=Debug . 

# Open the generated Solution in Visual Studio IDE and build/run
cmake --open .
```

### Projucer

Projucer builds are supported on Mac and Windows (For Linux please use CMake). 
To build the examples via the Projucer navigate to the example directory you 
wish to build (i.e. examples/GainPlugin) and load the `.jucer` project to 
generate for XCode or Visual Studio.

