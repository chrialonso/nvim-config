--Basic
vim.opt.number = true
vim.opt.relativenumber = true
vim.opt.wrap = false
vim.opt.tabstop = 4
vim.opt.shiftwidth = 4
vim.opt.expandtab = true
vim.opt.swapfile = false
vim.opt.signcolumn = "yes"
vim.opt.termguicolors = true
vim.opt.scrolloff = 8
vim.opt.updatetime = 250
vim.opt.cursorline = false
vim.opt.cursorcolumn = false
vim.opt.clipboard = "unnamedplus"
vim.opt.undofile = true
vim.opt.splitbelow = true
vim.opt.splitright = true  
vim.opt.confirm = true
vim.opt.splitkeep = "screen"

--Leader key!
vim.g.mapleader = " "

--Window border
vim.opt.winborder = "rounded"

-- Stay in visual mode when indenting
vim.keymap.set('v', '<', '<gv', {desc = 'Indent left'})
vim.keymap.set('v', '>', '>gv', {desc = 'Indent right'})

-- Easy navigation between splits
vim.keymap.set('n', '<C-h>', '<C-w>h')
vim.keymap.set('n', '<C-j>', '<C-w>j')
vim.keymap.set('n', '<C-k>', '<C-w>k')
vim.keymap.set('n', '<C-l>', '<C-w>l')

-- Quickly move between recently edited files
vim.keymap.set('n', '<leader><tab>', '<C-^>', {desc = 'Switch to last file'})

-- Highlight on yank
vim.api.nvim_create_autocmd('TextYankPost', {
    callback = function()
        vim.highlight.on_yank({ timeout = 200 })
    end,
})

-- Highlight current line in active window only
vim.api.nvim_create_autocmd({"WinEnter", "BufEnter"}, {command = "setlocal cursorline"})
vim.api.nvim_create_autocmd({"WinLeave"}, {command = "setlocal nocursorline"})

vim.pack.add({
		{src = "https://github.com/rose-pine/neovim"},
		{src = "https://github.com/stevearc/oil.nvim"},	
		{src = "https://github.com/echasnovski/mini.pick"},
		{src = "https://github.com/neovim/nvim-lspconfig"},
		{src = "https://github.com/Pocco81/auto-save.nvim"},
		{src = "https://github.com/altermo/ultimate-autopair.nvim"},
        {src = "https://github.com/hrsh7th/nvim-cmp"},
        {src = "https://github.com/hrsh7th/cmp-nvim-lsp"},
        {src = "https://github.com/folke/which-key.nvim"},
        {src = "https://github.com/nvim-mini/mini.icons"},
        {src = "https://github.com/hrsh7th/cmp-buffer"},
        {src = "https://github.com/hrsh7th/cmp-path"},
        {src = "https://github.com/tpope/vim-dadbod"},
        {src = "https://github.com/kristijanhusak/vim-dadbod-ui"},
        {src = "https://github.com/kristijanhusak/vim-dadbod-completion"},
		{src = "https://github.com/tpope/vim-fugitive"},
		{src = "https://github.com/lewis6991/gitsigns.nvim"},
		{src = "https://github.com/sindrets/diffview.nvim"},
		{src = "https://github.com/tpope/vim-rhubarb"}
})

--Mini.pick setup
require"mini.pick".setup()
vim.keymap.set('n', '<leader><leader>', function()
		require('mini.pick').builtin.buffers()
		end, {desc = 'Find buffers'})

vim.keymap.set('n', '<leader>ff', function()
    require('mini.pick').builtin.files({}, {
        source = { tool = 'find' }  -- or 'fd' or 'find'
    })
end, {desc = 'Find files'})

vim.keymap.set('n', '<leader>fg', function()
    require('mini.pick').builtin.grep_live()
end, {desc = 'Live grep'})

--Oil plugin setup
require "oil".setup({
    default_file_explorer = true,
    columns = {'icon'},
    view_options = {
        show_hidden = false,
    },
})

