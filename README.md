# NSE ATH Signals

A comprehensive trading signals system for NSE (National Stock Exchange) stocks based on Advanced Technical Hosting (ATH) indicators.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Requirements](#system-requirements)
- [Windows 10 Setup Guide](#windows-10-setup-guide)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

NSE ATH Signals is a Python-based application that generates trading signals for NSE stocks using advanced technical analysis indicators. This tool helps traders identify potential buy/sell opportunities through automated signal generation.

## Features

✨ **Key Features:**
- Real-time NSE data integration
- Advanced technical indicator analysis
- Automated signal generation
- Support for multiple timeframes
- Alert system for significant signals
- Backtesting capabilities
- User-friendly interface

## System Requirements

### Minimum Requirements
- **OS:** Windows 10 (Build 1909 or later)
- **RAM:** 4 GB minimum (8 GB recommended)
- **Storage:** 500 MB free space
- **Processor:** Intel i5 or equivalent
- **Internet:** Stable connection required

### Software Requirements
- Python 3.8 or higher
- pip (Python package installer)
- Git for Windows

## Windows 10 Setup Guide

### Step 1: Download and Install Python

1. **Download Python:**
   - Visit [python.org](https://www.python.org/downloads/)
   - Click "Downloads" → Select "Windows"
   - Download Python 3.10 or 3.11 (Latest stable version)

2. **Install Python:**
   - Run the downloaded installer (`.exe` file)
   - ⚠️ **IMPORTANT:** Check the box "Add Python to PATH" at the bottom of the installer
   - Click "Install Now" or customize installation path if needed
   - Wait for installation to complete

3. **Verify Installation:**
   - Open Command Prompt (Win + R, type `cmd`, press Enter)
   - Run the following commands:
     ```bash
     python --version
     pip --version
     ```
   - Both commands should display version numbers

### Step 2: Install Git for Windows

1. **Download Git:**
   - Visit [git-scm.com](https://git-scm.com/download/win)
   - Download the latest Git for Windows installer

2. **Install Git:**
   - Run the installer
   - Follow the installation wizard with default settings
   - Ensure "Git Bash Here" and "Git GUI Here" are checked

3. **Verify Installation:**
   - Open Command Prompt or Git Bash
   - Run:
     ```bash
     git --version
     ```

### Step 3: Clone the Repository

1. **Create a Project Directory:**
   - Create a folder where you want the project (e.g., `C:\Projects`)
   - Open Command Prompt in that directory

2. **Clone Repository:**
   - Run:
     ```bash
     git clone https://github.com/kmsanjeev/nse-ath-signals.git
     cd nse-ath-signals
     ```

### Step 4: Create Virtual Environment

1. **Create Virtual Environment:**
   - In Command Prompt, navigate to the project directory and run:
     ```bash
     python -m venv venv
     ```
   - This creates a virtual environment folder named `venv`

2. **Activate Virtual Environment:**
   - Run:
     ```bash
     venv\Scripts\activate
     ```
   - You should see `(venv)` prefix in your Command Prompt

### Step 5: Install Dependencies

1. **Update pip:**
   ```bash
   python -m pip install --upgrade pip
   ```

2. **Install Required Packages:**
   ```bash
   pip install -r requirements.txt
   ```
   - This installs all necessary dependencies

3. **Verify Installation:**
   ```bash
   pip list
   ```

## Installation

### Quick Install Summary

```bash
# Clone repository
git clone https://github.com/kmsanjeev/nse-ath-signals.git
cd nse-ath-signals

# Create virtual environment
python -m venv venv

# Activate virtual environment (Windows)
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run application
python main.py
```

## Configuration

### Configuration File Setup

1. **Create Configuration File:**
   - Locate or create `config.json` in the project root directory

2. **Basic Configuration Template:**
   ```json
   {
     "nse": {
       "url": "https://www.nseindia.com/",
       "timeout": 30
     },
     "signals": {
       "rsi_threshold": 30,
       "macd_enabled": true,
       "bollinger_bands_enabled": true
     },
     "alerts": {
       "email_enabled": false,
       "telegram_enabled": false
     },
     "data": {
       "cache_enabled": true,
       "cache_duration": 3600
     }
   }
   ```

3. **Update Configuration:**
   - Modify parameters according to your preferences
   - Set API keys if required (optional features)

### Environment Variables

1. **Create `.env` File:**
   ```bash
   # In project root directory, create .env file
   NSE_USER_AGENT=Mozilla/5.0 (Windows NT 10.0; Win64; x64)
   DATA_PATH=./data
   LOG_LEVEL=INFO
   ```

2. **Load Environment Variables:**
   - The application automatically loads `.env` on startup

## Usage

### Running the Application

1. **Start the Application:**
   ```bash
   python main.py
   ```

2. **Via Web Interface (if available):**
   ```bash
   python app.py
   ```
   - Open browser: `http://localhost:5000`

3. **Command Line Usage:**
   ```bash
   # Generate signals for specific stock
   python cli.py --symbol SBIN

   # Backtest strategy
   python backtest.py --symbol SBIN --period 365

   # Export signals
   python export.py --format csv
   ```

### Basic Operations

**Generate Signals:**
```python
from nse_signals import SignalGenerator

generator = SignalGenerator()
signals = generator.get_signals('SBIN')
print(signals)
```

**Get Stock Data:**
```python
from nse_signals import DataFetcher

fetcher = DataFetcher()
data = fetcher.get_historical_data('INFY', days=30)
print(data)
```

## Troubleshooting

### Common Issues and Solutions

#### 1. **Python Not Found Error**
```
'python' is not recognized as an internal or external command
```
**Solution:**
- Python not added to PATH
- Reinstall Python and ensure "Add Python to PATH" is checked
- Restart Command Prompt after installation

#### 2. **Virtual Environment Won't Activate**
```
.\venv\Scripts\activate : File cannot be loaded because running scripts is disabled
```
**Solution:**
- Run PowerShell as Administrator
- Execute: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
- Try activation again or use Command Prompt instead

#### 3. **Module Not Found Error**
```
ModuleNotFoundError: No module named 'requests'
```
**Solution:**
- Ensure virtual environment is activated (check for `(venv)` prefix)
- Run: `pip install -r requirements.txt` again
- Verify requirements.txt exists in project directory

#### 4. **NSE Connection Error**
```
Connection error: Unable to connect to NSE
```
**Solution:**
- Check internet connection
- Verify firewall/proxy settings
- Update `config.json` timeout value
- Try with VPN if NSE blocks direct connections

#### 5. **Permission Denied Error**
```
PermissionError: [Errno 13] Permission denied
```
**Solution:**
- Run Command Prompt as Administrator
- Check file permissions in project folder
- Ensure antivirus isn't blocking file operations

#### 6. **pip Installation Hangs**
**Solution:**
- Press Ctrl+C to cancel
- Clear pip cache: `pip cache purge`
- Try with: `pip install -r requirements.txt --no-cache-dir`

### Getting Help

- Check the project's issue tracker on GitHub
- Review application logs in `logs/` directory
- Enable debug mode: `LOG_LEVEL=DEBUG` in `.env`

## Development

### Setting Up for Development

```bash
# Install development dependencies
pip install -r requirements-dev.txt

# Run tests
pytest tests/

# Format code
black .

# Lint code
flake8 .
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -am 'Add new feature'`
4. Push to branch: `git push origin feature/your-feature`
5. Submit a Pull Request

## Version History

- **v1.0.0** - Initial release
- **v1.1.0** - Added alert system
- **v1.2.0** - Backtesting support
- **v2.0.0** - Web interface implementation

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

⚠️ **Important:** This tool is for educational and informational purposes only. It is not financial advice. Always do your own research and consult with a financial advisor before making trading decisions. The authors are not responsible for any trading losses.

## Support

For support, questions, or suggestions:
- Open an issue on GitHub
- Contact: kmsanjeev@example.com
- Visit: [Project Documentation](https://github.com/kmsanjeev/nse-ath-signals/wiki)

---

**Last Updated:** December 6, 2025

**Created by:** [kmsanjeev](https://github.com/kmsanjeev)

Happy Trading! 📈
