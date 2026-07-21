# Untitled


Ich habe die Performance beider Suchverfahren in C++ mal ausgerechnet, wobei die Zeitmessung präzise in Nanosekunden erfolgt. Pro Array-Größe wurden jeweils 10 Testläufe mit komplett zufälligen Daten und variierenden Suchzielen generiert. Die dünnen Linien im Diagramm zeigen die exakten Einzelwerte der verschiedenen Durchläufe, während die dicke Linie den Gesamtdurchschnitt darstellt.

Um absolut unverfälschte Hardware-Messdaten zu erhalten, wurde vor jedem Durchlauf ein CPU Cache Flush durchgeführt. Dies verhindert halt, dass nachfolgende Testläufe von bereits im L1/L2-Cache vorliegenden Daten profitieren.
Sonst wäre es unfair.

Da für die Binary-Search die Sortierung in die Zeitmessung einfließt, habe ich hier std::sort benutzt, also Basic von C++. Das benutzt Introsort, einem hochoptimierten Hybrid-Algorithmus. Er startet mit Quicksort, wechselt bei zu großer Rekursionstiefe zu Heapsort (um diesen O(NlogN) Worst-Case zu garantieren) und bricht bei kleinen Datensegmenten (z.b. wenn sie unter 16 Elementen sind) automatisch auf Insertion Sort herunter, da dessen minimaler Overhead bei Micro-Arrays extrem schnell ist.



---@type ChadrcConfig
local M = {}


M.ui = {
  theme = "monochrome",
  transparency = true,

  cmp = {
    icons = true,
    lspkind_text = true,
    style = "default",                -- default/flat_light/flat_dark/atom/atom_colored
  },
  telescope = { style = "borderless" }, -- borderless / bordered

  statusline = {
    theme = "default",   -- default/vscode/vscode_colored/minimal
    -- default/round/block/arrow separators work only for default statusline theme
    -- round and block will work for minimal theme only
    separator_style = "default",
    order = nil,
    modules = nil,
  },

  -- lazyload it when there are 1+ buffers
  tabufline = {
    enabled = true,
    lazyload = true,
    order = { "treeOffset", "buffers", "tabs", "btns" },
    modules = nil,
  },
}


M.plugins = "custom.plugins"

return M
