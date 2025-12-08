# Digital Ruins SIM Portfolio

This is a MkDocs-based documentation site showcasing Security Incident Management (SIM) portfolios, governance frameworks, and cybersecurity resources.

## Quick Fix: "Unable to create process" Error

If you're seeing errors like:
- `Fatal error in launcher: Unable to create process using '"C:\Users\marje\AppData\Local\Programs\Python\Python313\python.exe"'`
- `The system cannot find the file specified`

This means pip and other Python packages have broken launchers. **Use these commands instead:**

```bash
# Instead of: pip install
python -m pip install -r requirements.txt

# Instead of: mkdocs serve
python -m mkdocs serve

# Instead of: mkdocs build
python -m mkdocs build
```

**Why this works:** `python -m` runs Python modules directly, bypassing the broken launcher scripts.

For a permanent fix, see the [Troubleshooting](#troubleshooting) section below.

## Prerequisites

- Python 3.8 or higher
- pip (Python package installer)

## Setup Instructions

### 1. Verify Python Installation

Open Command Prompt or PowerShell and check your Python installation:

```bash
python --version
```

If Python is not installed, download it from [python.org](https://www.python.org/downloads/)

### 2. Install Dependencies

Navigate to the project directory and install the required packages:

```bash
pip install -r requirements.txt
```

### 3. Run the Development Server

Start the MkDocs development server:

```bash
mkdocs serve
```

The site will be available at `http://127.0.0.1:8000/`

### 4. Build the Site

To build the static site:

```bash
mkdocs build
```

## Troubleshooting

### Error: "Fatal error in launcher: Unable to create process using..."

This error occurs when Python packages were installed with a Python installation that has since been moved or deleted. The launcher scripts (`.exe` files in `Scripts/`) contain hardcoded paths to the old Python executable.

**Complete Fix (When pip itself is broken):**

1. **First, verify Python works:**
   ```bash
   python --version
   ```
   You should see something like `Python 3.13.x` or similar.

2. **Use Python module syntax to reinstall everything:**
   ```bash
   # Navigate to your project directory
   cd path\to\The_Digital_Ruins-

   # Reinstall pip (fixes the broken pip launcher)
   python -m pip install --upgrade pip --force-reinstall

   # Install project dependencies
   python -m pip install -r requirements.txt
   ```

3. **Test that it works:**
   ```bash
   python -m mkdocs serve
   ```

4. **OPTIONAL - Fix the launchers:**
   After step 2, the regular commands should work again:
   ```bash
   pip --version    # Should work now
   mkdocs serve     # Should work now
   ```

**Quick Workaround (No reinstall needed):**

Always use `python -m` prefix:
- `python -m pip install <package>` instead of `pip install <package>`
- `python -m mkdocs serve` instead of `mkdocs serve`
- `python -m mkdocs build` instead of `mkdocs build`

### Using Virtual Environments (Recommended)

To avoid path issues in the future, use a virtual environment:

1. **Create a virtual environment:**
   ```bash
   python -m venv venv
   ```

2. **Activate the virtual environment:**
   - Windows (Command Prompt):
     ```bash
     venv\Scripts\activate
     ```
   - Windows (PowerShell):
     ```bash
     venv\Scripts\Activate.ps1
     ```
   - Linux/Mac:
     ```bash
     source venv/bin/activate
     ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run MkDocs:**
   ```bash
   mkdocs serve
   ```

## Project Structure

```
The_Digital_Ruins-/
├── docs/               # Documentation source files
│   ├── index.md       # Homepage
│   ├── about.md       # About page
│   ├── governance/    # Governance SIMs
│   ├── mfa/           # MFA documentation
│   ├── playbooks/     # Security playbooks
│   └── Blog/          # Blog posts
├── mkdocs.yml         # MkDocs configuration
└── requirements.txt   # Python dependencies
```

## Contributing

When making changes:
1. Test locally with `mkdocs serve`
2. Ensure all documentation renders correctly
3. Check for broken links
4. Build the site with `mkdocs build` to verify no errors

## License

See [LICENSE](LICENSE) file for details.

## Contact

- Website: [thedigitalruins.com](https://thedigitalruins.com)
- GitHub: [@marjeanm](https://github.com/marjeanm)
- Blog: [blog.thedigitalruins.com](https://blog.thedigitalruins.com)
