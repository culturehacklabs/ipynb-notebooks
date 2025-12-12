ipynb-notebooks Installation Guide
---

## System Requirements

* **[Python](https://www.python.org/downloads/)** 3.8.x (recommended)
* **[pyenv](https://github.com/pyenv/pyenv)** (recommended for Python version management)
* **System packages**: graphviz, graphviz-dev (for pygraphviz)

## Recommended Installation Method

This guide uses **pyenv** and Python 3.8.18 for maximum compatibility with the legacy packages in this repository.

### Step 1: Install pyenv

**On Linux/macOS:**
```bash
curl https://pyenv.run | bash
```

Then add to your shell configuration (~/.bashrc, ~/.zshrc, etc.):
```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

**On Windows:** Use [pyenv-win](https://github.com/pyenv-win/pyenv-win)

Restart your shell or run `source ~/.bashrc` (or equivalent).

### Step 2: Install Python 3.8.18

```bash
pyenv install 3.8.18
```

This will download and compile Python 3.8.18.

### Step 3: Create Virtual Environment

Navigate to the ipynb-notebooks directory and create the virtual environment:

```bash
cd /path/to/ipynb-notebooks
~/.pyenv/versions/3.8.18/bin/python3.8 -m venv venv38
```

### Step 4: Activate the Environment

**On Linux/macOS:**
```bash
source venv38/bin/activate
```

**On Windows:**
```cmd
venv38\Scripts\activate
```

You should see `(venv38)` in your terminal prompt.

### Step 5: Install System Dependencies

**On Ubuntu/Debian:**
```bash
sudo apt-get update
sudo apt-get install -y build-essential python3-dev graphviz graphviz-dev libgraphviz-dev pkg-config
```

**On macOS (with Homebrew):**
```bash
brew install graphviz
```

**On Arch Linux:**
```bash
sudo pacman -S base-devel graphviz
```

**On Fedora:**
```bash
sudo dnf groupinstall "Development Tools"
sudo dnf install graphviz graphviz-devel
```

These are required for:
- **pygraphviz**: Network visualization
- **MarkovChainRender**: Graph rendering
- Various compiled packages

### Step 6: Install Python Packages

With the virtual environment activated:

```bash
pip install -r requirements_py38.txt
```

This will install all compatible packages including:
- Core data science: numpy, pandas, matplotlib, scipy, scikit-learn
- Deep learning: tensorflow, keras
- NLP: spacy
- Visualization: bokeh, plotly, holoviews, datashader
- Web scraping: newspaper3k, news-please, scrapy
- Network analysis: networkx, pygraphviz
- And many more...

**Note:** The original `requirements.txt` contains legacy packages from 2019-2020 that are incompatible with modern Python. Use `requirements_py38.txt` instead.

### Step 7: Start Jupyter

Launch Jupyter Notebook or JupyterLab:

```bash
# Option 1: Jupyter Notebook (classic interface)
jupyter notebook

# Option 2: JupyterLab (modern interface)
jupyter lab
```

Your browser should open automatically to the Jupyter interface.

## Optional: SpaCy Language Models

For advanced NLP processing with **TextProcessor**, you may need SpaCy language models:

```bash
# English model
python -m spacy download en_core_web_sm

# Spanish model
python -m spacy download es_core_news_sm

# Other languages available at: https://spacy.io/models
```

## Optional: Selenium WebDriver

For web scraping with **Selenium**, install ChromeDriver:

**On Linux:**
```bash
# Download latest version from: https://chromedriver.chromium.org/downloads
wget https://chromedriver.storage.googleapis.com/LATEST_RELEASE
LATEST=$(cat LATEST_RELEASE)
wget https://chromedriver.storage.googleapis.com/${LATEST}/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
sudo mv chromedriver /usr/local/bin/
sudo chmod +x /usr/local/bin/chromedriver
```

**On macOS:**
```bash
brew install chromedriver
```

**On Windows:** Download from [ChromeDriver downloads](https://chromedriver.chromium.org/downloads) and add to PATH.

## Troubleshooting

### Issue: NLTK sqlite3 error

**Problem:** `ModuleNotFoundError: No module named '_sqlite3'`

**Cause:** The pyenv Python 3.8 build was compiled without sqlite3 support.

**Solution:** Most notebooks will work fine. If you need NLTK corpus functionality:
1. Use alternative NLP libraries (spacy, textblob)
2. Reinstall Python 3.8 with sqlite3 support:
   ```bash
   # Install sqlite3-dev first
   sudo apt-get install libsqlite3-dev  # Ubuntu/Debian
   # Then reinstall Python
   pyenv uninstall 3.8.18
   pyenv install 3.8.18
   ```

### Issue: Package dependency conflicts

**Problem:** Warning messages about incompatible package versions

**Cause:** Some packages have overlapping dependency requirements

**Solution:** These warnings are generally harmless. The environment has been tested and core functionality works. If you encounter actual errors, try:
```bash
pip install --upgrade <package-name>
```

### Issue: pygraphviz installation fails

**Problem:** `error: command 'gcc' failed` or similar

**Cause:** Missing system libraries

**Solution:** Install graphviz system packages (see Step 5)

### Deactivating the Environment

When done working:
```bash
deactivate
```

### Removing the Environment

To completely remove the virtual environment:
```bash
rm -rf venv38
```

## Alternative: Using Conda

If you prefer conda over pyenv:

```bash
# Create environment
conda create -n ipynb38 python=3.8

# Activate
conda activate ipynb38

# Install graphviz
conda install -c conda-forge graphviz

# Install Python packages
pip install -r requirements_py38.txt
```
