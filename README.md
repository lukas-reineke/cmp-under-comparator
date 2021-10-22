# cmp-under-comparator

A tiny function for [nvim-cmp](https://github.com/hrsh7th/nvim-cmp) to better
sort completion items that start with one or more underlines.

In most languages, especially Python, items that start with one or more
underlines should be at the end of the completion suggestion.

|                                                   Before                                                   |                                                   After                                                    |
| :--------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------: |
| ![](https://user-images.githubusercontent.com/12900252/138484425-93c14853-d45f-42e2-a5b8-8deaaa748330.png) | ![](https://user-images.githubusercontent.com/12900252/138484481-212b2478-c427-48b4-bc9f-0c0098be04b9.png) |

## Install

Use your favourite plugin manager to install.

#### Example with Packer

[wbthomason/packer.nvim](https://github.com/wbthomason/packer.nvim)

```lua
-- init.lua
require("packer").startup(
    function()
        use "lukas-reineke/cmp-under-comparator"
    end
)
```

#### Example with Plug

[junegunn/vim-plug](https://github.com/junegunn/vim-plug)

```vim
" init.vim
call plug#begin('~/.vim/plugged')
Plug 'lukas-reineke/cmp-under-comparator'
call plug#end()
```

## Setup

Add the `under` function to the list of comparators in the cmp setup function.

```lua
local cmp = require "cmp"
cmp.setup {
    -- ... rest of your setup ...

    sorting = {
        comparators = {
            cmp.config.compare.offset,
            cmp.config.compare.exact,
            cmp.config.compare.score,
            require "cmp-under-comparator".under,
            cmp.config.compare.kind,
            cmp.config.compare.sort_text,
            cmp.config.compare.length,
            cmp.config.compare.order,
        },
    },
}
```
