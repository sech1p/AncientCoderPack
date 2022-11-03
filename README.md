THIS CURRENTLY DOES NOT WORK. Several components are being rewritten.

**What is the Retro Coder Pack?**

The Retro Coder Pack (RCP) aims to create a buildable gradle that allows users to view decompile source
code from older Minecraft versions. Currently, the only version being worked on is Alpha 1.2.6. It is inspired
by the Mod Coder Pack (MCP), a now-defunct tool that allowed users to view Minecraft's source code for mod development.
I'm hoping this project will do the same and encourage mod-development of older MC versions, and generally act as an educational
tool for people to learn about the history of Minecraft.

**What tools are used for RCP?**

I originally created this project directly including and using files from the Mod Coder Pack version 2.5, but due to MCP's license 
I have been moving away from these in favor of more modern tools. RCP does use some tools developed by 
OceanLabs, MinecraftForge, and FabricMC, but these are Maven dependencies that are publicly available for others.
The only tool directly included is McAssetExtractor, a forked tool originally developed by GitHub user rhmeuer.

A toolchain text file wll be included to go more in depth about everything, but here's a brief rundown of the tools 
and what they do:

- RetroGuard by OceanLabs/MCP: Deobfuscation of classes, methods, and fields. [GitHub](https://github.com/ModCoderPack/Retroguard).
- MCInjector by OceanLabs/MCP: Adding exceptions for methods. [GitHub](https://github.com/ModCoderPack/MCInjector).
- Enigma by cuchaz, fork by FabricMC: Parameter name deobfuscation. [GitHub](https://github.com/FabricMC/Enigma).
- Fernflower by JetBrains, fork by MinecraftForge: Decompilation, Local variable naming. [GitHub](https://github.com/MinecraftForge/FernFlower).
- ApplyDiff.exe by (I believe) GNU: Applying diff patches to make everything run. Right now the patch files and the actual
executable are currently excluded because a) they're no longer compatible with the current setup and b) licensing. You can still see 
them mentioned in the gradle. Eventually another DiffPatch plugin (likely the one from Forge) will be used instead, and new patch files
will be created. No GitHub for this one.
- McAssetExtractor by rhmeuer, fork by me: extracting the run-time assets (not the ones from the client JAR) from Mojang's servers 
into the workspace. [Original GitHub](https://github.com/rmheuer/McAssetExtractor). [Forked GitHub](https://github.com/moist-mason/McAssetExtractor).

**What mappings does RCP use?**

For methods, classes, and fields, RCP uses SRG files. The SRG file for Minecraft Alpha 1.2.6 was created by MCP-Hackers,
a team that currently develops a much older, similar project to RCP known as RetroMCP. Currently, RetroMCP uses Tinyv2
mappings for its build process. The SRG files that I am using are from a now-defunct version of RetroMCP that you can
view [here](https://github.com/MCPHackers/RetroMCP). I intend on adding to these mappings by filling in unnamed fields
and methods (func_101_a --> myMethod).

For parameters, RCP uses Enigma. Aside from an older version of MCInjector (that RCP doesn't use), Enigma is pretty much the only 
deobfuscator/bytecode editor, that I know of, that allows for direct editing of parameter names. Lack of options and Enigma's 
ease of use makes it the preferred choice. The parameter names are written by me, and are currently work in progress.

Stay tuned for a full release.
