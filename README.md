# pynvim-hello-world
A simple set of instructions to write a greeting with the Python Neovim API.

This is a quick guide to writing a simple Python Plugin for Neovim. You will first need Neovim installed. I then installed pynvim from source following [their instructions](https://pynvim.readthedocs.io/en/latest/installation.html#install-from-source).

Write the following code to 
* `/home/yourname/.config/nvim/rplugin/python3/greet.py` 
* or another directory that ends `.../nvim/rplugin/python3/some_filename.py` where `...` is a folder on your runtime path. (Use `set runtimepath?` to see that.)

    import pynvim

    @pynvim.plugin
    class Greeting(object):

        def __init__(self, vim):
            self.vim = vim

        @pynvim.command('Greet', range='', nargs='*', sync=True)
        def command_handler(self, args, range):
            self.vim.command('echo "Hello, World!"')

After writing this file, run `:UpdateRemotePlugins` to tell Neovim to load the new file. You can then see "Hello, World!" echoed with the command `:Greet`
