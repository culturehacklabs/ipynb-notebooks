ipynb-notebooks
---

Collection of IPython (Jupyter/Colab) notebooks for collecting, streaming, scraping and processing data.

### Requirements

* **[Python](https://www.python.org/downloads/)** (3.8.x recommended)
* [pyenv](https://github.com/pyenv/pyenv) (recommended for managing Python versions)
* [virtualenv](https://pypi.org/project/virtualenv/) or venv (built-in with Python)

### Installation

#### Quick Start (Recommended)

If you already have Python 3.8 installed via pyenv:

```bash
# Create virtual environment with Python 3.8
~/.pyenv/versions/3.8.18/bin/python3.8 -m venv venv38

# Activate the virtual environment
source venv38/bin/activate

# Install all dependencies
pip install -r requirements_py38.txt
```

#### From Scratch

1. **Install pyenv** (if not already installed):
   ```bash
   curl https://pyenv.run | bash
   ```

2. **Install Python 3.8.18**:
   ```bash
   pyenv install 3.8.18
   ```

3. **Create virtual environment**:
   ```bash
   ~/.pyenv/versions/3.8.18/bin/python3.8 -m venv venv38
   ```

4. **Activate environment and install packages**:
   ```bash
   source venv38/bin/activate
   pip install -r requirements_py38.txt
   ```

5. **Start Jupyter**:
   ```bash
   jupyter notebook
   # or
   jupyter lab
   ```

#### What's Installed

The environment includes:
- **Data Science Stack**: numpy, pandas, matplotlib, scipy, scikit-learn, seaborn, statsmodels
- **Deep Learning**: tensorflow, keras
- **NLP**: spacy (3.3.3)
- **Visualization**: bokeh, plotly, holoviews, datashader
- **Network Analysis**: networkx, pygraphviz
- **Web Scraping**: beautifulsoup4, newspaper3k, news-please, scrapy
- **Jupyter**: Full Jupyter notebook/lab stack

#### Known Issues

- **NLTK/sqlite3**: The pyenv Python 3.8 build may lack sqlite3 support, affecting direct nltk corpus usage. Most notebooks will work fine with alternative approaches.
- **Legacy requirements.txt**: The original `requirements.txt` file contains packages from 2019-2020 that are incompatible with modern Python. Use `requirements_py38.txt` instead.

For detailed troubleshooting, see [INSTALL.md](INSTALL.md).

### Tools

* DataFrameTools
* LinkThings
* MarkovChainRender
* MediaCollector
* NetworkPlot
* PyCluster
* PyPhiNetwork
* SubgraphManipulator
* Text2WordCloud
* TextProcessor
* TwitterCollector
* TwitterProcessor
* TwitterSearch

Each bundled notebook requires the standalone tool as listed above.

For more information on each tool, please refer to their own repositories.
