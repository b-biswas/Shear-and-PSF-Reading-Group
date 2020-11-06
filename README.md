# Shear Book

Welcome to the Shear and PSF reading group repository!

The following steps will help you get set up to contribute to the book.

## Requirements

To build the book you will need the following packages.

- [numpy](https://numpy.org/)
- [scipy](https://www.scipy.org/)
- [matplotlib](https://matplotlib.org/)
- [Jupyter](https://jupyter.org/)
- [Jupyter Book](https://jupyterbook.org/intro.html)

You can install them as follows

```bash
$ pip install -r requirements.txt
```

alternatively you can build the `shear` conda environment.

```bash
$ conda env create -f environment.yml
$ conda activate shear
```

## Building

To build the book locally run

```bash
$ jupyter-book build shearbook
```

in the root of the directory. This will build the HTML files and provide a link to the `index.html` so that you can view the book in your browser.

## Cleaning

Similarly, to clean the locally builded files run

```bash
$ jupyter-book clean shearbook
```

in the root directory. This will remove the `_build` directory.


## Adding Content

### New Pages

To create a new page simply write a new markdown file or Jupyter notebook and the file name to the `_toc.yml` file to specify where the page should be included in the book.

*e.g.* For a file called `new_content.md` you would add

```yaml
- file: new_content
```

to the appropriate section of `_toc.yml`.

See the [Jupyter Book documentation](https://jupyterbook.org/content/content-blocks.html) for tips on including special content blocks, equations and references.

### Bibliography

To add a bibliography page:

1. Create a new `.bib` file with standard BibTeX content.  
> Be sure to prefix the file name with `z_` as this will ensure that the file is sourced after the content files. This makes it possible to cite papers across multiple pages.

2. Create a markdown file ending with `-ref.md` (for the sake of consistency) and include the following.

````markdown
# References

```{bibliography} _bibliography/z_<FILE_NAME>.bib
:all:
```
````

where `<FILE_NAME>` is the name of your `.bib` file.

### Interactive Notebooks

If you prepare an additional interactive version (*i.e.* with widgets) of a given notebook you should name it `<FILE_NAME>_interact.ipynb`. This file should not be included in `_toc.yml`. Instead you can include the following in your standard notebook.

```python
from IPython.display import Markdown as md
from interact import get_url, binder_badge

# Provide binder badge
md('<a href="{}" target="_blank"><img src="{}"></a>'.format(get_url('<FILE_NAME>'), binder_badge))
```

This will embed a Binder badge that links to the interactive notebook.
