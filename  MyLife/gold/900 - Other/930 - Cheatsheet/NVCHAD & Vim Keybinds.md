Date: 2025-12-16
Tags: {
#N 
[[%Nvim]]
[[%Command]]
}

:Lazy
für plugins
# NVCHAD

- zc → fold schließen
- zo → fold öffnen
- za → fold togglen
- zM → alles schließen
- zR → alles öffnen


- <leader>lf → Diagnostics Float
- [d / ]d → Prev/Next Diagnostic
- <leader>q → Diagnostics → Loclist

<leader>fw -> suchen nach etwas
:s/x/y/g -> macht x zu y;
bd -> closes current view
gc -> ausgewählten code block zum kommentar machen 
strg + n -> file tree opens

gd -> jumping to def of func

strg + h -> back to file tree when in file 

space f m -> LSP formatting



🖊️ Insert Mode (`i`)

- Ctrl+b → Anfang der Zeile
- Ctrl+e → Ende der Zeile
- Ctrl+h/j/k/l → Links / Runter / Hoch / Rechts

---
Klar, Ansgar — große Sprünge (“big jumps”) in Vim bzw. Neovim mit NvChad funktionieren genauso wie in normalem Vim, aber NvChad bringt ein paar zusätzliche, sehr praktische Bewegungs‑Plugins mit.

Damit du sofort sauber arbeiten kannst, hier eine kompakte, Obsidian‑taugliche Übersicht.

  

🚀 Große Sprünge in Vim / Neovim (auch in NvChad)

🧭 1. Klassische Vim‑Sprünge (funktionieren immer)

Zeilenweise große Sprünge

Bewegung | Wirkung

------------------

Ctrl + d | Halbseite nach unten (“down”)

Ctrl + u | Halbseite nach oben (“up”)

Ctrl + f | Ganze Seite nach unten (“forward”)

Ctrl + b | Ganze Seite nach oben (“backward”)

Zu Anfang/Ende

Bewegung | Wirkung

------------------

gg | Ganz nach oben

G | Ganz nach unten

123G | Zu Zeile 123

  

🎯 2. Wort‑ und Satzsprünge

Bewegung | Wirkung

------------------

w / b | Wortweise vor/zurück

W / B | Wortweise, aber “groß” (Whitespace‑basiert)

} / { | Absatzweise vor/zurück

  

🔥 3. NvChad‑spezifisch: Hop (extrem schnelle Sprünge)

NvChad nutzt Hop.nvim (früher auch Leap). Standard‑Keybinds:

Taste | Wirkung

---------------

s | Hop‑Sprung zu beliebigem Zeichen

S | Rückwärts

f / F | Hop‑Sprung zu erstem Vorkommen eines Zeichens

t / T | Bis kurz vor ein Zeichen

Hop zeigt dir kleine Buchstaben an, mit denen du direkt hinspringst — perfekt für große Textblöcke.

  

🧲 4. Treesitter‑Sprünge (NvChad integriert)

Wenn du strukturell springen willst (Funktionen, Klassen, Blöcke):

Taste | Wirkung

---------------

]m | Nächste Funktion

[m | Vorherige Funktion

]] | Nächster Block

[[ | Vorheriger Block

  

🗂️ 5. Datei‑Navigation (Telescope)

Für große Projekte oft der schnellste “Sprung”:

Taste | Wirkung

---------------

<leader> f f | Datei suchen

<leader> f w | Wort im Projekt suchen (live grep)

<leader> f b | Buffer wechseln

  

⚙️ 6. Eigene große Sprünge definieren

Wenn du z. B. 10 Zeilen auf einmal springen willst:

Lua

-- in ~/.config/nvim/lua/custom/mappings.lua

local map = vim.keymap.set

  

map("n", "<leader>j", "10j", { desc = "Großer Sprung nach unten" })

map("n", "<leader>k", "10k", { desc = "Großer Sprung nach oben" })

  

Wenn du willst, kann ich dir auch eine minimalistische NvChad‑Keybind‑Cheatsheet‑Seite für Obsidian bauen — perfekt für deine Sammlung klarer, wiederverwendbarer Notizen.
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





# References