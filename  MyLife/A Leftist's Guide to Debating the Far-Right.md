Date: 2025-12-27
Tags: {
#W 
}



==============================================================================
lazy:                                                                     2 ⚠️

lazy.nvim ~
- {lazy.nvim} version `11.17.5`
- ✅ OK {git} `version 2.39.5 (Apple Git-154)`
- ✅ OK no existing packages found by other package managers
- ✅ OK packer_compiled.lua not found

luarocks ~
- checking `luarocks` installation
- ✅ OK no plugins require `luarocks`, so you can ignore any warnings below
- ✅ OK {luarocks} `/opt/homebrew/bin/luarocks 3.12.2`
- ⚠️ WARNING `lua` version `5.1` needed, but found `Lua 5.4.8  Copyright (C) 1994-2025 Lua.org, PUC-Rio`
- ⚠️ WARNING {lua5.1} or {lua} or {lua-5.1} version `5.1` not installed

==============================================================================
lspconfig:                                                                  ✅

- Skipped. This healthcheck is redundant with `:checkhealth vim.lsp`.

==============================================================================
luasnip:                                                                  1 ⚠️

luasnip ~
- ⚠️ WARNING For Variable/Placeholder-transformations, luasnip requires
      the jsregexp library. See `:help |luasnip-lsp-snippets-transformations`| for advice
  

==============================================================================
null-ls:                                                                    ✅

- ✅ OK prettierd: the command "prettierd" is executable.

==============================================================================
nvim-treesitter:                                                          1 ⚠️

Installation ~
- ⚠️ WARNING `tree-sitter` executable not found (parser generator, only needed for :TSInstallFromGrammar, not required for :TSInstall)
- ✅ OK `node` found v22.17.1 (only needed for :TSInstallFromGrammar)
- ✅ OK `git` executable found.
- ✅ OK `cc` executable found. Selected from { vim.NIL, "cc", "gcc", "clang", "cl", "zig" }
  Version: Apple clang version 17.0.0 (clang-1700.0.13.5)
- ✅ OK Neovim was compiled with tree-sitter runtime ABI version 15 (required >=13). Parsers must be compatible with runtime ABI.

OS Info:
{
  machine = "arm64",
  release = "24.6.0",
  sysname = "Darwin",
  version = "Darwin Kernel Version 24.6.0: Mon Jul 14 11:28:30 PDT 2025; root:xnu-11417.140.69~1/RELEASE_ARM64_T6030"
} ~

Parser/Features         H L F I J
  - asm                 ✓ . . . ✓
  - c                   ✓ ✓ ✓ ✓ ✓
  - cpp                 ✓ ✓ ✓ ✓ ✓
  - go                  ✓ ✓ ✓ ✓ ✓
  - javascript          ✓ ✓ ✓ ✓ ✓
  - lua                 ✓ ✓ ✓ ✓ ✓
  - markdown            ✓ . ✓ ✓ ✓
  - markdown_inline     ✓ . . . ✓
  - query               ✓ ✓ ✓ ✓ ✓
  - rust                ✓ ✓ ✓ ✓ ✓
  - tsx                 ✓ ✓ ✓ ✓ ✓
  - typescript          ✓ ✓ ✓ ✓ ✓
  - vim                 ✓ ✓ ✓ . ✓
  - vimdoc              ✓ . . . ✓

  Legend: H[ighlight], L[ocals], F[olds], I[ndents], In[j]ections
         +) multiple parsers found, only one will be used
         x) errors found in the query, try to run :TSUpdate {lang} ~

==============================================================================
telescope:                                                                  ✅

Checking for required plugins ~
- ✅ OK plenary installed.

Checking external dependencies ~
- ✅ OK rg: found ripgrep 15.1.0
- ✅ OK fd: found fd 10.3.0

===== Installed extensions ===== ~

Telescope Extension: `terms` ~
- No healthcheck provided

Telescope Extension: `themes` ~
- No healthcheck provided

==============================================================================
vim.deprecated:                                                           2 ⚠️

 ~
- ⚠️ WARNING vim.lsp.get_active_clients() is deprecated. Feature will be removed in Nvim 0.12
  - ADVICE:
    - use vim.lsp.get_clients() instead.
    - stack traceback:
        /Users/ansgarseifert/.local/share/nvim/lazy/ui/lua/nvchad/signature.lua:99

 ~
- ⚠️ WARNING vim.validate is deprecated. Feature will be removed in Nvim 1.0
  - ADVICE:
    - use vim.validate(name, value, validator, optional_or_msg) instead.
    - stack traceback:
        /Users/ansgarseifert/.local/share/nvim/lazy/cmp-buffer/lua/cmp_buffer/source.lua:34
        /Users/ansgarseifert/.local/share/nvim/lazy/cmp-buffer/lua/cmp_buffer/source.lua:45
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/source.lua:239
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/source.lua:283
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/core.lua:308
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/core.lua:178
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/core.lua:170
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/init.lua:372
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/utils/autocmd.lua:53
        /Users/ansgarseifert/.local/share/nvim/lazy/nvim-cmp/lua/cmp/utils/autocmd.lua:14

