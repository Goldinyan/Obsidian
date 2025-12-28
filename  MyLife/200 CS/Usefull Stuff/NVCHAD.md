Date: 2025-12-16
Tags: {
#N 
[[%Nvim]]
[[%Command]]
}


# NVCHAD

- zc → fold schließen
- zo → fold öffnen
- za → fold togglen
- zM → alles schließen
- zR → alles öffnen

<leader>fw -> suchen nach etwas

strg + n -> file tree opens

gd -> jumping to def of func

strg + h -> back to file tree when in file 

space f m -> LSP formatting



🖊️ Insert Mode (`i`)

- Ctrl+b → Anfang der Zeile
- Ctrl+e → Ende der Zeile
- Ctrl+h/j/k/l → Links / Runter / Hoch / Rechts

---

📖 Normal Mode (`n`)

- Esc → Highlight löschen
- Ctrl+h/j/k/l → Fenster links / runter / hoch / rechts
- Ctrl+s → Speichern
- Ctrl+c → Ganze Datei kopieren
- <leader>n → Toggle line numbers
- <leader>rn → Toggle relative numbers
- j/k/↑/↓ → Wrapped line‑Navigation (gj/gk)
- <leader>b → Neuer Buffer
- <leader>ch → Cheatsheet
- <leader>fm → LSP Formatieren

---

🖥️ Terminal Mode (`t`)

- Ctrl+x → Escape Terminal (zurück nach Normal Mode)

---

✏️ Visual Mode (`v`)

- ↑/↓ → Wrapped line‑Navigation
- < → Einrücken links (bleibt markiert)
- > → Einrücken rechts (bleibt markiert)
- <leader>/ → Toggle Comment

---

📦 Visual Block Mode (`x`)

- j/k → Wrapped line‑Navigation
- p → Paste ohne Überschreiben des Registers

---

📑 Tabufline

- <Tab> → Nächster Buffer
- <Shift+Tab> → Vorheriger Buffer
- <leader>x → Buffer schließen

---

💬 Comment

- Normal: <leader>/ → Toggle Comment
- Visual: <leader>/ → Toggle Comment (markierte Zeilen)

---

⚙️ LSP

- gD → Declaration
- gd → Definition
- K → Hover
- gi → Implementation
- <leader>ls → Signature Help
- <leader>D → Type Definition
- <leader>ra → Rename
- <leader>ca → Code Action
- gr → References
- <leader>lf → Diagnostics Float
- [d / ]d → Prev/Next Diagnostic
- <leader>q → Diagnostics → Loclist
- <leader>wa → Workspace add
- <leader>wr → Workspace remove
- <leader>wl → Workspace list

---

🌲 NvimTree

- Ctrl+n → Toggle Tree
- <leader>e → Focus Tree

---

🖥️ NvTerm

- <A-i> → Toggle Floating Terminal
- <A-h> → Toggle Horizontal Terminal
- <A-v> → Toggle Vertical Terminal
- <leader>h> → Neuer Horizontaler Terminal
- <leader>v> → Neuer Vertikaler Terminal

---

❓ WhichKey

- <leader>wK → Alle Keymaps anzeigen
- <leader>wk → Keymap suchen

---

📏 Indent Blankline

- <leader>cc → Jump to current context

---

🔧 Gitsigns

- [c / ]c → Prev/Next Hunk
- <leader>rh → Reset Hunk
- <leader>ph → Preview Hunk
- <leader>gb → Blame Line
- <leader>td → Toggle Deleted


- :Telescope diagnostics zeigt alle Fehler in einer Liste.








-- Insert Mode: Alt+8/9/5/6 → { } [ ]
vim.keymap.set("i", "<M-8>", "{", { desc = "Insert {" })
vim.keymap.set("i", "<M-9>", "}", { desc = "Insert }" })
vim.keymap.set("i", "<M-5>", "[", { desc = "Insert [" })
vim.keymap.set("i", "<M-6>", "]", { desc = "Insert ]" })

-- Normal Mode: Alt+8/9/5/6 → springen/ersetzen mit { } [ ]
vim.keymap.set("n", "<M-8>", "{", { desc = "Normal {" })
vim.keymap.set("n", "<M-9>", "}", { desc = "Normal }" })
vim.keymap.set("n", "<M-5>", "[", { desc = "Normal [" })
vim.keymap.set("n", "<M-6>", "]", { desc = "Normal ]" })

-- Visual Mode (optional)
vim.keymap.set("v", "<M-8>", "{", { desc = "Visual {" })
vim.keymap.set("v", "<M-9>", "}", { desc = "Visual }" })
vim.keymap.set("v", "<M-5>", "[", { desc = "Visual [" })
vim.keymap.set("v", "<M-6>", "]", { desc = "Visual ]" })


# References