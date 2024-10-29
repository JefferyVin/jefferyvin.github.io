---
title: Personal Keybind Settings
date: '2024-09-23 05:07:30'
published: 'true'
tags:
- Stuff
---

This is what I use for assigning keybinds to my keyboard. Hope this helps other people out. There is a reason I picked Keyd instead of xmodmap because it allows me to use shift right command/alt hjkl to select text easier. Maybe there is a way but I just took the easy way out. 

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
[ids]

*

[main]

rightalt = layer(modi)
rightcontrol = rightalt

[modi:C]
h = left
k = up
j = down
l = right
n = backspace
m = delete
, = home
. = end
[ = (
] = )
u = +
i = -
o = _
p = *
; = =
```

### Windows
Powertoys (For my keychon k5)
```
{"remapKeys":{"inProcess":[{"originalKeys":"20","newRemapKeys":"162"},{"originalKeys":"165","newRemapKeys":"163"},{"originalKeys":"163","newRemapKeys":"165"}]},"remapKeysToText":{"inProcess":[]},"remapShortcuts":{"global":[{"originalKeys":"163;72","newRemapKeys":"37"},{"originalKeys":"163;73","newRemapKeys":"189"},{"originalKeys":"163;74","newRemapKeys":"40"},{"originalKeys":"163;75","newRemapKeys":"38"},{"originalKeys":"163;76","newRemapKeys":"39"},{"originalKeys":"163;77","newRemapKeys":"46"},{"originalKeys":"163;78","newRemapKeys":"8"},{"originalKeys":"163;79","operationType":0,"secondKeyOfChord":0,"newRemapKeys":"160;189"},{"originalKeys":"163;85","operationType":0,"secondKeyOfChord":0,"newRemapKeys":"160;187"},{"originalKeys":"163;186","newRemapKeys":"187"},{"originalKeys":"163;219","operationType":0,"secondKeyOfChord":0,"newRemapKeys":"160;57"},{"originalKeys":"163;221","operationType":0,"secondKeyOfChord":0,"newRemapKeys":"160;48"}],"appSpecific":[]},"remapShortcutsToText":{"global":[],"appSpecific":[]}}
```
