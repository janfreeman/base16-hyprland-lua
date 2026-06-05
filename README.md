# base16-hyprland-lua

This repo provides templates for using
[Base16](https://github.com/tinted-theming/home) color schemes with
Hyprland's new Lua configuration.

> [!NOTE]
> It is recommended to apply this theme with [Tinty](https://github.com/tinted-theming/tinty).

If you are using Tinty, please add this to `~/.config/tinty/config.toml` with the rest of theme items:

```toml
[[items]]
path = "https://github.com/janfreeman/base16-hyprland-lua"
name = "base16-hyprland-lua"
themes-dir = "colors"
write-to-file = ["~/.config/hypr/colors.lua"] # Path to your Hyprland config
hook = "hyprctl reload" # Reloads hyprland after theme change
supported-systems = ["base16"]
```
> [!WARNING]
> Don't forget to execute `tinty install` and `tinty init` before modifying the Hyprland config.

Then, in your Hyprland Lua config, simply import it and use it like any variable:
```lua
-- Add this to the top of the file
colors = require("colors")

-- And then use it anywhere like so
hl.config({
  general = {
    -- ...
    col = {
      active_border   = { colors = {colors.base0C, colors.base0B}, angle = 45 },
      inactive_border = colors.base01,
    },
    -- ...
  },
```
Also, If you haven't already done so, it may be a good idea to also run `tinty init` on Hyprland startup. You can do so by adding a [start event](https://wiki.hypr.land/Configuring/Basics/Autostart/) in the Hyprland config, like so:
```lua
hl.on("hyprland.start", function ()
  hl.exec_cmd("tinty init")
  -- the rest of your autostart items
end)

```
