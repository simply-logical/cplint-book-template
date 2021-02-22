[![Licence][licence-badge]][licence-link]
[![Online][online-badge]][online-link]

[licence-badge]: https://img.shields.io/github/license/simply-logical/cplint-book-template.svg
[licence-link]: https://github.com/simply-logical/cplint-book-template/blob/master/LICENCE
[online-badge]: https://img.shields.io/badge/read-online-green.svg
[online-link]: https://cplint-template.simply-logical.space/

# Interactive cplint Book Example #

This repository holds a [*Jupyter Book*] template for building interactive
[cplint] books based on [SWISH].
The cplint support is enabled with our custom [`sphinx-prolog`] extension.
The built book is hosted on *GitHub Pages* and is available under
<https://cplint-template.simply-logical.space>.
**This webpage describes the process of building interactive cplint content
with the aforementioned technology stack.**

## Building the Book ##

1. Pull the book repository
   ```bash
   git clone https://github.com/simply-logical/cplint-book-template.git

   cd cplint-book-template
   ```
2. Install [*Jupyter Book*](https://pypi.org/project/jupyter-book/) with the
   [`sphinx-prolog`](https://pypi.org/project/sphinx-prolog/) extension
   ```bash
   pip install -r requirements.txt
   ```
3. Build the book
   ```bash
   jb build .
   ```
4. Open the html build
   ```bash
   open _build/html/index.html
   ```
   or run it as a server
   ```bash
   python -m http.server --directory _build/html
   open http://localhost:8000
   ```

[*Jupyter Book*]: https://jupyterbook.org/
[cplint]: https://friguzzi.github.io/cplint/_build/html/
[SWISH]: http://cplint.ml.unife.it/
[`sphinx-prolog`]: https://github.com/simply-logical/sphinx-prolog
