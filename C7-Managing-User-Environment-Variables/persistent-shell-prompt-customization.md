#### Why the Command Is Not Working
```bash
PS1="World's Best Hacker: #"
export PS1
```
- `export PS1=...` only affects the **current shell session**.
- Environment variables are **not persisted** unless set in a shell startup file (e.g., `~/.bashrc`, `~/.zshrc`).
- Once you open a new terminal, the shell reinitializes and your change is lost.

---

#### ✅ Actual Working Command (Bash)

```bash
echo 'export PS1="World'\''s Best Hacker: # "' >> ~/.bashrc
source ~/.bashrc
```

*(For Zsh, use `~/.zshrc` instead of `~/.bashrc`)*

---

#### Why This Command Works

- Shell startup files are executed **every time a new shell starts**.
- Adding `export PS1=...` there makes the prompt **persistent across sessions**.
- Proper escaping ensures the apostrophe (`'`) is interpreted correctly.

---

#### Reverting the Prompt to Default

There are **two safe ways** to revert your prompt in Kali Linux (Bash).

---

### ✅ Method 1: Temporarily Revert (Current Session Only)

```bash
export PS1='\u@\h:\w\$ '
```

**Explanation:**
- This resets the prompt **only for the active terminal session**.
- Once the terminal is closed, the customized prompt from `~/.bashrc` will return.
- Useful for quick testing or troubleshooting.

---

### ✅ Method 2: Permanently Revert (Recommended)

```bash
nano ~/.bashrc
```

- Locate the line:
  ```bash
  export PS1="World's Best Hacker: # "
  ```
- Delete or comment it:
  ```bash
  # export PS1="World's Best Hacker: # "
  ```
- Save and exit, then reload:
  ```bash
  source ~/.bashrc
  ```

**Explanation:**
- `~/.bashrc` is executed every time Bash starts.
- Removing the line restores Kali Linux’s **default prompt behavior**.
- This is the cleanest and safest method.

---

### ✅ Method 3: Automatic Cleanup (One‑Liner)

```bash
sed -i '/World.*Best Hacker/d' ~/.bashrc && source ~/.bashrc
```

**Explanation:**
- Deletes the custom prompt line automatically.
- Best when you know exactly what you added.
- Immediate effect after reloading.

---

✔ Kali Linux uses **Bash by default**, so all commands above apply directly.<br>
✔ Changes affect only your user, not the system globally.