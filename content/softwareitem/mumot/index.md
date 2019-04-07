+++
title = "MuMoT - Multiscale Modelling Tool"
subtitle = ""

# Add a summary to display on homepage (optional).
summary = ""

date = 2019-04-04T08:07:17+01:00
draft = false

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = []

# Is this a featured post? (true/false)
featured = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = []
categories = ["software", "resources"]

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["deep-learning"]` references 
#   `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
# projects = ["internal-project"]

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = ""
  
  preview_only=true
+++

*MuMoT* is a software tool developed at the University of Sheffield as part of the [DiODe project](https://diode.group.shef.ac.uk/). It is open source and can be accessed on the [MuMoT GitHub page](https://github.com/DiODeProject/MuMoT), including full documentation and installation instructions.

MuMoT aims at life scientists/biologists with little mathematical background and engineers designing collective behaviours. It runs inside [Jupyter](https://jupyter.org/) notebooks. MuMoT will be available as Python package that is easy to install on a personal computer and can also be run as server: [launch **example-filled User Manual** now in your web-browser on MyBinder](https://mybinder.org/v2/gh/DiODeProject/MuMoT/master?filepath=docs%2FMuMoTuserManual.ipynb). MuMoT is designed in an object-oriented and modular fashion to make it easy to maintain and to extend functionality.

**Core developers:** James A. R. Marshall, Andreagiovanni Reina, Thomas Bose (all at University of Sheffield)\
**Packaging, documentation, deployment:** Will Furnass (University of Sheffield)\
**Windows compatibility:** Renato P. Vasquez (Princeton University)

{{< figure src="workflow.png" width="600" title="Schematic of a typical workflow in MuMoT." >}}


**MuMoT's core features:**

- **requires simple input:** all functionality is based on providing information about the system as chemical reaction
- allows **model exploration** with simple commands, including **model visualisation** (see stream plot below as an example)
- automatically **generates mathematical equations**, including ODEs, Master equation, system size expansion, Fokker-Planck equation 
(integrates with $\mathsf{\LaTeX}$ to display & export equations)
- allows studying **effects of noise** both analytically and graphically
- allows **interactive analysis** controlled by simple **sliders** using **IPython widgets**
- allows **network analysis** of **agent-based** simulations
- features **stochastic simulations** of the system
- **automated figure formatting** in publication-ready quality

{{< figure src="featured.png" width="600" title="Example input and output in MuMoT: stream plot of honey bee nest-site selection model with two alternatives, A and B ([Seeley et al. (2012)](http://science.sciencemag.org/content/335/6064/108) and [Pais et al. (2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0073216), cf. [our PRE article Reina et al. (2017)](/publication/best-of-n/) ). Fixed points are shown (blue hollow circle: saddle point, green full circle: stable fixed point)." >}}

**Try it out!** The *User Manual* can be accessed (and worked with straight away) via [this link](https://mybinder.org/v2/gh/DiODeProject/MuMoT/master?filepath=docs%2FMuMoTuserManual.ipynb) (it may take a few seconds, or a bit longer, until the server is ready) or you can get started by having a look at [these tutorials](/tutorial/).
