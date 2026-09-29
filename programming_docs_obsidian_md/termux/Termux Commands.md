
### Table of Contents

- [Setup Storage Access](#Setup_Storage_Access)
- [Git Workflow](#Git_Workflow)
- [More Commands](#More_Commands)

---

### Setup_Storage_Access
Give Termux access to Android storage by running this command and Android will ask for storage permission (Allow it)

```bash
termux-setup-storage
```

Termux then creates this:

```Bash
~/storage/
```

With shortcuts such as:

```bash
~/storage/shared/
~/storage/downloads/
~/storage/documents/
```

`~/storage/shared/` points roughly to our phones **Internal Storage**. We can go to those directory using:

```bash
cd ~/storage/documents
```

Check what's there using this command:

```bash
ls
```

---

### Git_Workflow
Then install git using these commands:

```bash
pkg update
pkg install git
```

Then simply run any git commands:

```bash
git init
git add .
git commit -m "..."
git clone
```


--- 

### More_Commands
There's this command for cleaning the terminal and keeping the session:

```bash
clear
```

