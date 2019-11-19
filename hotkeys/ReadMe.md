# The Problem I'm Solving

These hotkeys are for users of Visual Studio for Mac who have their Control and Command keys swapped in the system settings.

Visual Studio for Mac has a built-in set of VS hotkeys to match its VS for Windows counterpart. However, these hotkeys do not take into consideration that many Mac users who come from a Windows background will have swapped their **Command(⌘)** and **Control(⌃)** keys. This is because Mac ueses the Command(⌘) key as its primary modifier key for things like Copy (⌘+C), Undo (⌘+Z), etc. As a result, all of the built-in "Windows-Style" hotkeys will be backwards on a Mac that has swapped these keys.

As an additional confusion point, VS for Mac uses the **Option(⌥)** key as the Windows **Alt** key even though it is not in the correct location on the keyboard

On Windows:

[Control] [Meta/Windows] **[Alt]**

On Mac:

[Control] **[Option]** [Command]

# The Solution

- Command(⌘) key has been set as the primary modifier key. This is the "Meta" key in the config file. Thinks like copy, paste, and undo (as well as the vast majority of other hotkeys in VS) will use Command(⌘).

- Control(^) key has been set as the alt key, which aligns to the keyboard order outlined above.

- All other hotkeys that previously used Command(⌘) now use Option(⌥). This is the "Alt" key in the config file.

# Installation Instructions

Copy the `Custom.mac-kb.xml` file to `~/Library/VisualStudio/[version]/KeyBindings` folder

It is also strongly recommended that you do the following:

- Open the Mac System Keyboard Settings

- Navigate to the "Shortcuts" tab

- In the "Mission Control" section
  - disable application windows
  - disable all hotkeys under the Mission Control callout.
  
- In the "Accessibility" menu, turn off the voiceover toggle

- In the "Function Keys" menu, click the **+** button to add the Visual Studio app. This will cause your touchbar to show the F1-F12 keys by default when you have Visual Studio open, which will save your pinky much effort.

# Some Exceptions To The Rule

There are a few hotkeys that you may find are still setup as defined by Microsoft. This is because changing those hotkeys would conflict with hotkeys defined internally in the Mac OS, and because I don't *personally* use these VS hotkeys. So why disable a bunch of my OS's hotkeys? 

To understand in more detail, consider `MonoDevelop.Debugger.DebugCommands.ShowDisassembly`. It is set to **^+⌥+D**, and changing it would transform it into **^+⌘+D**, which conflicts with the Mac OS "Lookup in Dictionary" shortcut.

To find these hotkeys which I have not changed, you can try running a diff with the [Visual Studio (Windows) defaults](https://github.com/mono/monodevelop/blob/master/main/src/core/MonoDevelop.Ide/options/KeyBindingSchemeVisualStudio.xml)
