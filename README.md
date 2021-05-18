[`diagnostic-languageserver`](https://github.com/iamcco/diagnostic-languageserver)
configuration for Neovim's language server client.

```lua
local lspconfig = require("lspconfig")
local diagnosticls = require("diagnosticls")

lspconfig.diagnosticls.setup({
  filetypes = {
    "haskell",
    unpack(diagnosticls.filetypes),
  },
  init_options = {
    linters = vim.tbl_deep_extend("force", diagnosticls.linters, {
      hlint = {
        command = "hlint",
        -- ...
      },
    }),
    formatters = diagnosticls.formatters,
    filetypes = {
      haskell = "hlint",
      lua = { "luacheck", "selene" },
      markdown = { "markdownlint" },
      python = { "flake8", "mypy" },
      scss = "stylelint",
      sh = "shellcheck",
      vim = "vint",
      yaml = "yamllint",
    },
    formatFiletypes = {
      fish = "fish_indent",
      javascript = "prettier",
      javascriptreact = "prettier",
      json = "prettier",
      lua = { "lua-format", "stylua" },
      python = { "isort", "black" },
      sh = "shfmt",
      sql = "pg_format",
      typescript = "prettier",
      typescriptreact = "prettier",
    },
  },
})
```
