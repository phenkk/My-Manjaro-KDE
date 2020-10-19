# Capslock Delay Fix for Manjaro KDE
### 1. Export your keyboard configuration:
`xkbcomp -xkb $DISPLAY xkbmap`

### 2. Open and Edit the extracted xkbmap file:
`nano ~/xkbmap`

##### Locate the Caps Lock section which begins with key <CAPS>:
##### Example:
`key <CAPS> {         [       Caps_Lock ] };`

##### Replace with:
```
key <CAPS> {
    repeat=no,
    type[group1]="ALPHABETIC",
    symbols[group1]=[ Caps_Lock, Caps_Lock],
    actions[group1]=[ LockMods(modifiers=Lock), Private(type=3,data[0]=1,data[1]=3,data[2]=3)]
};
```
##### Save

### 3. Create script to run on startup:
`nano ~/.capslockfixer.sh`

##### Add this:
```
#!/bin/sh
xkbcomp -w 0 xkbmap $DISPLAY
```
##### Save

### 4. Open Settings > Startup and Shutdown > Autostart > add Script File you created before, leave other options unchange.
