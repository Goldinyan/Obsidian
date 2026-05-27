To visualize a **JPEG image** directly in the **Kitty terminal**, you can use the built-in **image display protocol** that Kitty supports. This allows you to render images directly in the terminal without needing an external image viewer.

---

### **Steps to Display a JPEG in Kitty Terminal**
1. **Ensure Kitty Supports Image Display**:
   - Kitty has built-in support for displaying images using the `kitty +kitten icat` command. This is part of Kitty's "kittens" (small utilities bundled with Kitty).

2. **Use the `icat` Kitten**:
   - The `icat` kitten is designed to display images in the terminal. You can use it to render a JPEG image.

3. **Command to Display a JPEG**:
   Run the following command in your terminal:
   ```bash
   kitty +kitten icat /path/to/your/image.jpg
   ```
   Replace `/path/to/your/image.jpg` with the actual path to your JPEG file.

---

### **Example**
If your image is named `example.jpg` and is in your current directory, run:
```bash
kitty +kitten icat example.jpg
```

---

### **Additional Options**
1. **Resize the Image**:
   You can resize the image to fit the terminal window using the `--scale-up` or `--scale-down` flags:
   ```bash
   kitty +kitten icat --scale-up example.jpg
   ```

2. **Display Image in a Specific Position**:
   Use the `--place` flag to specify the position and size of the image:
   ```bash
   kitty +kitten icat --place="100x50@100x20" example.jpg
   ```
   - `100x50` sets the width and height.
   - `100x20` sets the position (x,y).

3. **Display Image in the Background**:
   If you want to display the image in the background (e.g., for a wallpaper effect), you can use:
   ```bash
   kitty +kitten icat --stdin=no --place="100%x100%@0x0" example.jpg < /dev/null &
   ```
   - This renders the image in the background and continues using the terminal.

---

### **Notes**
- **Kitty Must Be Running**: The image will only display if Kitty is already running. If you're using another terminal, you won't see the image.
- **Supported Formats**: Kitty supports JPEG, PNG, GIF, and other common image formats.
- **Performance**: Large images may take a moment to render, especially if your terminal is not optimized for image display.

---

### **Alternative: Use `viu` for Terminal Image Display**
If you prefer a more interactive experience, you can use the `viu` tool, which is designed to display images in the terminal:
1. Install `viu`:
   ```bash
   cargo install viu
   ```
   (Requires [Rust](https://www.rust-lang.org/) to be installed.)

2. Display the image:
   ```bash
   viu example.jpg
   ```

---
### **Summary**
| Method             | Command                                                  | Description                                             |
| ------------------ | -------------------------------------------------------- | ------------------------------------------------------- |
| **Kitty `icat`**   | `kitty +kitten icat /path/to/image.jpg`                  | Display image directly in Kitty terminal.               |
| **Resize Image**   | `kitty +kitten icat --scale-up example.jpg`              | Scale the image to fit the terminal.                    |
| **Position Image** | `kitty +kitten icat --place="100x50@100x20" example.jpg` | Set position and size of the image.                     |
| **`viu` Tool**     | `viu example.jpg`                                        | Alternative tool for displaying images in the terminal. |





kitten themes -> for themes
kitty + list-fonts -> fonts einstellen etc
ctrl + c -> list all for cd (win + c on this kb)

## **General**
- `cmd+c` → copy_to_clipboard  
- `cmd+v` → paste_from_clipboard  
- `cmd+q` → quit  
- `cmd+m` → minimize_macos_window  
- `cmd+h` → hide_macos_app  
- `cmd+,` → edit_config_file  
- `ctrl+cmd+,` → load_config_file  
- `cmd+=` → change_font_size +2  
- `cmd+-` → change_font_size -2  
- `cmd+0` → reset font size  
- `cmd+shift+ctrl+e` → unicode_input  

---


## **Window Management**
- `cmd+n` → new_os_window  
- `ctrl+shift+enter` → split window (auto)  
- `cmd+w` → close_window  
- `ctrl+shift+o` → close_other_windows_in_tab  
- `ctrl+shift+-` → hsplit  
- `ctrl+shift+\` → vsplit  
- `ctrl+shift+k` → focus window up  
- `ctrl+shift+j` → focus window down  
- `ctrl+shift+h` → focus window left  
- `ctrl+shift+l` → focus window right  
- `ctrl+shift+p` → nth_window -1  
- `ctrl+shift+r` → start_resizing_window  
- `ctrl+shift+0` → reset_window_sizes  
- `ctrl+9` → focus_visible_window  
- `ctrl+0` → swap_with_window  

---

## **Tabs**
- `cmd+t` → new tab (cwd=current)  
- `cmd+shift+t` → new_tab  
- `ctrl+shift+w` → close_tab  
- `ctrl+shift+]` → next_tab  
- `ctrl+shift+[` → previous_tab  
- `ctrl+shift+,` → move_tab_backward  
- `ctrl+shift+.` → move_tab_forward  
- `ctrl+shift+n` → set_tab_title  
- `cmd+1` → goto_tab 1  
- `cmd+2` → goto_tab 2  
- `cmd+3` → goto_tab 3  
- `cmd+4` → goto_tab 4  
- `cmd+5` → goto_tab 5  
- `cmd+6` → goto_tab 6  
- `cmd+7` → goto_tab 7  
- `cmd+8` → goto_tab 8  
- `cmd+9` → goto_tab 9  

---

## **Kitten Hints**
- `ctrl+shift+u` → open_url_with_hints  
- `ctrl+shift+/` → hints (path mode)  

---

## **Misc / Raw Key Sends**
- `shift+enter` → send `\x1b[13;2u`  
- `ctrl+enter` → send `\x1b[13;5u`  
- `ctrl+1` → send `\x1b[27;5;49~`  
- `ctrl+2` → send `\x1b[27;5;50~`  
- `ctrl+3` → send `\x1b[27;5;51~`  
- `ctrl+4` → send `\x1b[27;5;52~`  
- `ctrl+5` → send `\x1b[27;5;53~`  
- `ctrl+6` → send `\x1b[27;5;54~`  
- `ctrl+7` → send `\x1b[27;5;55~`  
- `ctrl+8` → send `\x1b[27;5;56~`  
- `ctrl+9` → send `\x1b[27;5;57~`  
- `ctrl+0` → send `\x1b[27;5;58~`  
- `ctrl+/` → send `\x1f`  
