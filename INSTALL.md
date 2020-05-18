chn-tools
---

### Requirements

* **[Python](https://www.python.org/downloads/)** (3.6.8+)
* [virtualenv](https://pypi.org/project/virtualenv/) (option 1)
* [conda](https://docs.conda.io/en/latest/miniconda.html) (option 2)

The commands below assume your Python3 binary launcher is called with `python3`.

If using the default `py` launcher on Windows, replace it with `py -3` when executing the lines below.

### 1/5: Create the environment

In order to avoid conflicting library versions, it is advised to create a new virtual environment:

* Using **virtualenv** (option 1): `python3 -m virtualenv chn --python=python3`

* Using **conda** (option 2): `conda create -n chn python=3.6`

#### Activate the environment

Ensure you activate your newly created environment before making any further changes:

* Using **virtualenv** (Linux): `source chn/bin/activate`

* Using **virtualenv** (Windows): `chn/bin/activate`

* Using **conda**: `conda activate chn`

### 2/5: Install compilers (conda)

If using **conda**, the following packages may be needed for compiling libraries:

* On **Linux**: `conda install gcc_linux-64 gxx_linux-64 gfortran_linux-64`

* On **Mac**: `conda install clang_osx-64 clangxx_osx-64 gfortran_osx-64`

On **Windows** the Python ecosystem uses the Microsoft Visual C compiler (VisualStudio).

### 3/5: Install prerequesites (Linux)

Make sure to install the required development packages on Linux:

* On **Ubuntu/Debian**: `sudo apt install build-essential python3-dev python3-tk`

* On **Arch/Antergos/Manjaro**: `sudo pacman -S base-devel tk`

* On **Fedora**: `sudo yum groupinstall "Development Tools"`

* On **Mageia**: `sudo urpmi development-libs development-tools`

* On **SUSE**: `sudo zypper install -t pattern devel_C_C++`

#### Additional requirements

The following libraries may be required for **MarkovChainRender** (Ubuntu/Debian; others will differ):

* `sudo apt-get install python3-dev graphviz graphviz-dev libgraphviz-dev pkg-config`

Natural language processing with **TextProcessor** requires **[SpaCy models](https://spacy.io/usage/models)** and can be installed automatically on execution based on language detection, or manually by running e.g. for english:

* `python3 -m spacy download en`

Additional requirements for text conversion are also needed by **[textract](https://textract.readthedocs.io/en/latest/installation.html)** as per input file extension.

### 4/5: Install libraries (Python)

To install the required Python libraries from PyPI in your environment, run:

* `pip install -r requirements.txt`

**Note:** alternatively, some listed packages are also available for installing from **conda** repositories.

### 5/5: Download chrome driver (Selenium)

To start crawling data with **[Selenium](https://www.seleniumhq.org/)**, it is required to install the binary chrome driver in your system.

On Linux, run the following commands in order to make it available system-wide:

```
wget https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
mv chromedriver /usr/bin/chromedriver
```

**Note:** you might check the most recent version released **[here](https://chromedriver.storage.googleapis.com/index.html)** before downloading.

### Build and setup package (optional)

Get all required libraries and install in your environment running:

* `python3 setup.py install`

### Binary launcher (optional)

For convenience, a symbolic link or alias to the launcher can optionally be added to your system. To do so, run the command below on your terminal of choice (replace `/path/to/chn-tools.py` accordingly):

* On **Linux/Mac**: `sudo ln -s /path/to/chn-tools.py /usr/local/bin/chn-tools`

* On **Cmder** (Windows): `alias chn-tools=python3 X:/path/to/chn-tools.py $*`

* On **Git Bash** (Windows): `echo "alias chn-tools=python3 X:/path/to/chn-tools.py" >> "${HOME}/.profile`

This will link the **chn-tools.py** script file as `chn-tools`. Restart your terminal for changes to take in effect.

**Note:** you may also choose to link the script for launch with the default Command Prompt for Windows by adding a custom system environment variable.

### Cleanup

To remove build files and remaining data from previous executions, run:

* `python3 setup.py clean`
