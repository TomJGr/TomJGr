- 👋 Hi, I’m @TomJGr
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
TomJGr/TomJGr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
-- This file can be loaded by calling `lua require('plugins')` from your init.vim

require('packer').add{
  -- Packer can manage itself
  'wbthomason/packer.nvim';

  -- Simple plugins can be specified as strings
  '9mm/vim-closer';

  -- Lazy loading:
  -- Load on specific commands
  {'tpope/vim-dispatch', cmd = {'Dispatch', 'Make', 'Focus', 'Start'}};

  -- Load on specific keymap
  {'tpope/vim-commentary', keys = 'gc'},

  -- Load on a combination of conditions: specific filetypes or commands
  -- Also run code after load (see the "config" key)
  { 'w0rp/ale',
    ft = {'sh', 'zsh', 'bash', 'c', 'cpp', 'cmake', 'html', 'markdown', 'racket', 'vim', 'tex'},
    cmd = 'ALEEnable',
    config = 'vim.cmd[[ALEEnable]]'
  };

  -- Local plugins can be included
  '~/projects/personal/hover.nvim';

  -- Plugins can have post-install/update hooks
  {'iamcco/markdown-preview.nvim', run = 'cd app && yarn install', cmd = 'MarkdownPreview'};

  -- Post-install/update hook with neovim command
  -- Install plugin as a 'start' plugin
  { 'nvim-treesitter/nvim-treesitter', run = ':TSUpdate', start = true };

  -- Post-install/update hook with call of vimscript function with argument
  { 'glacambre/firenvim', run = function()
    vim.fn['firenvim#install'](0)
  end };

  -- Use specific branch, dependency and run lua file after load
  { 'glepnir/galaxyline.nvim',
    branch = 'main',
    requires = {'kyazdani42/nvim-web-devicons'},
    config = function()
      require'statusline'
    end
  };

  -- Run config *before* the plugin is loaded
  {'whatyouhide/vim-lengthmatters', config_pre = function()
    vim.g.lengthmatters_highlight_one_column = 1
    vim.g.lengthmatters_excluded = {'packer'}
  end},
}
