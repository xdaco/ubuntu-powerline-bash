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

`~/.local/lib/your_python_version/site-packages/powerline/config_files/colorschemes/shell/default.json`

Here is my default.json for color scheme. 

```
{
	"name": "Default color scheme for shell prompts",
	"groups": {
		"hostname": {
			"fg": "brightyellow",
			"bg": "mediumorange",
			"attrs": []
		},
		"environment": {
			"fg": "white",
			"bg": "darkestgreen",
			"attrs": []
		},
		"mode": {
			"fg": "darkestgreen",
			"bg": "brightgreen",
			"attrs": ["bold"]
		},
		"attached_clients": {
			"fg": "white",
			"bg": "darkestgreen",
			"attrs": []
		},

		"gitstatus": {
			"fg": "gray8",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_branch": {
			"fg": "gray8",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_branch_clean": {
			"fg": "green",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_branch_dirty": {
			"fg": "gray8",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_branch_detached": {
			"fg": "mediumpurple",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_tag": {
			"fg": "darkcyan",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_behind": {
			"fg": "gray10",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_ahead": {
			"fg": "gray10",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_staged": {
			"fg": "green",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_unmerged": {
			"fg": "brightred",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_changed": {
			"fg": "mediumorange",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_untracked": {
			"fg": "brightestorange",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus_stashed": {
			"fg": "darkblue",
			"bg": "gray2",
			"attrs": []
		},
		"gitstatus:divider": {
			"fg": "gray8",
			"bg": "gray2",
			"attrs": []
		}
	},
	"mode_translations": {
		"vicmd": {
			"groups": {
				"mode": {
					"fg": "darkestcyan",
					"bg": "white",
					"attrs": ["bold"]
				}
			}
		}
	}
}
```

Edit the following file for theme. 

`~/.local/lib/your_python_version/site-packages/powerline/config_files/themes/shell/default.json` 

Here is my default.json for theme. 

```
{
	"segments": {
		"left": [{
				"function": "powerline.segments.shell.mode"
			},
			{
				"function": "powerline.segments.common.net.hostname",
				"priority": 10
			},
			{
				"function": "powerline.segments.common.env.user",
				"priority": 30
			},
			{
				"function": "powerline.segments.shell.cwd",
				"priority": 10
			}, {
				"function": "powerline_gitstatus.gitstatus",
				"priority": 40
			}
		],
		"right": []
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


