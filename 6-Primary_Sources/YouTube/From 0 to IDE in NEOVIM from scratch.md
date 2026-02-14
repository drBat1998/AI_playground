Title: From 0 to IDE in NEOVIM from scratch
Author: [[typecraft]]
Tags: #programming #youtube 

[[neovim]]

# Notes
# 1
```shell
nvim ~/.config/nvim/init.lua
```

```shell

vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
vim.g.mapleader= " "

local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not (vim.uv or vim.loop).fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

local opts = {}
local plugins = {
	{"folke/tokyonight.nvim",
	name = "tokyonight",
  lazy = false,
  priority = 1000,
  opts = {}}, 
	{
		'nvim-telescope/telescope.nvim', tag = '0.1.6', 
		dependencies = { 'nvim-lua/plenary.nvim' }
    }, {"nvim-treesitter/nvim-treesitter", build= ":TSUpdate"}

}

require("lazy").setup(plugins, opts)

local builtin = require('telescope.builtin')
vim.keymap.set('n', '<C-p>', builtin.find_files, {})
vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})

local config = require("nvim-treesitter.configs")
config.setup({
  ensure_installed = {"r", "python", "markdown", "csv","powershell"},
  highlight = { enable = true },
  indent = { enable = true }
})

require("tokyonight").setup()
vim.cmd.colorscheme "tokyonight"

```

# 2
create dir  in nvim name it `lua` there create dir `plugins` where create separet `.lua` files for each plugins. In `init.lua`.
in `init.lua`  change from 
```lua
require("lazy").setup(plugins, opts)
```
to 
```lua
require("lazy").setup("plugins")
```

In each plugins write in this way
```lua
return {
	"nvim-neo-tree/neo-tree.nvim",
  branch = "v3.x",
  dependencies = {
    "nvim-lua/plenary.nvim",
    "nvim-tree/nvim-web-devicons", -- not strictly required, but recommended
    "MunifTanjim/nui.nvim",
    -- {"3rd/image.nvim", opts = {}}, -- Optional image support in preview window: See `# Preview Mode` for more information
  },
	lazy = false, -- neo-tree will lazily load itself
  ---@module "neo-tree"
  ---@type neotree.Config?
  opts = {
    -- fill any relevant options here
}, 
	config = function()
	
	vim.keymap.set('n', '<C-n>', ':Neotree filesystem reveal left<CR>', {})
	
	end


}
```

## Autocomplete and Snippets in Neovim | FREE COURSE // EP 5


# Links
https://youtu.be/zHTeCSVAFNY?si=sFOQh_3W2-NF1Xyb
https://typecraft.dev/neovim-for-newbs/setting-up-lua
https://youtu.be/4zyZ3sw_ulc?si=odAu3lsoEPwwHhHF