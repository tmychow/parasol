# alloypress

This is my Python static site generator. I use it for [my personal website](https://tmychow.com).

## Package

```
alloypress
├── LICENSE                    ┐ 
├── README.md                  │ Package documentation
├── .gitignore                 ┘
├── pyproject.toml             ┐ 
├── src                        │
│   └── alloypress             │ Package source code, metadata,
│       ├── __init__.py        │ and build instructions 
│       └── ssg.py             │
│       └── stylesheet.py      ┘
└── tests                      ┐
    └── raw                    │
        └── test.md            │ Package tests
    └── run.py                 │ 
    └── ...                    ┘ 
```

## Approach 

The high-level approach of `alloypress` is to do everything on the server-side with HTML and CSS, serving static files only and rendering nothing client-side.

- Takes every `.md` file from `./raw` and generates the HTML in `./`
- Takes a path to the local stylesheet as an argument
- Gnerates the default stylesheet as `./style.css` if none is provided

## Features

- Supports Jon Gruber's original [Markdown syntax](https://daringfireball.net/projects/markdown/syntax) via `markdown`
- Supports LaTeX via `latex2mathml` inside `$` and `$$` delimiters
- Supports syntax highlighting for Python via `pygments`
- Supports sidenotes (displayed inline for narrow devices)
- See `./tests/raw/test.md` for an example of all the features

## To Be Implemented

- Automatically generating an index page for every subfolder, with links to all the posts in that folder

## Usage

Install via `pip install alloypress` and run a script with the following code in the root directory of your site:

```
from alloypress import generate

generate()
``````

This code is also in `./tests/run.py`, which you can run to see the output of `alloypress` on the example file `./tests/raw/test.md`.