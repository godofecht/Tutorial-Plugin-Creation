# Tutorial-Plugin-Creation

Instructions for creating a bare-bones JUCE plugin project.

## What this is

A step-by-step guide, with screenshots, to starting your first audio plugin. A plugin is a small program that loads inside a DAW (digital audio workstation, such as Ableton Live, Logic Pro, FL Studio or Reaper) and adds an effect or an instrument to a track. The guide uses JUCE, a free C++ framework that most independent plugin makers use, and its project tool, the Projucer.

The folder `JuceBasicPluginTemplate` holds the project the steps produce. Built, it is a plugin that passes sound through unchanged and shows a window with the words "Hello World!". It is the empty starting point you fill with your own effect.

## What you can learn from it

- How a plugin project is set up before any audio code is written (Music Technology, Computer Science).
- What JUCE modules are: separate libraries for audio, graphics, file formats and so on, which you switch on as you need them.
- What an exporter is: a setting that tells the Projucer which IDE (integrated development environment, the program you write and build code in) to make a project for, such as Xcode on a Mac or Visual Studio on Windows.
- The two halves of every JUCE plugin: the processor, which handles audio, and the editor, which draws the window.

## Run it

### On your own computer

**You will need:**

- [JUCE](https://juce.com/get-juce/), which includes the Projucer. The screenshots show JUCE and Projucer 7.0.5.
- An IDE with a C++ compiler:
  - macOS: [Xcode](https://developer.apple.com/xcode/).
  - Windows: [Visual Studio 2022 Community](https://visualstudio.microsoft.com/vs/community/) with the "Desktop development with C++" workload.
  - Linux: a C++ compiler and `make`.
- A DAW to test the plugin in, or use the standalone app that JUCE also builds.

The screenshots were taken on macOS.

### Create a new plugin project

1. Download and install JUCE from the [JUCE website](https://juce.com/get-juce/).

2. Launch the Projucer app. It is in the JUCE folder.

   <img width="737" alt="A macOS Finder window showing the contents of the JUCE folder, with the Projucer application selected. Other items include DemoRunner, docs, examples, extras and modules." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/d29e1492-760d-4f60-86ee-194f54774087">

3. From the side list, select **New Project**, then select the project type **Basic** under **Plug-In**.

   <img width="900" alt="The Projucer New Project window. Basic is selected under Plug-In on the left. On the right are the Project Name box, a list of modules with juce_audio_basics, juce_audio_devices and juce_audio_formats ticked, the path to modules, a list of exporters with Xcode (macOS) ticked, and a Create Project button." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/c2b2c13a-73f5-4ec5-ae92-e83b88512f3a">

4. Type a name for your project in **Project Name**.

   <img width="577" alt="The Project Name field, showing the placeholder text NewProject." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/5c5fb124-48d8-4e80-b32f-c90b02cd45fa">

5. The Projucer picks the [modules](https://docs.juce.com/master/index.html) (libraries) the project type needs. You can tick more from the list if you need them.

   <img width="575" alt="The Modules list with juce_audio_basics, juce_audio_devices and juce_audio_formats ticked, juce_analytics unticked, and 16 more below." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/ed2e3abc-01b5-4761-8305-215fae36af53">

6. Tick the exporters for the computers you want to build on. Choose Xcode (macOS) for a Mac and Visual Studio 2022 for Windows.

   <img width="571" alt="The Exporters list with Xcode (macOS) ticked and Xcode (iOS), Visual Studio 2022 and Visual Studio 2019 unticked, and 5 more below." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/f0ede3b2-c2a9-454d-9bff-960ee3f33326">

7. Click **Create Project...** and choose where to save it.

   <img width="157" alt="The purple Create Project button." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/5243aa3e-ad95-4106-a575-fb8e097a0cef">

8. Under **File Explorer** you can add files and resources to the project. Click the **plus** icon to create new files, or drag in assets and folders.

   <img width="898" alt="The Projucer project window. The File Explorer lists PluginProcessor.cpp, PluginProcessor.h, PluginEditor.cpp and PluginEditor.h. A menu from the plus icon offers options such as Add New Group, Add Existing Files and Add New CPP File." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/9c0741cb-8203-448d-9cb7-983ecfca7242">

9. In the same way, you can add or remove **Modules** and **Exporters** from their sections, using the **plus** icon in each.

   <img width="899" alt="The Modules section open, listing twelve modules from juce_audio_basics to juce_gui_extra, with the Add a module menu showing Global JUCE modules path, Global user modules path and Exporter paths. The window shows JUCE v7.0.5 and Projucer 7.0.5." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/a57f9f47-3e0c-453b-91e8-28755cc72991">

   <img width="898" alt="The Exporters section open with Xcode (macOS) and its Debug and Release configurations, and a menu titled Create a new export target listing Xcode (macOS), Xcode (iOS), Visual Studio 2022, 2019 and 2017, Linux Makefile, Android and Code::Blocks." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/53fa8311-6e3a-4df8-b74b-8d3d85558e2c">

10. Click the IDE icon at the top, next to **Selected exporter**, to save the project and open it in your IDE. You can now start editing and building.

    <img width="898" alt="The Projucer project window with Xcode (macOS) as the selected exporter and the mouse over the round button beside it, which shows the tooltip Save and Open in IDE." src="https://github.com/SolomonMoulangLewis/JuceBasicPluginTemplate/assets/92383851/804910b7-2939-4121-9ead-bd4c53ea41d9">

### Use the included template instead

1. Download this repo with **Code > Download ZIP** on GitHub, or run:

   ```bash
   git clone https://github.com/godofecht/Tutorial-Plugin-Creation.git
   ```

2. In the Projucer, check **File > Global Paths** points to the `modules` folder in your JUCE download.
3. Open `JuceBasicPluginTemplate/JuceBasicPluginTemplate.jucer`.
4. Pick the exporter for your computer (Xcode (macOS), Visual Studio 2022 or Linux Makefile) and click the IDE icon to save and open it.
5. Build. The project builds a VST3 plugin, an AU plugin (macOS only) and a standalone app.

When it works, the plugin window is 400 by 300 pixels and says "Hello World!" in the middle. Sound passes through unchanged.

## How it works

Every JUCE plugin has two classes. The processor gets audio from the DAW in small blocks and can change it. The editor draws the plugin window. The template's processor leaves the audio alone, and its editor only draws text.

| File or folder | What is in it |
|---|---|
| `JuceBasicPluginTemplate/JuceBasicPluginTemplate.jucer` | The Projucer project: modules, exporters and plugin settings. |
| `JuceBasicPluginTemplate/Source/PluginProcessor.cpp` | The audio code. `processBlock` is called for every block of audio. |
| `JuceBasicPluginTemplate/Source/PluginProcessor.h` | The processor class declaration. |
| `JuceBasicPluginTemplate/Source/PluginEditor.cpp` | The window. `paint` draws "Hello World!" and `setSize (400, 300)` sets its size. |
| `JuceBasicPluginTemplate/Source/PluginEditor.h` | The editor class declaration. |
| `JuceBasicPluginTemplate/JuceLibraryCode/` | Files the Projucer writes for you. Do not edit them; they are rewritten each time you save. |

## Ideas to try

1. Change the text and window size in `JuceBasicPluginTemplate/Source/PluginEditor.cpp`.
2. Make a volume control. In `processBlock` in `JuceBasicPluginTemplate/Source/PluginProcessor.cpp`, multiply every sample in `channelData` by 0.5 and listen to the sound get quieter.
3. Make a distortion. In the same loop, pass each sample through `std::tanh` after multiplying it by 5. This soft-clips the waveform, rounding off the peaks, which adds harmonics (higher overtones that make the sound brighter and grittier).
4. Ambitious: add a slider to the editor that controls the volume, using `juce::AudioProcessorValueTreeState`. [JUCE-Ladder-Filter-Implementation](https://github.com/godofecht/JUCE-Ladder-Filter-Implementation) shows one way to connect sliders to parameters.

## Technical details

- The template's `.jucer` has three exporters: `LINUX_MAKE`, `VS2022` and `XCODE_MAC`.
- Plugin formats enabled in `JuceLibraryCode/JucePluginDefines.h`: VST3, AU and Standalone. VST2, AUv3, AAX, Unity and LV2 are off.
- The plugin name is `JuceBasicPluginTemplate`. The manufacturer is the Projucer default, `yourcompany`. Change both in the Projucer project settings (the gear icon) before you share a plugin.
- Every module has `useGlobalPath="1"`, so the Projucer's global JUCE path is used.

JUCE's own step-by-step guide covers the same ground: [Create a basic Audio/MIDI plugin, Part 1: Setting up](https://juce.com/tutorials/tutorial_create_projucer_basic_plugin/).

## Project status

The guide and template were written in October 2023 against JUCE 7.0.5. Newer versions of the Projucer may look a little different. The template has not been rebuilt since.

## Licence

You can use, copy and change this code and guide for any purpose, as long as you keep the copyright notice. See [LICENSE](LICENSE) (MIT).

JUCE has its own licence terms. Check [the JUCE website](https://juce.com/) before you share a built plugin.

## Credits

- Guide, screenshots and template by Solomon Moulang Lewis (2023).
- Repo maintained by Abhishek Shivakumar.
- Built with [JUCE](https://juce.com/) and the Projucer.
