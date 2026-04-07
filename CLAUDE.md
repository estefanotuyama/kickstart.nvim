# Neovim Config (kickstart.nvim fork)

Personal Neovim configuration based on kickstart.nvim. Single-file core (`init.lua`) with modular plugin configs.

## Commands

- Lint Lua: `stylua --check .`
- Format Lua: `stylua .`
- Health check: open Neovim and run `:checkhealth`

## Architecture

- `init.lua` — Entry point. Contains all settings, keymaps, autocommands, and plugin specs (lazy.nvim).
- `lua/kickstart/plugins/` — Optional bundled plugin configs (debug, autopairs, neo-tree, gitsigns, lint). Loaded via `require 'kickstart.plugins.<name>'` in init.lua.
- `lua/custom/plugins/` — User plugin extensions (currently empty). Files here are NOT auto-imported; uncomment the `{ import = 'custom.plugins' }` line in init.lua to enable.

Plugin manager: **lazy.nvim** (auto-bootstrapped).
LSP servers managed by **Mason**: lua_ls, clangd, gopls, pyright, sqlls, ts_ls.
Formatter: **conform.nvim** (stylua for Lua, isort/black for Python). Format-on-save enabled except for C/C++/Python.
Completion: **blink.cmp** with super-tab preset. AI completion via **Codeium**.
Colorscheme: `github_dark_dimmed` (github-nvim-theme).

## Conventions

- Lua formatting: stylua with config in `.stylua.toml` (2-space indent, single quotes, no call parentheses, 160 col width).
- Leader key is `<Space>`. All custom keymaps use `<leader>` prefix.
- `vim.g.have_nerd_font = false` — do not assume Nerd Font icons are available.
- New plugins go in `lua/custom/plugins/` or directly in the lazy.setup table in init.lua. Kickstart plugin files under `lua/kickstart/plugins/` follow upstream structure.
