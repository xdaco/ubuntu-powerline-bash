# ubuntu-powerline-bash

A script to quickly setup powerline **for bash** in **ubuntu**.

Powerline: https://github.com/powerline/powerline

## Use case

If you only want to quickly setup powerline for the bash prompt in ubuntu, this script saves you some manual steps.

## Run

    ./install.sh

Then logout and login again (if you open new terminals without logging-out first you will see some errors). Do not forget to fix the font issue if you are using it on WSL. Download and install the powerline fonts from https://github.com/xdaco/powerline-fonts .

## Add Git status
To add the git version control system status in the terminal install powerline-gitstatus and customize the shell color scheme and theme to display git status.

``pip install --user powerline-gitstatus``

Edit the following file for colorscheme. 

Now we will add our custom configuations. For that we need to have to edit the following files.

`1. ~/.local/lib/your_python_version/site- packages/powerline/config_files/config.json`
`2. ~/.local/lib/your_python_version/site- packages/powerline/config_files/colorschemes/default.json`
`3. ~/.local/lib/your_python_version/site- packages/powerline/config_files/themes/shell/__main__.json`

And We will create our own custome theme
`.~/.local/lib/your_python_version/site- packages/powerline/config_files/themes/shell/mine.json`

Here is my `mine.json` for theme. 

```
{
	"segments": {
		"left": [
			{
				"function": "powerline.segments.common.net.hostname",
				"priority": 10
			},
			{
				"function": "powerline.segments.common.env.user",
				"priority": 30
			},
			{
				"function": "powerline.segments.common.env.virtualenv",
				"priority": 50
			},
			{
				"function": "powerline.segments.shell.cwd",
				"priority": 10
			},
			{
				"function": "powerline_gitstatus.gitstatus",
				"priority": 40
			},
			{
				"function": "powerline.segments.shell.jobnum",
				"priority": 20
			}
		]
	}
}
	
```

Here is my `default.json` for colorschemes. 

```
{
  "groups": {
    "gitstatus":                 { "fg": "gray8",           "bg": "gray2", "attrs": [] },
    "gitstatus_branch":          { "fg": "gray8",           "bg": "gray2", "attrs": [] },
    "gitstatus_branch_clean":    { "fg": "green",           "bg": "gray2", "attrs": [] },
    "gitstatus_branch_dirty":    { "fg": "gray8",           "bg": "gray2", "attrs": [] },
    "gitstatus_branch_detached": { "fg": "mediumpurple",    "bg": "gray2", "attrs": [] },
    "gitstatus_tag":             { "fg": "darkcyan",        "bg": "gray2", "attrs": [] },
    "gitstatus_behind":          { "fg": "gray10",          "bg": "gray2", "attrs": [] },
    "gitstatus_ahead":           { "fg": "gray10",          "bg": "gray2", "attrs": [] },
    "gitstatus_staged":          { "fg": "green",           "bg": "gray2", "attrs": [] },
    "gitstatus_unmerged":        { "fg": "brightred",       "bg": "gray2", "attrs": [] },
    "gitstatus_changed":         { "fg": "mediumorange",    "bg": "gray2", "attrs": [] },
    "gitstatus_untracked":       { "fg": "brightestorange", "bg": "gray2", "attrs": [] },
    "gitstatus_stashed":         { "fg": "darkblue",        "bg": "gray2", "attrs": [] },
    "gitstatus:divider":         { "fg": "gray8",           "bg": "gray2", "attrs": [] }
  }
}

```
Here is my `config.json` for custom configuration.

```
{
	"common": {
		"term_truecolor": false
	},
	"ext": {
		"ipython": {
			"colorscheme": "default",
			"theme": "in",
			"local_themes": {
				"rewrite": "rewrite",
				"out": "out",
				"in2": "in2"
			}
		},
		"pdb": {
			"colorscheme": "default",
			"theme": "default"
		},
		"shell": {
			"colorscheme": "default",
			"theme": "mine",
			"local_themes": {
				"continuation": "continuation",
				"select": "select"
			}
		},
		"tmux": {
			"colorscheme": "default",
			"theme": "default"
		},
		"vim": {
			"colorscheme": "default",
			"theme": "default",
			"local_themes": {
				"__tabline__": "tabline",

				"cmdwin": "cmdwin",
				"help": "help",
				"quickfix": "quickfix",

				"powerline.matchers.vim.plugin.nerdtree.nerdtree": "plugin_nerdtree",
				"powerline.matchers.vim.plugin.commandt.commandt": "plugin_commandt",
				"powerline.matchers.vim.plugin.gundo.gundo": "plugin_gundo",
				"powerline.matchers.vim.plugin.gundo.gundo_preview": "plugin_gundo-preview"
			}
		},
		"wm": {
			"colorscheme": "default",
			"theme": "default"
		}
	}
}


```

Here is my `__main__.json` for custom theme to work.

```
{
  "segment_data": {
    "hostname": {
      "args": {
        "only_if_ssh": true
      }
    },
    "cwd": {
      "args": {
        "dir_limit_depth": 2
      }
    },
    "gitstatus": {
      "args": {
          "show_tag": true
      }
    }
  }
}


```

Now restart the powerline daemon 
```powerline-daemon --replace```


## Customization

Refer to https://powerline.readthedocs.org/en/latest/configuration.html#configuration-and-customization for how to customize the installation.

The configuration file will be in `./.local/lib/python2.7/site-packages/powerline/config_files/config.json`

![What you get](ubuntu-powerline-bash.png "What you get")



*I am not responsible if this script damages your computer, use it at your own risk and understand what it does first!*


