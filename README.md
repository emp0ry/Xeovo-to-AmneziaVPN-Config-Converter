# 🌐 Xeovo to AmneziaVPN Config Converter

A Python script that converts Xeovo VPN `.conf` files into an `AmneziaVPN.backup` file compatible with the AmneziaVPN client. The script generates configurations for multiple Xeovo VPN servers across various global locations, using a user-selected `.conf` file as input. It is **cross-platform**, running on **Windows**, **Linux**, and **macOS**.

## 🚀 Features
- **Converts Xeovo VPN Configs**: Parses a Xeovo VPN `.conf` file and generates an `AmneziaVPN.backup` file.
- **Multiple Server Support**: Creates configurations for 23 server locations, including Albania (Tirana), ~Brazil (São Paulo)~, Germany (Falkenstein), and more.
- **File Explorer Integration**: Uses `tkinter` to provide a graphical file selection dialog for choosing the `.conf` file.
- **Dynamic Endpoint Updates**: Automatically updates the `Endpoint` in the configuration for each server (e.g., `al.gw.xeovo.com`, `au.gw.xeovo.com`).
- **AmneziaVPN Compatibility**: Outputs a JSON-structured `AmneziaVPN.backup` file with a properly formatted `Servers/serversList` string and escaped `last_config` fields.
- **Cross-Platform**: Works seamlessly on Windows, Linux, and macOS with minimal dependencies.
- **Console Feedback**: Displays parsed configuration data in the terminal for verification.

## 📦 Requirements
- Python 3.6 or higher
- Required Python packages (listed in `requirements.txt`):
  - `tkinter` (usually included with Python; may need `python3-tk` on Linux)
- A valid Xeovo VPN `.conf` file (WireGuard format)

## 🛠️ Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/emp0ry/Xeovo-to-AmneziaVPN-Converter.git
   cd Xeovo-to-AmneziaVPN-Converter
   ```

2. **Install Python** (if not already installed):
   - **Windows**: Download from [python.org](https://www.python.org/) or use `choco install python`.
   - **Linux**: Install via package manager:
     - Ubuntu/Debian: `sudo apt-get install python3`
     - CentOS/RHEL: `sudo yum install python3`
   - **macOS**: Use Homebrew: `brew install python3` (or pre-installed on recent versions).
   - Verify: `python3 --version` or `python --version`.

3. **Install Tkinter** (Linux only, if missing):
   - Ubuntu/Debian: `sudo apt-get install python3-tk`
   - CentOS/RHEL: `sudo yum install python3-tkinter`

4. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   If permission issues occur:
   ```bash
   pip install -r requirements.txt --user
   ```
   *Note*: If `requirements.txt` only includes `tkinter`, this step may be skipped as it’s typically bundled with Python.

5. **Prepare a Xeovo VPN `.conf` File**:
   - Ensure you have a valid `.conf` file from Xeovo VPN, containing `Interface` and `Peer` sections with details like `PrivateKey`, `PublicKey`, `Endpoint`, etc.

## ▶️ Usage
Run the script with:
```bash
python main.py
```

The script will:
- Open a file explorer dialog to select a `.conf` file.
- Parse the selected `.conf` file and display its contents in the terminal.
- Generate an `AmneziaVPN.backup` file in the script’s directory.
- Output the path to the generated file.

### 📋 Example Output
```
Parsed Configuration Data:
--------------------------------------------------
Address: 10.0.0.2/32
PrivateKey: <private_key>
DNS: 1.1.1.1
Jc: 10
Jmin: 100
Jmax: 1000
S1: 10
S2: 20
H1: <hash1>
H2: <hash2>
H3: <hash3>
H4: <hash4>
PublicKey: <public_key>
AllowedIPs: 0.0.0.0/0, ::/0
Endpoint: au.gw.xeovo.com:51820

AmneziaVPN.backup file created at: AmneziaVPN.backup
```

The generated `AmneziaVPN.backup` file can be imported into the AmneziaVPN client to access Xeovo VPN servers.

## 💡 Platform-Specific Notes
- **Windows**:
  - Works out of the box with Python 3.6+ and `tkinter` (included in standard Python installations).
  - The file explorer dialog uses the native Windows file picker.
- **Linux**:
  - Install `python3-tk` if the file explorer dialog fails to open.
  - The dialog uses the native file picker (e.g., GTK or Qt, depending on the desktop environment).
- **macOS**:
  - Python 3 and `tkinter` are typically pre-installed.
  - Use `python3` to run the script if `python` points to Python 2.
  - The file explorer dialog uses the native macOS file picker.

## 🧰 Troubleshooting
- **File Explorer Dialog Doesn’t Open**:
  - Ensure `tkinter` is installed (see installation steps for Linux).
  - Verify Python 3.6+ (`python3 --version` or `python --version`).
  - Check for errors in the terminal and install missing dependencies.
- **Invalid `.conf` File**:
  - Ensure the `.conf` file has valid `Interface` and `Peer` sections.
  - Check that fields like `PrivateKey`, `PublicKey`, and `Endpoint` are present.
- **Generated `AmneziaVPN.backup` Not Working**:
  - Verify the output JSON structure matches AmneziaVPN’s expected format (e.g., `Servers/serversList` as a string, not an array).
  - Ensure the `last_config` field in each server’s `awg` configuration is a properly escaped JSON string.
  - Share the generated file (redact sensitive keys) for debugging.
- **Dependency Issues**:
  - Run `pip install -r requirements.txt --user` for permission errors.
  - If `tkinter` is missing, install it manually (e.g., `sudo apt-get install python3-tk` on Ubuntu).

## ☕ Donation
[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/emp0ry)

## 📄 License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 🙌 Acknowledgments
- Built with Python, `configparser`, `json`, and `tkinter`.
- Inspired by the need to integrate Xeovo VPN with AmneziaVPN clients.
