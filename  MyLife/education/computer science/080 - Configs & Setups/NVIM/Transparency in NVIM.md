Date: 2026-01-20
Tags: {
#W
[[%Nvim]]
[[%Config]]
[[%UI]]
}


# Transparency in NVIM


To achieve full transparency in NVIM with NVChad, you need to have this code in`~/.config/nvim/lua/custom/chadrc.lua`:

```lua
---@type ChadrcConfig
local M = {}

M.ui = {
  theme = "chadracula",
  transparency = true,
}

M.plugins = "custom.plugins"

return M
```
This alone will achieve nearly everything, but the file preview at the top wont be transparent for that you need more code in your `custom/init.lua`:

```lua
vim.api.nvim_set_hl(0, "TabLineFill", { bg = "NONE", underline = true })
vim.api.nvim_set_hl(0, "TabLine", { bg = "NONE" })
vim.api.nvim_set_hl(0, "TabLineSel", { bg = "NONE" })
```
# References