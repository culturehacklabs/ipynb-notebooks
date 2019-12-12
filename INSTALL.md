ipynb-notebooks
---

### Requirements

* **[Python](https://www.python.org/downloads/)** (3.6.8+)
* **[node.js](https://nodejs.org/en/)** (11.15.0+)
* **[npm](https://www.npmjs.com/get-npm)** (6.9.0+)
* [virtualenv](https://pypi.org/project/virtualenv/) (option 1)
* [conda](https://docs.conda.io/en/latest/miniconda.html) (option 2)

The commands below assume your Python3 binary launcher is called with ```python3```.

If using the default ```py``` launcher on Windows, replace it with ```py -3``` when executing the lines below.

### 1/5: Create the environment

In order to avoid conflicting library versions, it is advised to create a new virtual environment:

* Using **virtualenv** (option 1): ```python3 -m virtualenv chn --python=python3```

* Using **conda** (option 2): ```conda create -n chn python=3```

#### Activate the environment

Ensure you activate your newly created environment before making any further changes:

* Using **virtualenv** (Linux): ```source chn/bin/activate```

* Using **virtualenv** (Windows): ```chn/bin/activate```

* Using **conda**: ```conda activate chn```

### 2/5: Install prerequesites (Linux)

Make sure to install the required development packages on Linux:

* On **Ubuntu/Debian**: ```sudo apt install build-essential python3-dev python3-tk```

* On **Arch/Antergos/Manjaro**: ```sudo pacman -S base-devel tk```

* On **Fedora**: ```sudo yum groupinstall "Development Tools"```

* On **Mageia**: ```sudo urpmi development-libs development-tools```

* On **SUSE**: ```sudo zypper install -t pattern devel_C_C++```

#### 3/5: Install compilers (conda)

If using **conda**, the following packages may be needed for compiling libraries:

* On **Linux**: ```conda install gcc_linux-64 gxx_linux-64 gfortran_linux-64```

* On **Mac**: ```conda install clang_osx-64 clangxx_osx-64 gfortran_osx-64```

On **Windows** the Python ecosystem uses the Microsoft Visual C compiler (VisualStudio).

### 4/5: Install libraries (Python)

To install the required Python libraries from PyPI in your environment, run:

* ```pip install -r requirements.txt```

**Note:** alternatively, some listed packages are also available for installing from conda repositories.

### 5/5: Download chrome driver (Selenium)

To start crawling data with **[Selenium](https://www.seleniumhq.org/)**, it is required to install the binary chrome driver in your system.

On Linux, run the following commands in order to make it available system-wide:

```
wget https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
mv chromedriver /usr/bin/chromedriver
```

**Note:** you might check the most recent version released **[here](https://chromedriver.storage.googleapis.com/index.html)** before downloading.