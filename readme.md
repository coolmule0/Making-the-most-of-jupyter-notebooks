# Making The Most Of Jupyter Notebooks

A talk given at Lunchbytes on 2020-Oct-07. A ten minute talk on extentions and libraries available to Jupyter Notebooks. Part of an hour long session on "The Pros and Cons of Jupyter Notebooks". [See more information here](https://rse.shef.ac.uk/events/lunchbytes-2020-10-07.html)

[View a live notebook here](https://hub.gke2.mybinder.org/user/coolmule0-makin-pyter-notebooks-gp5obs8v/notebooks/Making%20the%20most%20out%20of%20Jupyter%20Notebooks.ipynb) or here: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/coolmule0/Making-the-most-of-jupyter-notebooks/master)

[View a static version of the slides here](https://coolmule0.github.io/talks/JupyterNotebooks/Making_the_most_out_of_Jupyter_Notebooks.html)

## Running the Slideshow from Source

Two options are provided to create the slides. One is through [binder](https://mybinder.org/), the other is from source.

### Running The Slideshow in Binder

A cloud image running this notebook is available [on binder](https://mybinder.org/v2/gh/coolmule0/Making-the-most-of-jupyter-notebooks/master). Ensure "Split Cells Notebook" extention is active by selecting Nbextentions -> Split Cells notebook -> Enable. You may need to disable configuration for nbextentions by unticking the top tickbox.

View the notebook through Files->Making the most out of Jupyter Notebooks.ipynb. Run the code required through cell->Run all. To view the slides select the "Enter/Exit RISE slideshow" button along the top toolbars (should be next to the download button). If any cells do not appear correct within the slideshow re-run the cell within the slideshow with shift+enter.

### Running The Slideshow From Source Code

Download this repository and set up the dependencies using `conda`: 

`conda env create -f environment.yml`

Ensure "Split Cells Notebook" extention is active by selecting Nbextentions -> Split Cells notebook -> Enable. You may need to disable configuration for nbextentions by unticking the top tickbox.

View the notebook through Files->Making the most out of Jupyter Notebooks.ipynb. Run the code required through cell->Run all. To view the slides select the "Enter/Exit RISE slideshow" button along the top toolbars. If any cells do not appear correct within the slideshow re-run the cell within the slideshow with shift+enter.