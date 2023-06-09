(sec:intro)=
# Interactive cplint Book Example #

## About ##
This online book describes the process of building online interactive [cplint]
materials using [SWISH].
It is hosted on [*GitHub Pages*], and built with [*Jupyter Book*] and our
custom [`sphinx-prolog`] extension.
The source of this book can be found in the
[simply-logical/cplint-book-template] GitHub repository, which can also serve
as a template and a starting point for building your own book.

:::{tip}
This template is a proof-of-concept for embedding interactive [cplint]-based
[SWISH] code boxes using the [`sphinx-prolog`] Jupyter Book extension.
This extension was primarily developed for [SWI Prolog] and the original
[Prolog SWISH].
The full template and a user guide describing how to use this content
creation system can be found at <https://book-template.simply-logical.space/>,
with its source hosted in the [simply-logical/prolog-book-template] GitHub
repository.
**The main difference between the SWI Prolog and the cplint version is the
SWISH URL configured with the `sp_swish_url` parameter held under the
`sphinx.config` key in the [`_config.yml`] file.**
```yaml
sphinx:
  config:
    # Configure sphinx-prolog <https://github.com/simply-logical/sphinx-prolog>
    sp_swish_url: https://cplint.ml.unife.it/
```
To see the full potential of the `sphinx-prolog` extension, have a look at
the part of its documentation describing [interactive SWISH boxes].
:::

## Building the Book ##
To build this book you need two Python packages: `jupyter-book` and
`sphinx-prolog`.
You can either install them manually
```bash
pip install "jupyter-book>=0.10.0"
pip install "sphinx-prolog>=0.5"
```
or by using our `requirements.txt` file, i.e.,
`pip install -r requirements.txt`.
Then, the book can be built with `jb build .`.

:::{note}
For more details about installing necessary dependencies and building this
book see the [`README.md`] file included in the [GitHub repository] that
holds the source of this book.
:::

[cplint]: https://friguzzi.github.io/cplint/_build/html/
[SWISH]: https://cplint.ml.unife.it/
[SWI Prolog]: https://www.swi-prolog.org/
[Prolog SWISH]: https://swish.swi-prolog.org/
[*GitHub Pages*]: https://pages.github.com/
[*Jupyter Book*]: https://jupyterbook.org/
[`sphinx-prolog`]: https://github.com/simply-logical/sphinx-prolog
[GitHub repository]: https://github.com/simply-logical/cplint-book-template
[`README.md`]: https://github.com/simply-logical/cplint-book-template#building-the-book
[simply-logical/cplint-book-template]: https://github.com/simply-logical/cplint-book-template
[simply-logical/prolog-book-template]: https://github.com/simply-logical/prolog-book-template
[`_config.yml`]: https://github.com/simply-logical/cplint-book-template/blob/master/_config.yml
[interactive SWISH boxes]: https://book-template.simply-logical.space/src/text/sphinx_prolog_swish.html
