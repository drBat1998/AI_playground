``` lua
{
  "jiaoshijie/undotree",
  dependencies = "nvim-lua/plenary.nvim",
  config = true,
  keys = { -- load the plugin only when using it's keybinding:
    { "<leader>u", "<cmd>lua require('undotree').toggle()<cr>" },
  },
}
```

``` lua
local undotree = require('undotree')

undotree.setup({
  float_diff = true,  -- using float window previews diff, set this `true` will disable layout option
  layout = "left_bottom", -- "left_bottom", "left_left_bottom"
  position = "left", -- "right", "bottom"
  ignore_filetype = { 'undotree', 'undotreeDiff', 'qf', 'TelescopePrompt', 'spectre_panel', 'tsplayground' },
  window = {
    winblend = 30,
  },
  keymaps = {
    ['j'] = "move_next",
    ['k'] = "move_prev",
    ['gj'] = "move2parent",
    ['J'] = "move_change_next",
    ['K'] = "move_change_prev",
    ['<cr>'] = "action_enter",
    ['p'] = "enter_diffbuf",
    ['q'] = "quit",
  },
})
```

keymaps
``` lua
vim.keymap.set('n', '<leader>u', require('undotree').toggle, { noremap = true, silent = true })

-- or
vim.keymap.set('n', '<leader>uo', require('undotree').open, { noremap = true, silent = true })
vim.keymap.set('n', '<leader>uc', require('undotree').close, { noremap = true, silent = true })
```

Some Mappings
Mappings	Action
j	jump to next undo node
gj	jump to the parent node of the node under the cursor
k	jump to prev undo node
J	jump to next undo node and undo to this state
K	jump to prev undo node and undo to this state
q	quit undotree
p	jump into the undotree diff window
Enter	undo to this state