### **Kompilieren**
Im Projektordner:

```
javac -d out src/**/*.java
```

- `src/` → dein Quellcode  
- `out/` → Zielordner für `.class` Dateien

### **Ausführen**
```
java -cp out Main
```

## Nvim
```# Build
:!javac -d out src/**/*.java

# Run
:!java -cp out Main
```