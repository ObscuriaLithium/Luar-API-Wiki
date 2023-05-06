# Luar API
The Luar API allows you to modify the behavior of Minecraft through simple Lua scripts. With this mod, you can customize the technical part of your modpack, as well as add completely new logic to the server or effects to the client.

## Getting Started
Run Minecraft once so that the mod will generate the `.minecraft/luar` root directory and all the necessary sub-directories. All your scripts and libraries will be there.

In order to add a script to a game event, place your .lua file in the appropriate directory (for example, `.minecraft/luar/events/server/onEntityHurt` for [onEntityHurt][hurt] event). Your scripts will run automatically if they have no errors or non-existent values.

You can add custom libraries and function sets to `.minecraft/luar/libs` directory and then use them in scripts to avoid code repetition. For example, if we create a library `.minecraft/luar/libs/myDir/myLib.lua`, then we need to use the `require "myDir.myLib"` line to import it into any script. All imports should be placed in the header of the script.

## Basic Concept
Despite the fact that your script is initially empty, each event has its own environment, predefined values ​​and built-in libraries. This way you can immediately refer to the values related to the event. For example, for the [onEntityHurt][hurt] event, we can call `entity.getMaxHealth()` in the first line of the script, since the `entity` was put into the script by the event. All initial values ​​of each event are displayed on their wiki pages.

The following example script, placed in the onEntityHurt directory, will give out 5 diamonds to the attacked entity if it is a player.

```lua
if entity.is("player") then
   stack = builder.item("diamond").getDefaultStack()
   stack.setCount(5)
   entity.addStack(stack)
end
```

Note the `builder` value, which we also use without initialization. This is one of the built-in libraries ([Builder][builder]) supplied by the event, necessary for creating new objects.

These concept will make your scripts look more concise and prevent the import of unsuitable libraries that load the scripting environment.

## Examples

[Here][examples] you can take a look at some examples. However, I recommend using my [Discord Server][discord] where you can share your scripts and find more examples and community scripts.

[hurt]:
https://github.com/ObscuriaLithium/Luar-API-Wiki/wiki/event-onEntityHurt
[builder]:
https://github.com/ObscuriaLithium/Luar-API-Wiki/wiki/lib-Builder

[examples]:
https://github.com/ObscuriaLithium/Luar-API-Wiki
[discord]:
https://discord.gg/jSHHJSUWdY
