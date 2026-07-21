---
id: yabai - Start guide
aliases:
Topic: Explains how to run and start a yabai service.
Related:
Tags:
  - w
Date: 2026-05-03T19:13:00
Updated:
Source:
---
# yabai - Start guide

### Option 1: The "Permanent" Way (Recommended)

Since you've already fixed the permissions and the plist exists, you should use the built-in service command. This ensures it **starts automatically when you log in**.

Bash

```
yabai --start-service
```

_If it's already running and you want to refresh it after changing your config:_

Bash

```
yabai --restart-service
```

---

### Option 2: The "Manual/Debug" Way

If you ever feel like things aren't working and you want to see **why** (error messages, etc.), you can run it directly in your terminal:

Bash

```
yabai
```

_Note: This will "hang" your terminal window while it runs. To stop it, press `Ctrl+C`._

---

### Pro-Tips for 2026 macOS "Tahoe"

1. **The "Fix-it" Alias:** Since the lock-file issue might happen again if your Mac loses power or crashes, add this to your `.zshrc` or `.bashrc`:
    
    Bash
    
    ```
    alias fix-yabai="sudo pkill -9 yabai; rm /tmp/yabai_$USER.lock; yabai --start-service"
    ```
    
    Next time it acts up, just type `fix-yabai`.
    
2. **Hotkeys:** You mentioned it's tiling perfectly, but you'll eventually want to move windows with your keyboard. Make sure you install and start **skhd**:
    
    Bash
    
    ```
    brew services start skhd
    ```
    
3. **Scripting Addition:** If you find that space-switching is a bit laggy, remember to run the scripting addition command (requires that SIP adjustment we discussed earlier):
    
    Bash
    
    ```
    sudo yabai --load-sa
    ```
    
