ZSH Hooks
=========

Usage
-----

```sh
# Define a new hook that can be added to
hooks-define-hook <hook_variable_name>

# Run all functions added to the hook
hooks-run-hook <hook_variable_name>

# adds function to hook
#
# Options:
#   -d    remove from hook
#   -D    remove with pattern
#
# Everything else accepted by add-zsh-hook works... because it's the same
hooks-add-hook [ops] <hook_variable_name> <function>
```

What??
------

That's right. `hooks-add-hook` is shamelessly taken from `add-zsh-hook`, and modified to be able to run on user defined hooks.

**Why is this important?**

Because ZSH has defined certain magic functions such as `zle-line-init` and `zle-keymap-select` that, if defined are run, but which can only have one definition.

**The answer:** define it to be a function that simply runs a hook.

So this plugin provides:

- `zle_line_init_hook` - these functions run on line init!
- `zle_keymap_select_hook` - these functions run when you switch your keymap!
- similar to the previous two, all of the other special functions documented [here](http://zsh.sourceforge.net/Doc/Release/Zsh-Line-Editor.html#Special-Widgets), except the history one, due to a bug.
- `$ZSH_CUR_KEYMAP` - this variable is set on line init/keymap change!

Why?
----

Plugin authors might want to use this functionality, but if they do it will conflict with what end-users do. This can solve that problem. Basically this is made to be a dependency for other plugins.

Install
-------

### [Zplugin](https://github.com/psprint/zplugin)

```
zplugin load RobertAudi/zsh-hooks
```

### [zplug](https://github.com/zplug/zplug)

```
zplug "RobertAudi/zsh-hooks"
```

### [zgen](https://github.com/tarjoilija/zgen)

```
zgen load RobertAudi/zsh-hooks
```

### [antigen](https://github.com/zsh-users/antigen)

```
antigen bundle RobertAudi/zsh-hooks
```
