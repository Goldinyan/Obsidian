# Untitle#!/usr/bin/env sh

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


# draw border on focus window 
# Schaltet die Rahmen generell ein
yabai -m config window_border on

# Die Dicke des Rahmens in Pixeln
yabai -m config window_border_width 3

# Farbe für das AKTIVE Fenster (z.B. ein helleres Grau/Weiß oder dein Koda-Muted-Ton)
yabai -m config active_window_border_color 0xffb0b0b0

# Farbe für alle INAKTIVEN Fenster (sollte dunkel sein, damit es nicht ablenkt)
yabai -m config normal_window_border_color 0xff272727

# mouse settings

yabai -m config mouse_follows_focus on

yabai -m config mouse_modifier alt
yabai -m config mouse_action1 move
# left click + drag to move
yabai -m config mouse_action2 resize
# right click + drag to resize

# Turn off native window shadows to eliminate the curved look underneath borders
yabai -m config window_shadow off

yabai -m mouse_drop_action swap


# Toggle between Tiling (bsp) and Floating layouts globally
alt - f : current_layout=$(yabai -m query --spaces --space | jq -r '.layout'); \
          if [ "$current_layout" = "bsp" ]; then \
              yabai -m space --layout float; \
          else \
              yabai -m space --layout bsp; \
          fi



# Disanle specific apps


yabai -m rule --add app="^Karabiner-Elements$" manage=off
yabai -m rule --add app="^Terminal$" manage=off
d 2

