# 📁 Project Structure

```bash
.
├── config
├── README.md
├── structure.md
├── style.css


```

> /home/sj/.config/waybar/config

```config
// -*- mode: json -*-

{
	"layer": "bottom",
	"position": "bottom",

	"modules-left": [
		"hyprland/workspaces",
		"hyprland/window",
		"custom/right-arrow-dark",
    "custom/timer",
    "custom/kanata-mode",
    "custom/age",
    "custom/smt"
	],
	"modules-center": [
		"custom/left-arrow-dark",
		"clock#1",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"clock#2",
		"custom/right-arrow-dark",
		"custom/right-arrow-light",
		"clock#3",
		"custom/right-arrow-dark"
	],
	"modules-right": [
		"custom/left-arrow-dark",
		"pulseaudio",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"memory",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"cpu",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"battery",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"disk",
		"custom/left-arrow-light",
		"custom/left-arrow-dark",
		"tray"
	],

	"custom/left-arrow-dark": {
		"format": "",
		"tooltip": false
	},
	"custom/left-arrow-light": {
		"format": "",
		"tooltip": false
	},
	"custom/right-arrow-dark": {
		"format": "",
		"tooltip": false
	},
  "custom/timer": {
        "format": "{} ⏳",  // Shows the time with a timer icon (customize or remove icon)
        "exec": "~/.config/hypr/shellscript/waybar/waybar-timer.sh",
        "interval": 1,  // Update every second for smooth countdown
        "tooltip": false  // Optional: no hover info
    },

    "custom/kanata-mode": {
    "format": "{}",
    "exec": "cat /tmp/kanata_mode 2>/dev/null || echo NORM",
    "interval": 1,
    "tooltip": false
},

	"custom/age": {
		"format": "{}",
		"return-type": "json",
		"exec": "~/.config/hypr/shellscript/waybar/duration_tracker.py age",
		"interval": 60,
		"tooltip": true
	},

	"custom/smt": {
		"format": "{}",
		"return-type": "json",
		"exec": "~/.config/hypr/shellscript/waybar/duration_tracker.py smt",
		"interval": 60,
		"tooltip": true
	},

	"custom/right-arrow-light": {
		"format": "",
		"tooltip": false
	},

	"hyprland/workspaces": {
		"disable-scroll": false,
		"all-outputs": true,
		"format": "{icon}",
		"format-icons": {
			"default": "",
			"active": "",
			"urgent": ""
		},
		"on-click": "activate",
		"on-scroll-up": "hyprctl dispatch workspace e+1",
		"on-scroll-down": "hyprctl dispatch workspace e-1"
	},

	"hyprland/window": {
		"format": "{}",
		"format-alt": "{}",
		"separator": false,
		"max-length": 30,
		"rewrite": {
			"(.*) - Mozilla Firefox": "🌐 $1",
			"(.*) - Google Chrome": "🌐 $1",
			"Alacritty": "💻 Terminal",
			"kitty": "💻 Terminal",
			"Thunar": "📁 Files",
			"nautilus": "📁 Files",
			"Code": "⚡ Code",
			"nvim": "✏️ Neovim",
			"Neovim": "✏️ Neovim"
		},
		"tooltip": false
	},

	"clock#1": {
		"format": "{:%a}",
		"tooltip": false
	},
	"clock#2": {
		"interval": 1,
		"format": "{:%I:%M:%S}",
		"tooltip": false
	},
	"clock#3": {
		"format": "{:%d-%m-%y}",
		"tooltip": false
	},

	"pulseaudio": {
		"format": "{icon} {volume:2}%",
		"format-bluetooth": "{icon}  {volume}%",
		"format-muted": "MUTE",
		"format-icons": {
			"headphones": "",
			"default": [
				"",
				""
			]
		},
		"scroll-step": 5,
		"on-click": "pamixer -t",
		"on-click-right": "pavucontrol"
	},
	"memory": {
		"interval": 5,
		"format": "Mem {}%",
		"tooltip": true,
		"on-click": "alacritty -e htop"
	},
	"cpu": {
		"interval": 5,
		"format": "CPU {usage:2}%",
		"tooltip": true,
		"on-click": "alacritty -e htop"
	},
	"battery": {
		"states": {
			"good": 95,
			"warning": 30,
			"critical": 15
		},
		"format": "{icon} {capacity}%",
		"format-charging": " {capacity}%",
		"format-plugged": " {capacity}%",
		"format-icons": [
			"",
			"",
			"",
			"",
			""
		],
		"tooltip": true
	},
	"disk": {
		"interval": 5,
		"format": "Disk {percentage_used:2}%",
		"path": "/",
		"tooltip": true,
		"on-click": "thunar"
	},
	"tray": {
		"icon-size": 20,
		"spacing": 8
	}
}
```

> /home/sj/.config/waybar/style.css

```css
* {
  font-size: 20px;
  font-family: monospace;
}

window#waybar {
  background: #292b2e;
  color: #fdf6e3;
}

#custom-right-arrow-dark,
#custom-left-arrow-dark {
  color: #1a1a1a;
}
#custom-right-arrow-light,
#custom-left-arrow-light {
  color: #292b2e;
  background: #1a1a1a;
}

#custom-timer {
  background-color: #f82a36;
  color: #f8f8f2;
  padding: 0 10px;
  border-radius: 5px;
}

#custom-kanata-mode {
  background-color: #6c71c4;
  color: #f8f8f2;
  padding: 0 10px;
  border-radius: 5px;
  font-weight: bold;
}

#custom-age {
  background-color: #2aa198;
  color: #f8f8f2;
  padding: 0 10px;
  border-radius: 5px;
  font-weight: bold;
  margin-left: 5px;
}

#custom-smt {
  background-color: #859900;
  color: #f8f8f2;
  padding: 0 10px;
  border-radius: 5px;
  font-weight: bold;
  margin-left: 5px;
}

#workspaces,
#clock.1,
#clock.2,
#clock.3,
#pulseaudio,
#memory,
#cpu,
#battery,
#disk,
#tray {
  background: #1a1a1a;
}

#workspaces button {
  padding: 0 2px;
  color: #d3abe3;
}
#workspaces button.focused {
  color: #268bd2;
}
#workspaces button:hover {
  box-shadow: inherit;
  text-shadow: inherit;
}
#workspaces button:hover {
  background: #1a1a1a;
  border: #1a1a1a;
  padding: 0 3px;
}

#pulseaudio {
  color: #268bd2;
}
#memory {
  color: #2aa198;
}
#cpu {
  color: #6c71c4;
}
#battery {
  color: #859900;
}
#disk {
  color: #b58900;
}

#clock,
#pulseaudio,
#memory,
#cpu,
#battery,
#disk {
  padding: 0 10px;
}
```
