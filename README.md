# Sphinx Python Documentation Tool Tutorial

## Setup Tasks

  1. Download `astroengisci/csclub-sphinx-demo` from GitHub
  2. Install the Sphinx package in Python according to the installation
     tutorial. 
     http://www.sphinx-doc.org/en/master/usage/installation.html
     
     
     ## Windows
        1. Install Python from here [Python](https://www.python.org/downloads/)
          note: When installing make sure to check the PATH option so that pip can be invoked from the command line.
        2. Open Command Prompt (cmd) and type in:
        
           ``pip install -U sphinx``
           
           if pip is not found reinstall python and check the PATH option
        3. open folder in CMD with CD ex:
          `` cd Downloads\csclub-sphinx-demo\ ``
     
  3. You're going to be using the terminal/command prompt in this 
     presentation. ***STAY CALM, EVERYTHING WILL BE ALRIGHT***
     
## Creating your Sphinx Documentation Build

  1. Create a `/docs` folder in the cloned repository:
  ``mkdir docs``
  
  2. Run `sphinx-quickstart` in the `docs` folder. You can use the
     default values for all except:
     - `autodoc` should be included (select `y`)
     - `viewcode` should be included (select `y`)
     - `makefile` should be included (select `y`)
     - `Windows command file` should be included (select `y`)
  3. Run `make html` or, on Windows, `make.bat html`
  4. Edit `conf.py` to change the source path to the folder containing
     your project's actual code (`..` in this case).
         
```python
import os
import sys
sys.path.insert(0, os.path.abspath('..'))
```
  5. Make a new folder `ref` in `docs`:
  ``mkdir ref``
  6. In the `docs` folder, run `sphinx-apidoc .. -o ref`. This will
     automatically generate reference files for every Python module
     in `..` (the directory above the current one) and stuff them in
     `docs`.
  7. Add `ref/modules` to the table of contents in `index.rst`
  8. Rebuild the documentation.
  ``make html`` or
  ``make.bat html``
  9. You're done!
  Open the ``index.html`` file in ``nbuild\html\`` to see your work!
  
## Your Own Projects
In order to make this kind of documentation with your own Python projects, simply add a docstring inside your functions
and follow the above instructions. 
Ex:

```python
def print_red():
    """Prints the value of Color.RED"""
    print(Color.RED)

def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """
    if imag == 0.0 and real == 0.0:
        return complex_zero
    ...
```

The docstring goes underneath the function declaration and can also be the first statement in the file for the module.
For more information and information on more complex docstrings visit the python website at 
https://www.python.org/dev/peps/pep-0257/

## Other Fun Stuff

### Changing the theme
In `conf.py` change `html_theme` at (likely around line 79) to the
Sphinx theme of your choice.

### Autosummary tables

  1. Edit `conf.py` to include the `sphinx.ext.autosummary` extension.
  2. Edit `ref/modules.rst` to use the `.. autosummary::` directive
     rather than the `.. toctree::` directive. 
     - Add the `:toctree:` option to this directive. 
     - Remove the  `:maxdepth:` option.
