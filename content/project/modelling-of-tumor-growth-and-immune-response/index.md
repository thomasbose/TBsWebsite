+++
title = "Modelling Of Tumor Growth And Immune Response"
date = 2012-12-01
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Mathematical Biology"]

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
  preview_only = true
+++

Tumor growth has become an important issue in medicine, biology and physics. Thus, understanding of cancer growth mechanisms is necessary to develop relevant strategies against this disease. It is widely accepted that the immune system plays an important role during tumor evolution and therapy.

Introduced in the early 1900's and again suggested in the middle of the 20th century there is the hypothesis that the immune system is able to detect and to eliminate nascent transformed cells. During the last decade the concept of the immune surveillance of the body was emphasized again, supported by experimental results verifying the immune surveillance hypothesis. Later on, the immune surveillance concept was modified and is now known as 'immunoediting' which reflects the dual role of the immune response during the early stages of cancer growth. The term immunoediting means both the ability of the immune system to destroy the tumor cells and a possible sculpting of the cancer cells. As the result all cells with a low immunogenicity will survive and begin to proliferate which is often referred to as escape of the tumor from the control of the immune system.

{{< figure src="featured.png" width="400" title="Schematic of tumor-immune cells interaction after introducing randomness." >}}

Here, we investigate tumor evolution in presence of an intact immune system taking further into account stochasticity to demonstrate that tumor-immune cell reactions can be induced by stochastic forces. To that purpose we consider three types of cells:

- tumor cells the density of which is denoted by $x(t)$,
- effector cells with density $y(t)$, and
- tumor-detecting cells with density $z(t)$.

Whereas tumor-detecting cells are only able to recognize tumor cells but not to kill them, the effector cells have the ability to eliminate tumor cells.

After introducing a system of coupled differential equations describing the interaction between different cell species we find that tumor extinction is only observed in the presence of randomness and noise. The mutual interaction of the different kinds of cells is shown in the figure. The quantities in the brackets are mean values derived by a probabilistic treatment of the equations describing the stochastic dynamic system. The parameters of the noise correlation function have a great impact on the behavior of the coupled tumor-immune cell interaction, especially on the response of the immune system. In particular we show that the auto-correlation time and the cross-correlation strength are able to control the evolution of the tumor. More precise, these two quantities discriminate whether the system tends to tumor suppression, tumor progression or tumor dormancy. The assistance of inevitable noisy influences seems to play a crucial role during cancer genesis and growth in humans. The involved random forces may be originated in the tumor as well as inside the immune system and can even interact mutually which is manifested in the cross-correlation. Our model should be considered as an attempt toward a more detailed analysis of tumor-immune systems. It elucidates that noise plays an decisive role in such systems.

**Representative publications:** 

- [T. Bose and S. Trimper, Physical Review E **84**, 021927 (2011)](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.84.021927)
- [T. Bose and S. Trimper, Physical Review E **79**, 051903 (2009)](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.79.051903)
