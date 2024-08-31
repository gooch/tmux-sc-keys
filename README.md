# SC keys: a tmux window switching script

Camera hotkeys in `tmux`. You can set specific windows as "camera" positions
and quickly switch between them using simple commands.

## Usage

The script provides two main operations:

1. **Set Camera Position**: Record the current tmux window index and assign it
   to a specific camera hotkey.
2. **Switch Camera**: Jump to the window assigned to a particular camera hotkey.

### Commands

```bash
tmux_camera CMD INDEX
```

- `CMD` can be:
  - `set`: Assign the current tmux window to camera position `INDEX`.
  - `switch`: Switch to the tmux window assigned to camera position `INDEX`.

### Examples

1. **Set Camera Position**
   - To assign the current window as camera position 1:
     ```bash
     tmux_camera set 1
     ```

2. **Switch Camera**
   - To switch to the window assigned to camera position 1:
     ```bash
     tmux_camera switch 1
     ```

### Special Cases

- If a camera position is set to a window that no longer exists, the script
will remove the old camera position.
- When switching, if no window is set for a camera position, you'll get a
message like "Camera X is not set."

### File Storage

The camera positions are stored as files in the following location:
```
${HOME}/.config/tmux/CAMERA_INDEX_${index}
```

Each file contains the window index for the corresponding camera.

## tmux key binds

Bind your prefered hotkeys in .tmux.conf.

```
bind -n C-F1 run 'tmux_camera set 1'
bind -n C-F2 run 'tmux_camera set 2'
bind -n C-F3 run 'tmux_camera set 3'
bind -n C-F4 run 'tmux_camera set 4'
bind -n F1 run 'tmux_camera switch 1'
bind -n F2 run 'tmux_camera switch 2'
bind -n F3 run 'tmux_camera switch 3'
bind -n F4 run 'tmux_camera switch 4'
```
