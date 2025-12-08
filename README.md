# Digital Ruins SIM Portfolio

This is a MkDocs-based documentation site showcasing Security Incident Management (SIM) portfolios, governance frameworks, and cybersecurity resources.

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

This error occurs when Python packages were installed with a Python installation that has since been moved or deleted. The launcher scripts contain hardcoded paths to the old Python executable.

**Solution:**

1. **Uninstall the affected packages:**
   ```bash
   pip uninstall mkdocs mkdocs-material pymdown-extensions
   ```

2. **Reinstall the packages with your current Python installation:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Alternative: Use Python module syntax:**
   Instead of running `mkdocs serve`, use:
   ```bash
   python -m mkdocs serve
   ```

4. **If pip itself is broken:**
   ```bash
   python -m pip install --upgrade pip
   python -m pip install -r requirements.txt
   ```

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
