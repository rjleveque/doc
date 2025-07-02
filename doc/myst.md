
(myst)=
# Using Myst for our Documentation

Experimenting with using
[Myst](https://myst-parser.readthedocs.io/en/v0.17.2/index.html)
rather than reStructured Text in the clawpack docs. The source for this
page in in `myst.md`, which can be viewed by clicking on `Source .rst` on the
left menu even though it's not a `.rst` file.


Including
```
    extensions = ["myst_parser"]
```
in `conf.py` allows including `.md` files along with `.rst` files in the
documentation.  


Myst has many cool features, e.g.

- You can cite references from `references.bib` and refer to
  {cite:t}`mandli2016clawpack` or {cite:p}`clawpack`.
  Note that hovering over a reference shows the citation, while clicking
  on it takes you to the [Myst biblography](#bibliography)
  as defined in `bibliography.md`.
  Getting this to work requires including `'sphinxcontrib.bibtex'` in
  the list of `exensions` in `conf.py`, and also including the line
  ```
  bibtex_bibfiles = ['references.bib']
  ```

- Equations are easy to include, both inline as {math}`\int_0^\pi e^x\,dx = e^{\pi} - 1` or
  displayed and labeled for cross-referencing:
  ```{math}
  :label: claw-with-source
  q_t(x,t) + f(q(x,t))_x = \psi(x,t)
  ```
  This equation is labeled as equation [](#claw-with-source).

## Admonitions

Various admonitions are defined, e.g.

:::{tip}
You can refer to other myst files, e.g. this file is [](#myst).
:::

:::{warning}
But I don't yet know how to refer to sections of `.rst` files, since  e.g.
:ref:`geoclaw` doesn't work.
:::


:::{versionchanged} 5.12.0
See the [release notes](https://www.clawpack.org/release_5_12_0.html).
(This is the `versionchanged` admonition.)
:::

## Jupyter notebooks

Still need to figure this out.  See [myst-nb](https://myst-nb.readthedocs.io/en/latest/index.html).

:::{caution}
Need to now include
```
    extensions = ["myst_nb"]
```
in `conf.py` (which also loads `myst_parser`). But when I do so, I get
the exception
`jupyter_client.kernelspec.NoSuchKernel: No such kernel named python2`.
