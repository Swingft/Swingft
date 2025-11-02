
<img width="453" height="171" alt="Swingft Logo" src="https://github.com/user-attachments/assets/6ccbf1bc-e6ca-48fb-8ddd-bb0863992e93" />

# Swingft

**Swingft** is a Swift source code obfuscation tool.
<br><br>

## Main Function
- **Identifier Obfuscation**
- **Control Flow Obfuscation**
  - Control Flow Flattening
  - Opaque Predicate Insertion
  - Dead Code Insertion
  - Dynamic Function Calls
- **String Encryption**
- **Comment and Debug Code Removal**

> Using the `SwingftSecurity` module when applying string encryption

---

## Installation and use

### 1. Download and Settings
```bash
git clone <repository_url>
python3 -m venv venv
source venv/bin/activate
cd swingft
pip install -r requirements.txt
```

### 2. Config file settings
- Enter the path to the obfuscated project, the path to the obfuscated project file, and the build target.
- Function-specific options (true/false) can be specified
- You can enter the elements you want to require or exclude for obfuscation and encryption. 
- Preflight is an option that can be selected from three options: check, apply, and ignore via cli when it conflicts with internal regulations.
```bash
python3 ./swingft --json [config_file_path/config_file_name] run
```

### 3. Swingft Run
```bash
python3 ./swingft -c {config_file_path}
```

### 4. Get help
```bash
python3 ./swingft -h
python3 ./swingft run -h
```

---

## Output
### 1. Resulting file directory (`swingft_output/`)
All result files are created under the `{obf_project_dir}/swingft_output/` directory.

#### 1-1. ID Obfuscation Dump File
- **Swingft_ID_Obfuscation_Dump.json**
  - Location: `{obf_project_dir}/swingft_output/Swingft_ID_Obfuscation_Dump.json`
  - Description: JSON file containing the identifier obfuscation results
  - Generated Location: `ID_Obf/id_dump.py`

#### 1-2. CFF Diff File (Control flow flattening results)
- **Directory**: `{obf_project_dir}/swingft_output/Swingft_CFF_Dump/`
  - File name: Generated in the format `{path}.diff`
  - Description: Diff files comparing before and after control flow flattening
  - Generated Location: `Obfuscation_Pipeline/CFF/run_swiftCFF.py`, `Obfuscation_Pipeline/CFF/Sources/Swingft_CFF/main.swift`

### 2. StringSecurity folder (maintained separately)
- **Directory**: `{obf_project_dir}/StringSecurity/`
  - Description: Swift package module for string encryption and CFG functionality
  - Created in: `CFG/last.py`, `String_Encryption/SwingftEncryption.py`
  - Note: Located in the root directory, separate from the output file directory

### 3. Obfuscated Swift Source Files
- Swift source files from actual projects have been obfuscated and modified.

### 4. Files that are kept unorganized
- `{obf_project_dir}/swingft_output/` directory and its contents - kept as the final output
- `StringSecurity/` folder - kept as it is required for the build
- Obfuscated Swift source files - kept as the final output
