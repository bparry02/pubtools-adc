# pubtools-adc Offline Installation Package

This package contains **everything needed** to install and run `pubtools-adc` on another machine **without internet access**. All dependencies are included as pre-built wheels.

## 🚀 Quick Start (Recommended)

```bash
# Extract the package (if you received a tarball)
tar -xzf pubtools-adc-offline-*.tar.gz
cd offline-pubtools-adc

# Run the automated offline installer
./install-offline.sh
```

That's it! No internet connection required.

## 📦 Package Contents

- `lib/` - Directory containing pre-built wheels including:
  - `pubtools_adc-*.whl` - The main package
  - All dependencies (AWS SDK, crypto libraries, etc.)
- `install-offline.sh` - **Fully offline** installation script
- `README.md` - This file

## 🔧 Installation Methods

### Method 1: Automated Offline Installation (Recommended)
```bash
./install-offline.sh
```

**Features:**
- ✅ **Zero internet dependency** - uses only bundled wheels
- ✅ Creates virtual environment automatically
- ✅ Installs all dependencies
- ✅ Verifies installation
- ✅ Provides usage instructions

### Method 2: Manual Installation
```bash
# Create and activate virtual environment
python3 -m venv pubtools-adc-env
source pubtools-adc-env/bin/activate

# Install all wheels offline
pip install --no-index --find-links lib/ lib/*.whl

# Verify
pubtools-adc-push --help
```

## ✅ Usage After Installation

```bash
# Activate the virtual environment (if not already active)
source pubtools-adc-env/bin/activate

# Use the tool (example commands)
pubtools-adc-push --help
pubtools-adc-push --version
```

## 📋 System Requirements

- **Python 3.6+** (Python 3.8+ recommended)
- **Linux x86_64** (wheels are pre-compiled for this platform)
- **~100MB disk space** for installation
- **No internet connection required** during installation

## 🔍 What's Included

This offline package includes wheels for all dependencies:
- **Core**: `pubtools-adc`
- **AWS**: `boto3`, `botocore`, `s3transfer`
- **Azure**: `azure-storage-blob`, `azure-mgmt-storage`
- **Cloud**: `cloudimg` (AWS/Azure image publishing)
- **Security**: `cryptography`, `gssapi`, `requests-gssapi`
- **Data**: `attrs`, `jsonschema`, `PyYAML`
- **Publishing**: `pushsource`, `pushcollector`, `pubtools`
- **Utilities**: `more-executors`, `tenacity`, `koji`
- And 30+ other dependencies...

## 🚨 Platform Compatibility

⚠️ **Important**: This package contains wheels compiled for **Linux x86_64**.

For other platforms:
- **macOS/Windows**: Some binary wheels may not work
- **ARM64**: Architecture-specific wheels would be needed
- **Different Linux distros**: Should work on most modern Linux distributions

## 🎯 Key Benefits

### ✅ Fully Offline
- No `pip install -r requirements.txt` needed on target
- No PyPI downloads during installation
- Perfect for air-gapped environments

### ✅ Complete Dependencies
- All dependencies pre-downloaded as wheels
- No compilation required on target machine
- No missing dependency surprises

### ✅ Easy Deployment
- Single archive to transfer
- One command installation
- Self-contained and portable

## 🔧 Troubleshooting

### Issue: Command not found
```bash
# Make sure virtual environment is activated
source pubtools-adc-env/bin/activate
which pubtools-adc-push
```

### Issue: Permission denied on install-offline.sh
```bash
chmod +x install-offline.sh
```

### Issue: Python version compatibility
- Requires Python 3.6 or higher
- Check: `python3 --version`

### Issue: No wheels found
- Ensure you've run the build script to populate the `lib/` directory
- Check: `ls lib/*.whl`

## 🏗️ Building This Package

This offline package is created using the build script in the main project:

```bash
# From the main pubtools-adc directory

# 1. Create and activate virtual environment (if not already done)
python3 -m venv .venv
source .venv/bin/activate

# 2. Install pubtools-adc in development mode
pip install -e .

# 3. Run the build script
./build-offline-pubtools-adc.sh
```

This will:
1. Build the pubtools-adc wheel
2. Download all dependency wheels
3. Create staging directory `build-offline/offline-pubtools-adc/` with `lib/` subdirectory
4. Copy installation files and populate the `lib/` directory
5. Create a compressed tarball containing just the `offline-pubtools-adc/` directory

## 📦 Package Information

- **Package built for**: Linux x86_64
- **Python compatibility**: 3.6+
- **Installation type**: Fully offline
- **Dependencies**: Pre-bundled as wheels in `lib/` directory
- **Extracted directory**: `offline-pubtools-adc/`
