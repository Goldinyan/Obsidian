#!/usr/bin/env sh

# JankyBorders - Clean Dark/White Look (Sharp Edges)
killall borders 2>/dev/null
borders active_color=0xfff2f2f2 inactive_color=0xff333333 width=5.0 flash_duration=0.2 hidpi=on style=square &

# Global Layout Rules
yabai -m config layout bsp
yabai -m config window_placement second-child

# Padding Adjustments
yabai -m config top_padding 16
yabai -m config bottom_padding 16
yabai -m config left_padding 16
yabai -m config right_padding 16
yabai -m config window_gap 16


# Corner Flattening Overrides
yabai -m config window_opacity off
yabai -m config window_shadow off
yabai -m config window_border off  # Let JankyBorders draw the line so native curves don't bleed out

# Mouse Settings
yabai -m config mouse_follows_focus on
yabai -m config mouse_modifier alt
yabai -m config mouse_action1 move
yabai -m config mouse_action2 resize
yabai -m mouse_drop_action swap


# Modifier-Taste definieren (fn, alt, cmd oder ctrl)
yabai -m config mouse_modifier fn
# Linksklick + Ziehen verschiebt das Fenster (wenn es floatet)
yabai -m config mouse_action move
# Rechtsklick + Ziehen verändert die Fenstergröße
yabai -m config mouse_drop_action resize

# Force Zen Browser's window container to strip sub-layer decorations
yabai -m rule --add app="^Zen Browser$" sub-layer=normal manage=on
# Disanle specific apps
#
yabai -m rule --add app="^qutebrowser$" manage=on
yabai -m rule --add app="^Obsidian$" manage=on


yabai -m rule --add app="^Obsidian$" manage=on window_shadow=off

yabai -m rule --add app="^Karabiner-Elements$" manage=off
yabai -m rule --add app="^Terminal$" manage=off