vim.keymap.set("n", "<leader>e", "<CMD>Oil<CR>", {desc = "Open parent directory"})

--which-key plugin setup
require "which-key".setup({
    plugins = {
        marks = true,
        registers = true,
        spelling = {enabled = true},
    },
})

--mini icons plugin
require "mini.icons".setup({})

--gitsigns plugin setup
require('gitsigns').setup({
  signs = {
    add          = { text = '┃' },
    change       = { text = '┃' },
    delete       = { text = '_' },
    topdelete    = { text = '‾' },
    changedelete = { text = '~' },
    untracked    = { text = '┆' },
  },
    signs_staged = {
    add          = { text = '┃' },
    change       = { text = '┃' },
    delete       = { text = '_' },
    topdelete    = { text = '‾' },
    changedelete = { text = '~' },
    untracked    = { text = '┆' },
  },
  signs_staged_enable = true,
  signcolumn = true,
  numhl      = false,
  linehl     = false,
  word_diff  = false,
  current_line_blame = true,
    preview_config = {
    style = 'minimal',
    relative = 'cursor',
    row = 0,
    col = 1
  },
})

--Gitsigns keymaps
local gs = require("gitsigns")
vim.keymap.set("n", "<leader>hs", gs.stage_hunk, {desc = "Stage hunk"})
vim.keymap.set("n", "<leader>hr", gs.reset_hunk, {desc = "Reset hunk"})
vim.keymap.set("n", "<leader>hp", gs.preview_hunk, {desc = "Preview hunk"})
vim.keymap.set("n", "<leader>hb", gs.blame_line, {desc = "Blame line"})
vim.keymap.set("n", "]h", gs.next_hunk, {desc = "Next hunk"})
vim.keymap.set("n", "[h", gs.prev_hunk, {desc = "Previous hunk"})

--Fugitive keymaps
vim.keymap.set("n", "<leader>gg", function()
  vim.cmd("Git")
  vim.cmd("resize 15")
end, {desc = "Git status (Fugitive)"})
vim.keymap.set("n", "<leader>gp", ":Git push<CR>")
vim.keymap.set("n", "<leader>gl", ":Git pull<CR>")

--Diffview keymaps
vim.keymap.set("n", "<leader>gd", ":DiffviewOpen<CR>")
vim.keymap.set("n", "<leader>gq", ":DiffviewClose<CR>")
vim.keymap.set("n", "<leader>gh", ":DiffviewFileHistory<CR>")

local lspconfig = require("lspconfig")

--Lua LSP config
lspconfig.lua_ls.setup({
		settings = {
				Lua = {
						runtime = {
								version = 'LuaJIT',
						},
						diagnostics = {
								globals = {'vim'},
						},
						workspace = {
								library = vim.api.nvim_get_runtime_file("", true),
						},
						telemetry = {
								enable = false,
						},
				},
		},
})

--Rust LSP config
lspconfig.rust_analyzer.setup({
		root_dir = lspconfig.util.root_pattern("Cargo.toml", ".git"),
		settings = {
				["rust-analyzer"] = {
						cargo = {
								allFeatures = true,
						},
						procMacro = {
								enable = true,
						},
				},
		},
})

--C setup
lspconfig.clangd.setup({
    root_dir = lspconfig.util.root_pattern(
        "compile_commands.json",
        "compile_flags.txt",
        ".clangd",
        ".git"
    ),
    cmd = {
        "clangd",
        "--clang-tidy",
        "--completion-style=detailed",
        "--function-arg-placeholders",
        "--fallback-style=llvm",
    },
})

--Python LSP config
lspconfig.pyright.setup({
    settings = {
        python = {
            analysis = {
                autoSearchPaths = true,
                useLibraryCodeForTypes = true,
                diagnosticMode = "workspace",
            },
        },
    },
})

