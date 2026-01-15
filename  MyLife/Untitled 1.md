local base = require("plugins.configs.lspconfig")
local on_attach = base.on_attach
local capabilities = base.capabilities

local lspconfig = require("lspconfig")
local util = require("lspconfig.util")

-- damit tailwind nicht crashout geht, und alle sachen aus dem root lädt
-- um die tailwind config zu finden

lspconfig.tailwindcss.setup({
  on_attach = on_attach,
  capabilities = capabilities,
  root_dir = util.root_pattern(
    "tailwind.config.js",
    "tailwind.config.cjs",
    "tailwind.config.mjs",
    "postcss.config.js",
    "package.json"
  ),
})

-- java
vim.api.nvim_create_autocmd("FileType", {
  pattern = "java",
  callback = function()
    require("custom.configs.jdtls")
  end,
})
-- others

local servers = { "tsserver", "eslint", "clangd", "gopls" }

for _, server in ipairs(servers) do
  lspconfig[server].setup({
    on_attach = on_attach,
    capabilities = capabilities,
  })
end
