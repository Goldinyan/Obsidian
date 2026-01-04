

## **System‑ & Hardware‑Monitoring (TUI)**

### **btop** - Perfomance Monitor 
```sh
brew install btop
btop
```
- CPU‑Graphen  
- RAM/Swap  
- Prozesse  
- Temperaturen (wenn verfügbar)  
- Teilweise GPU‑Infos  

---

### **htop** - Perfomance Monitor (simpler)
```sh
brew install htop
htop
```
- Prozessmonitor  
- Weniger grafisch als btop  

---

### **fastfetch** - System‑Specs  
```sh
brew install fastfetch
fastfetch
```
- Hardware/OS‑Infos  
- Kein Live‑Monitoring  

---

### **neofetch** -  ältere Alternative  
```sh
brew install neofetch
neofetch
```

---

### **glances** — breites Monitoring + Web‑UI  
```sh
brew install glances
glances
```
Web‑Dashboard:  
```sh
glances -w
```
→ http://localhost:61208


## **Weitere nützliche TUI‑Tools**

### **gotop** - minimalistischer Systemmonitor  
```sh
brew install gotop
gotop
```

---

### **ncdu** - Festplattenanalyse  
```sh
brew install ncdu
ncdu
```

---

### **bmon** - Netzwerk‑Graphen  
```sh
brew install bmon
bmon
```

---

### **iftop** - Traffic pro Verbindung/IP  
```sh
brew install iftop
sudo iftop
```

---


## **Empfohlene Minimal‑Installation**
```sh
brew install btop fastfetch bmon iftop ncdu
```

---

