# µlsp

LSP client for [micro-editor](https://github.com/zyedidia/micro). Note that this
is work in progress and currently **extremely buggy**, even the basic features
don't work properly yet. Use at your own risk.

[AndCake/micro-plugin-lsp](https://github.com/AndCake/micro-plugin-lsp)
is a slightly more complete LSP client for micro.


## Installation

Clone the repository to your micro plugins directory:

```
git clone https://github.com/Andriamanitra/mlsp ~/.config/micro/plug/mlsp
```

The plugin currently provides three commands:
* `lsp` starts a language server. If you run it without arguments the plugin
  tries to guess the right server by type of the currently open file, but you
  can also give it a command to run to launch any language server of your
  choice, for example `lsp "deno lsp"` (the quotes are required if the command
  takes arguments).
* `hover` shows hover information for the code under cursor
* `format` formats the buffer that is currently open

You can type the commands on micro command prompt or bind them to keys by
adding something like this to your `bindings.json`:
```json
{
    "F7": "command:lsp",
    "F8": "command:format",
    "Ctrl-j": "command:hover"    
}
```


## Supported features

* [x] get hover information
* [x] format document
* [ ] format selection
* [ ] everything else


## Known issues

* When using multiple language servers at the same time there is no good way
  to handle which one handles which request. So if you start both
  `pyright-language-server --stdio` and `ruff-lsp` and then ask for hover
  information you may get the result from either one (depending on which one
  is slower to respond) even though only Pyright responded with something useful.