--Use Esc for normal mode in terminal
vim.keymap.set('t', '<Esc>', '<C-\\><C-n>', {noremap = true})
vim.keymap.set('n', '<leader>t', ':15split | terminal<CR>', {noremap = true, silent = true})

--Diagnostics
vim.diagnostic.config({
		virtual_text = true,
		signs = true,
		underline = true,
		update_in_insert = true,
		severity_sort = true,
        float = {
            style = "minimal",
            border = "rounded",
            source = "always",
            header = "",
            prefix = "",
        },
})

vim.keymap.set('n', '[d', vim.diagnostic.goto_prev, {desc = 'Previous diagnostic'})
vim.keymap.set('n', ']d', vim.diagnostic.goto_next, {desc = 'Next diagnostic'})

vim.api.nvim_create_autocmd('LspAttach', {
    group = vim.api.nvim_create_augroup('UserLspConfig', {}),
    callback = function(ev)
        local opts = { buffer = ev.buf }
        vim.keymap.set('n', 'gd', vim.lsp.buf.definition, opts)
        vim.keymap.set('n', 'K', vim.lsp.buf.hover, opts)
        vim.keymap.set('n', 'gi', vim.lsp.buf.implementation, opts)
        vim.keymap.set('n', '<leader>rn', vim.lsp.buf.rename, opts)
        vim.keymap.set('n', '<leader>ca', vim.lsp.buf.code_action, opts)
        vim.keymap.set('n', 'gr', vim.lsp.buf.references, opts)
    end,
})

-- Delete buffers
vim.api.nvim_create_user_command('TermClean', function()
  for _, buf in ipairs(vim.api.nvim_list_bufs()) do
    if vim.bo[buf].buftype == 'terminal' then
      vim.api.nvim_buf_delete(buf, { force = true })
    end
  end
end, {})

--Diagnostic keymaps
vim.keymap.set('n','<leader>d', vim.diagnostic.open_float, {desc = "Show diagnostic"})

--Autopair plugin
require "ultimate-autopair".setup()

--Completion setup
local cmp = require('cmp')
cmp.setup({
    window = {
        completion = cmp.config.window.bordered(),
        documentation = cmp.config.window.bordered(),
    },
    mapping = cmp.mapping.preset.insert({
        ['<C-b>'] = cmp.mapping.scroll_docs(-4),
        ['<C-f>'] = cmp.mapping.scroll_docs(4),
        ['<C-Space>'] = cmp.mapping.complete(),
        ['<C-e>'] = cmp.mapping.abort(),
        ['<CR>'] = cmp.mapping.confirm({ select = true }),
        ['<Tab>'] = cmp.mapping(function(fallback)
            if cmp.visible() then
                cmp.select_next_item()
            else
                fallback()
            end
        end, { 'i', 's' }),
        ['<S-Tab>'] = cmp.mapping(function(fallback)
            if cmp.visible() then
                cmp.select_prev_item()
            else
                fallback()
            end
        end, { 'i', 's' }),
    }),
    sources = cmp.config.sources({
        { name = 'nvim_lsp' },    -- LSP completions (functions, methods, etc.)
    }, {
        { name = 'buffer' },      -- Words from current buffer
        { name = 'path' },        -- File paths
    }),
    formatting = {
        format = function(entry, vim_item)
            -- Show where the completion came from
            vim_item.menu = ({
                nvim_lsp = "[LSP]",
                buffer = "[Buf]",
                path = "[Path]",
            })[entry.source.name]
            return vim_item
        end,
    },
})

vim.opt.completeopt = {'menu', 'menuone', 'noselect'}
vim.opt.pumheight = 10

--Better search
vim.opt.ignorecase = true
vim.opt.smartcase = true
vim.opt.hlsearch = true
vim.opt.incsearch = true

vim.keymap.set('n', '<leader>hh', ':nohlsearch<CR>')

--Colorscheme
vim.cmd("colorscheme rose-pine")
