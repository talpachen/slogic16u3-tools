# SLogic16U3-tools

Minimal instructions to set up and run the ota, cli, and pt components.

## Prerequisites
- Python 3.8+ (recommended)
- cmake, ninja, a C/C++ toolchain (for the CLI)
- git (optional)

## Setup (Unix/macOS)
1. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
   Windows (PowerShell):
   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

2. Install Python dependencies for each component:
   ```bash
   pip install -r ota/requirements.txt
   pip install -r cli/requirements.txt
   pip install -r pt/requirements.txt
   ```

## Build the CLI
From the repo root:
```bash
cd cli
cmake -B build -GNinja -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DCMAKE_BUILD_TYPE=Debug
cmake --build build
# Built binary: ./build/slogic_cli
```

To build a release binary:
```bash
cmake -B build -GNinja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

## Run the PT GUI
From the repo root:
```bash
cd pt
python src/gui.py
```

## Run the CLI
From the cli directory (after build):
```bash
./build/slogic_cli --help
```

## Troubleshooting
- If pip fails, ensure your venv is activated and pip is up-to-date: `python -m pip install --upgrade pip`.
- If cmake cannot find a compiler, install a system compiler (gcc/clang on Unix, MSVC on Windows).
- If GUI does not start, check for missing GUI dependencies in `pt/requirements.txt` and confirm the virtualenv is active.

## Contributing / Notes
- Keep dependencies in the respective requirements files.
- Use the Debug build for development and Release for distribution.

<!-- end -->
