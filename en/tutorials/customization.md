---
title: Customization of Lite-XL
---

This is a simple guide to explain how to customize your install of Lite-XL by changing fonts, themes, keybinds, plugins, and a lot more.

##### Note: This page is still under construction. Expect it to change a lot over the next few days.

## So, where are the settings?

They're here, near the bottom left corner of the window:

![settings]

When you click on it, a file called `init.lua` opens up, which is essentially like .bashrc but for lite-xl; it runs everytime the app is started (either by launching it or by running the command `Core: Restart`), and you can add a lot of things to it that it'll execute while launching (which will be discussed in the rest of the article).

## init.lua

right now, `init.lua` should be looking something like this: 
```lua
-- put user settings here
-- this module will be loaded after everything else when the application starts
-- it will be automatically reloaded when saved

local core = require "core"
local keymap = require "core.keymap"
local config = require "core.config"
local style = require "core.style"

------------------------------ Themes ----------------------------------------

-- light theme:
-- core.reload_module("colors.summer")

--------------------------- Key bindings -------------------------------------

-- key binding:
-- keymap.add { ["ctrl+escape"] = "core:quit" }


------------------------------- Fonts ----------------------------------------

-- customize fonts:
-- style.font = renderer.font.load(DATADIR .. "/fonts/FiraSans-Regular.ttf", 14 * SCALE)
-- style.code_font = renderer.font.load(DATADIR .. "/fonts/JetBrainsMono-Regular.ttf", 14 * SCALE)
--
-- font names used by lite:
-- style.font          : user interface
-- style.big_font      : big text in welcome screen
-- style.icon_font     : icons
-- style.icon_big_font : toolbar icons
-- style.code_font     : code
--
-- the function to load the font accept a 3rd optional argument like:
--
-- {antialiasing="grayscale", hinting="full"}
--
-- possible values are:
-- antialiasing: grayscale, subpixel
-- hinting: none, slight, full

------------------------------ Plugins ----------------------------------------

-- enable or disable plugin loading setting config entries:

-- enable plugins.trimwhitespace, otherwise it is disable by default:
-- config.plugins.trimwhitespace = true
--
-- disable detectindent, otherwise it is enabled by default
-- config.plugins.detectindent = false
```

The file has hints inside itself already, but we'll go into a bit more detail of what each setting does here (since this isn't going to be a part of the source code of the app).

let's begin!

### 1. Require

take a look at the first bit of code:
```lua
local core = require "core"
local keymap = require "core.keymap"
local config = require "core.config"
local style = require "core.style"
```

so here in the beginning of the file, you link to specific modules in the codebase of the editor, since lite-xl is built such that modules made of multiple files have their entry point as init.lua; you can add others too, if you need it (for example, the LSP server plugin needs you to require the plugin folder here at the top by adding `local lsp = require "plugins.lsp"`).

[settings]: {{ 'assets/img/screenshots/settings.jpg' | relative_url }}