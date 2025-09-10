# Minecraft Schematic to JSON Converter

## Overview

**`schem_to_json.py`** is a Python script that automates the conversion of Minecraft WorldEdit `.schem` files into JSON slice format for use with mods like **Lost Cities**.

The script monitors a folder for new schematic files, archives them, and converts them into JSON with:

- `xsize` / `zsize` for dimensions  
- A **palette** mapping UTF-8 symbols to block IDs  
- **Slices** representing vertical layers of the schematic  

> `" "` is always reserved for `minecraft:air` to ensure empty space is consistent.

---

## Why Use This Script?

1. **Lost Cities edit mode can be buggy or unusable** depending on the modpack.  
2. **Leverage Minecraft schematics for Lost Cities builds** without manually recreating complex structures in JSON.  
3. **Faster workflow:** the script runs in the background, automatically converting schematics as you create and save them, eliminating the need to manually run each schematic through the converter.

---

## Requirements

- **Python 3.13.7**  
- [amulet-nbt](https://pypi.org/project/amulet-nbt/) 2.1.5  
- [watchdog](https://pypi.org/project/watchdog/) 6.0.0  
- **Minecraft** with **WorldEdit** installed  
  - Tested with **Forge WorldEdit 7.2.15** and **Lost Cities 1.20-7.4.3**

---

## Setup Instructions

### 1. Install Python

1. Download and install [Python 3.13.7](https://www.python.org/downloads/release/python-3137/) for your OS.  
2. Make sure Python is added to your system PATH.

### 2. Create a Virtual Environment

From your project folder:

```bash
python -m venv venv
```
### 3. Activate the Virtual Environment

Windows (PowerShell):
```bash
.\venv\Scripts\Activate.ps1
```
macOS / Linux:
```bash
source venv/bin/activate
```

### 4. Install Required Python Packages

Inside the activated venv:
```
pip install amulet-nbt==2.1.5 watchdog==6.0.0
```

### 5. Copy the Script

Place `schem_to_json.py` into the **root folder** of your project (or a folder of your choice) where you want to run the script.

### 6. Configure Folder Paths

Open `schem_to_json.py` and set your folder paths:

```python
INPUT_DIR = r"...Your Minecraft Instace\config\worldedit\schematics" # or wherever it saves schematics / perhaps a folder of your choice
ARCHIVE_DIR = r"Folder Path Of Your Choice"
OUTPUT_DIR = r"Folder Path Of Your Choice"
```

### 7. Run the Python Script

python schem_to_json.py

---

## Minecraft WorldEdit Instructions

> Skip this section if you already know how to use WorldEdit.

1. **Open your Minecraft world** with WorldEdit installed.

2. **Get the WorldEdit wand:**

```minecraft
//wand
```
Select a region:

Left-click a block for the first position

Right-click a block for the second position

Copy the selection:

```minecraft
//copy
```
Save the selection as a schematic:

```minecraft
//schematic save example
```
Replace `example` with your desired schematic name.

---

Now you can rinse and repeat without having to manually convert each schematic into a lostcities compatible .json part.