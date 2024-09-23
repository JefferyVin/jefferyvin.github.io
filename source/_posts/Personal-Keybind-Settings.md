---
title: Personal Keybind Settings
date: '2024-09-23 05:07:30'
published: 'true'
tags:
- Stuff
---

### Mac OS
Karabiner-Elements
```
{
    "description": "Change right_command+hjkl to arrow keys",
    "manipulators": [
        {
            "from": {
                "key_code": "h",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "left_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "j",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "down_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "k",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "up_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "l",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "right_arrow" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "semicolon",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "equal_sign" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "n",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "delete_or_backspace" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "m",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "delete_forward" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "comma",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "home" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "period",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "end" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "u",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [
                {
                    "key_code": "equal_sign",
                    "modifiers": "shift"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "i",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [{ "key_code": "hyphen" }],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "o",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [
                {
                    "key_code": "hyphen",
                    "modifiers": "shift"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "p",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [
                {
                    "key_code": "8",
                    "modifiers": "shift"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "open_bracket",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [
                {
                    "key_code": "9",
                    "modifiers": "shift"
                }
            ],
            "type": "basic"
        },
        {
            "from": {
                "key_code": "close_bracket",
                "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                }
            },
            "to": [
                {
                    "key_code": "0",
                    "modifiers": "shift"
                }
            ],
            "type": "basic"
        }
    ]
}
```


### Ubuntu
Keyd
```
will update once I get on PC
```


### Windows
Powertoys
```
will update once I get on PC
```

This is what I use for assigning keybinds to my keyboard. Hope this helps other people out. There is a reason I picked Keyd instead of xmodmap because it allows me to use shift right command/alt hjkl to select text easier. Maybe there is a way but I just took the easy way out. 

![](Construction.png)