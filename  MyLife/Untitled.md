clang -Wall -Wextra -std=c11 -Iinclude -I/opt/homebrew/include \
      -fsanitize=address -g -O0 \
      -L/opt/homebrew/lib -lSDL2 -lSDL2_image \
      -o main main.c
