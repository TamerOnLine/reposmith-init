# 🐍 install_all.py — Multi‑Python Package Manager

## 📘 Overview
`install_all.py` lets you **install, upgrade, or uninstall** Python packages across **all Python versions** installed on your system (e.g., 3.12, 3.13).  
It reads package names from a simple JSON configuration file and performs the operations automatically or selectively.

---

## ⚙️ Key Features
- 🔍 **Automatic Python version detection** via `py -0p` or Windows Registry.
- 📦 **Batch install or upgrade** multiple packages at once.
- ❌ **Batch uninstall** packages from all interpreters.
- 🧩 **Version targeting** using the `--versions` option.
- 🧪 **Dry-run mode** to preview commands without executing them.
- ⚡ **Dynamic behavior** — works with any packages defined in JSON.

---

## 📁 File Structure
```
tools/
├── install_all.py      # Main script
└── packages.json       # JSON configuration file
```

---

## 🧾 packages.json
List all packages you want to install or uninstall:
```json
{
  "packages": [
    "reposmith-tol",
    "fastapi",
    "uvicorn",
    "requests"
  ]
}
```

---

## 🚀 Usage

> Run all commands from the project root or the `tools/` folder.

### 1️⃣ Install or upgrade packages on all Python versions:
```powershell
py tools/install_all.py
```

### 2️⃣ Uninstall packages from all Python versions:
```powershell
py tools/install_all.py --uninstall
# or short:
py tools/install_all.py -u
```

### 3️⃣ Preview commands only (dry-run):
```powershell
py tools/install_all.py --dry-run
```

### 4️⃣ Specify certain Python versions:
```powershell
py tools/install_all.py --versions "-3.13,-3.12"
```

### 5️⃣ Combine options:
```powershell
py tools/install_all.py -u --versions "3.13" --dry-run
```

---

## 🧠 How It Works
1. Detects Python interpreters using:
   - `py -0p`
   - Windows Registry (fallback)
2. Loads package list from `packages.json`.
3. Executes the relevant commands:
   - `pip install -U` for install/upgrade.
   - `pip uninstall -y` for removal.
4. Prints a detailed report for all operations.

---

## 🧰 Requirements
- Windows 10 or newer  
- Python 3.12+ with **Python Launcher (`py.exe`)**  
- Permission to install/uninstall packages

---

## 🪄 Example Scenarios

Upgrade `reposmith-tol` and `fastapi` across all interpreters:
```powershell
py tools/install_all.py
```

Remove the same packages from Python 3.13 only:
```powershell
py tools/install_all.py -u --versions "3.13"
```

Preview all actions before running them:
```powershell
py tools/install_all.py --dry-run
```

---

## 📄 License
Licensed under the [MIT License](https://opensource.org/licenses/MIT).
