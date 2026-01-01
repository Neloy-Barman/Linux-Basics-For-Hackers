# 🧾 Nano Editor Cheat‑Sheet (Kali Linux)

> **Legend**
- `^` = **Ctrl**
- `M-` = **Alt (Meta)**

---

## 📂 File Operations

| Action | Shortcut |
|------|---------|
| Save (Write Out) | `^O` → `Enter` |
| Exit Nano | `^X` |
| Open / Insert file | `^R` |

---

## 🧭 Navigation

| Action | Shortcut |
|------|---------|
| Move cursor | Arrow keys |
| Start of line | `^A` |
| End of line | `^E` |
| Next page | `^V` |
| Previous page | `M-V` |
| Go to line number | `^/` |

---

## ✏️ Editing

| Action | Shortcut |
|------|---------|
| Cut line | `^K` |
| Paste line | `^U` |
| Undo | `M-U` |
| Redo | `M-E` |
| Delete character | `Backspace` / `Delete` |
| Insert new line | `Enter` |

---

## 🔍 Search & Replace

| Action | Shortcut |
|------|---------|
| Search text | `^W` |
| Find next | `M-W` |
| Search & replace | `^\` |

---

## 📑 Text Formatting

| Action | Shortcut |
|------|---------|
| Justify (wrap) text | `^J` |
| Toggle line numbers | `M-#` |
| Enable soft wrap | `M-S` |

---

## 🧩 Commenting Lines (IMPORTANT)

> ❌ Nano has **no single “comment‑out” key**

### ✅ Manual Commenting (Most Common)

| File Type | Comment Character |
|---------|------------------|
| Shell (`.sh`, `.bashrc`) | `#` |
| Python | `#` |
| Config files | `#` or `;` |
| C / C++ | `//` |
| HTML | `<!-- -->` |

➡️ Place cursor at line start and type the comment symbol.

---

### ✅ Comment Multiple Lines (Search & Replace)

**Add comments to all lines:**
```
^\
Search: ^
Replace: #
Replace All
```

**Uncomment lines:**
```
^\
Search: ^#
Replace: (empty)
Replace All
```

---

### ✅ Selection (Mark Mode)

| Action | Shortcut |
|------|---------|
| Start selection | `^6` |
| Copy selection | `M-6` |
| Cut selection | `^K` |
| Paste selection | `^U` |

---

## 🆘 Help & Info

| Action | Shortcut |
|------|---------|
| Show help | `^G` |
| Show cursor position | `^C` |

---

## ✅ Safe Exit Workflow

1. `^X` → Exit  
2. `Y` → Save changes  
3. `Enter` → Confirm filename  

---

### 🐧 Kali Linux Notes
- Nano is ideal for quick config edits
- No native comment toggle (unlike Vim/VS Code)
- Use **Search & Replace** for bulk commenting

✔ Beginner‑friendly  
✔ Keyboard‑centric  
✔ Safe for system configs  

---
**End of File**