==============================================================================
vim.health:                                                                 ✅

Configuration ~
- ✅ OK no issues found

Runtime ~
- ✅ OK $VIMRUNTIME: /opt/homebrew/Cellar/neovim/0.11.4/share/nvim/runtime

Performance ~
- ✅ OK Build type: Release

Remote Plugins ~
- ✅ OK Up to date

terminal ~
- key_backspace (kbs) terminfo entry: `key_backspace=\177`
- key_dc (kdch1) terminfo entry: `key_dc=\E[3~`
- $COLORTERM="truecolor"

External Tools ~
- ✅ OK ripgrep 15.1.0 (/opt/homebrew/bin/rg)

==============================================================================
vim.lsp:                                                                    ✅

- LSP log level : WARN
- Log path: /Users/ansgarseifert/.local/state/nvim/lsp.log
- Log size: 43884 KB

vim.lsp: Active Clients ~
- clangd (id: 1)
  - Version: Apple clangd version 17.0.0 (clang-1700.0.13.5) mac+xpc arm64-apple-darwin24.6.0
  - Root directory: ~/Desktop/Personal/lowLevel/C/Projects/snake_game
  - Command: { "clangd" }
  - Settings: vim.empty_dict()
  - Attached buffers: 10

vim.lsp: Enabled Configurations ~

vim.lsp: File Watcher ~
- file watching "(workspace/didChangeWatchedFiles)" disabled on all clients

vim.lsp: Position Encodings ~
- No buffers contain mixed position encodings

==============================================================================
vim.provider:                                                               ✅

Clipboard (optional) ~
- ✅ OK Clipboard tool found: pbcopy

Node.js provider (optional) ~
- Disabled (loaded_node_provider=0).

Perl provider (optional) ~
- Disabled (loaded_perl_provider=0).

Python 3 provider (optional) ~
- Disabled (loaded_python3_provider=0).

Ruby provider (optional) ~
- Disabled (loaded_ruby_provider=0).

==============================================================================
vim.treesitter:                                                             ✅

Treesitter features ~
- Treesitter ABI support: min 13, max 15
- WASM parser support: false

Treesitter parsers ~
- ✅ OK Parser: asm                       ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/asm.so
- ✅ OK Parser: c                         ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/c.so
- ✅ OK Parser: c                    (not loaded), path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/c.so
- ✅ OK Parser: cpp                       ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/cpp.so
- ✅ OK Parser: go                        ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/go.so
- ✅ OK Parser: javascript                ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/javascript.so
- ✅ OK Parser: lua                       ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/lua.so
- ✅ OK Parser: lua                  (not loaded), path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/lua.so
- ✅ OK Parser: markdown                  ABI: 15, path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/markdown.so
- ✅ OK Parser: markdown_inline           ABI: 15, path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/markdown_inline.so
- ✅ OK Parser: query                     ABI: 15, path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/query.so
- ✅ OK Parser: rust                      ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/rust.so
- ✅ OK Parser: tsx                       ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/tsx.so
- ✅ OK Parser: typescript                ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/typescript.so
- ✅ OK Parser: vim                       ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/vim.so
- ✅ OK Parser: vim                  (not loaded), path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/vim.so
- ✅ OK Parser: vimdoc                    ABI: 14, path: /Users/ansgarseifert/.local/share/nvim/lazy/nvim-treesitter/parser/vimdoc.so
- ✅ OK Parser: vimdoc               (not loaded), path: /opt/homebrew/Cellar/neovim/0.11.4/lib/nvim/parser/vimdoc.so


# A Leftist's Guide to Debating the Far-Right


What others do is a principle *controlling the pivot*:

Moving the goalposts a lot in conversations, ones a claim is knocked down, he treats to a weaker claim position. If you ever feel like you argue in circles with someone, thats why, because you let them pivot from one point to the next without actually closing any topic. 
This never ends.
What you can do, is pressing them, to admit when they're giving up ground. This forces the other to either, argue the point or give up the point.
Another good idea is rattling of facts, making the points super tangible and concrete, because you're not just arguing about pure principles. You are actually backing your point up with examples.

How can we, you and I, develop the ability to always have a counterargument on hand?
In shows like Sorrunded, the person knows his claims and can prepare, but we can do something else to prepare for political discussions, which we can do anytime and anywhere without having to prepared for a specific point.

*Keeping up what the arguments of the other side could be.*

Ofcourse we don‘t wanna watch hours of Fox News, to know what the other side is saying, but we can do something else.

Go to *Ground News*, a website, which filteres and analyzes thousands of articles every day and merges them together, and look at stories from *every* angle, so you can get a look at who is covering a story and how theyre covering it 



# References

https://www.youtube.com/watch?v=4qVdTfCgtCw