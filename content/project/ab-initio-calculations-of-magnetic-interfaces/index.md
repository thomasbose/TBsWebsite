+++
title = "Ab-initio Calculations of Magnetic Interfaces"
date = 2016-12-01
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Computational Magnetism"]

# Project summary to display on homepage.
summary = ""

# Slides (optional).
#   Associate this page with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references 
#   `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides = ""

# Optional external URL for project (replaces project detail page).
external_link = ""

# Links (optional).
url_pdf = ""
url_code = ""
url_dataset = ""
url_slides = ""
url_video = ""
url_poster = ""

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
# links = [{icon_pack = "fab", icon="twitter", name="Follow", url = "https://twitter.com"}]

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

Fe/MgO-interfaces in magnetic multilayer structures are of great importance in magnetic material science with regard to promising applications and devices. In our present investigation we are looking at basic properties of Fe/MgO-slab geometries.

{{< figure src="featured.png" width="400" title="Illustration of MgO and Fe unit cells." >}}

Within a systematic study we investigated the effect of altering the Fe-layer thickness on quantities like layer-resolved magnetic moments, charge distributions and magnetocrystalline anisotropy. We made use of the SIESTA package which is based on density functional theory (DFT) and utilizes pseudo potentials and localized atomic orbitals as basis set. Our DFT-based calculations were performed within the generalized gradient approximation (GGA) for the exchange correlation potential. Typical calculations included the construction of the system under study and its relaxation to find the final atomic coordinates. Subsequent, information about energies, atomic magnetic moments and charges could be obtained directly from the SIESTA output. In particular, the magnetocrystalline anisotropy energy which is an important quantity regarding magnetic data storage devices could be calculated as well.

**Representative publication:** 

- [T. Bose, R. Cuadrado, R.F.L. Evans, R.V. Chepulskii, D. Apalkov and R.W. Chantrell
Journal of Physics: Condensed Matter **28**, 156003 (2016)](https://iopscience.iop.org/article/10.1088/0953-8984/28/15/156003)
