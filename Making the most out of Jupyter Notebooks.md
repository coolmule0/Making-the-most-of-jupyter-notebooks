---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.2'
      jupytext_version: 1.6.0
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

<!-- #region slideshow={"slide_type": "slide"} -->
# Making the most out of Jupyter Notebooks
Extentions and magic

2020-10-06

John Charlton, Research Software Engineer, RSE Team (pronoun: he)
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
# Notebooks are good
- Great for quickly prototyping
- Easy to explore data
- The format lends itself to educating

# Notebooks are bad
- Not great for large, extended pieces of code
- Good coding practices can be hard to apply
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "fragment"} -->
- Can lessen the downsides & strengthen the upsides with extentions
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
# Version Control 

`!pip install jupytext --upgrade`

`.ipynb` file format uses `Json` underneath

Able to save as `.md`, `.rmd`, `.html` and more

Edit file in favourite IDE, refresh page and see results

Sensible version control
    e.g. diff, merge
    
Also load plain text files into notebooks


<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
# Pytests
`!pip install nbval`

Ensure that the notebook is behaving as expected and changes to the underlying source code have not affected the results

Runs the notebook, and compares the output with those stored in the .ipynb file.

Can validate this file!
`pytest --nbval *.ipynb
<!-- #endregion -->

```python
#!pytest --nbval "Making the most out of Jupyter Notebooks.ipynb"
```

<!-- #region slideshow={"slide_type": "slide"} -->
# Slideshows
The power of notebooks with the display capabilities of slides.
Choose what to show and hide from the notebooks.

`View->Cell Toolbar->Slideshow` to bring up slide control options

## Jupyter Notebook's buit-in slides
`jupyter nbconvert *.ipynb --to slides --post serve`
Run from commandline within folder. `nbconvert` transforms notebooks into a static format
- Generate static html pages locally at port 8000
- Geneates a .html file within the directory


## Rise
`pip install rise`
- Run code without exiting the slideshow
- Uses reveal.js, a javascript presentation framework
- Powering this presentation
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "notes"} -->
Make changes to the md document in an ide, reload the page and show the changes
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
# Widgets
`!pip install ipywidgets`

Powerful way to interact with code

Sliders, tickboxes, textboxes, colour pickers, tabs...
<!-- #endregion -->

```python slideshow={"slide_type": "notes"}
# Set the backend for an interactive plot
%matplotlib inline

import matplotlib.pyplot as plt
import numpy as np


def plot_func(freq, amplitude, graph_type):
    
    x = np.linspace(0, 2*np.pi)
    if graph_type == "sin":
        y = amplitude * np.sin(x * freq)
    elif graph_type == "cos":
        y = amplitude * np.cos(x * freq)
    elif graph_type == "tan":
        y = amplitude * np.tan(x * freq)
    else:
        y = x
    axes = plt.gca()
    axes.set_ylim([-3,3])
    line, = plt.plot(x, y)

```

```python slideshow={"slide_type": "fragment"}
from ipywidgets import interact, fixed
import ipywidgets as widgets

# def plot_func(freq, amplitude, graph_type) = ...

interact(plot_func, freq = (1,5,0.5), amplitude = (1,5,0.5), graph_type = widgets.Dropdown(options=['sin', 'cos', 'tan']))


```

<!-- #region slideshow={"slide_type": "subslide"} -->
# Widgets Continued
<!-- #endregion -->

```python slideshow={"slide_type": "notes"}
#def sierpinski_recursive(level, triangle):
    
```

```python slideshow={"slide_type": "-"}
play = widgets.Play(
    value=2,
    min=0,
    max=50,
    step=1,
    interval=500
)

interact(plot_func, freq = play, amplitude=fixed(1), graph_type=fixed("sin"))

```

```python slideshow={"slide_type": "notes"} cell_style="center"
# backend for following qgrid example
import pandas as pd
from datetime import time

# some columns should be datetime format
parse_dates = ['date', 'arrival', 'recordedarrivaltime']

df = pd.read_csv("df_example.csv", parse_dates=parse_dates)

```

<!-- #region slideshow={"slide_type": "slide"} cell_style="split" -->
# Qgrid
`pip install qgrid`

Powerful way to explore DataFrames

scrolling, sorting, filtering

nb: using "Split Cells Notebook" extention to display 2 cells horizontally
<!-- #endregion -->

```python cell_style="split"
import qgrid

qgrid_widget = qgrid.show_grid(df, show_toolbar=True)
qgrid_widget

# plt.plot() scatter of df data
#matplotlib extentions/theming?
```

```python
%matplotlib nbagg
import matplotlib.pyplot as plt

n = 50

qgrid_df = qgrid_widget.get_changed_df()
x = qgrid_df.index
y = qgrid_df['C']

fig, ax = plt.subplots()
fit = np.polyfit(x, y, deg=1)
line, = ax.plot(x, fit[0] * x + fit[1], color='red')
scatter, = ax.plot(x,y,ms=8,color='b',marker='o',ls='')

def handle_filter_changed(event, widget):
    qgrid_df = qgrid_widget.get_changed_df()
    x = qgrid_df.index
    y = qgrid_df['C']
    fit = np.polyfit(x, y, deg=1)
    line.set_data(x, fit[0] * x + fit[1])
    fig.canvas.draw()
    scatter.set_data(x, y)
    fig.canvas.draw()

qgrid_widget.on('filter_changed', handle_filter_changed)
```

<!-- #region slideshow={"slide_type": "slide"} -->
# Conclusions
There are numerous different extentions and alterations that
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "notes"} -->
What works on:
Jupyter notebooks, jupyterlab, R notebook, google collaborate?
<!-- #endregion -->

<!-- #region slideshow={"slide_type": "slide"} -->
# Collection of extentions
`pip install jupyter_contrib_nbextensions`

<!-- #endregion -->

<!-- #region slideshow={"slide_type": "notes"} -->
# Theming
`pip install jupyterthemes`
Add unique look for code highlighting AND document colour
- Includes plots (matplotlib) and dataframe styling
Helpful for coding and presenting
Appearance is kept when converting notebook to static content
<!-- #endregion -->

```python
 Jupyter, R Markdown, Apache Zeppelin, Spark Notebook 
```
