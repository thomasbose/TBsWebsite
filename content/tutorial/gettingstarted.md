+++
title = "Getting started"

date = 2019-04-01

draft = false  # Is this a draft? true/false
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

# Add menu entry to sidebar.
linktitle = "Getting started"
[menu.tutorial]
  parent = "Introduction to MuMoT"
  weight = 2
+++

## Working with MuMoT <a class="tocSkip">

MuMoT runs inside [Jupyter notebooks](http://jupyter.org). Jupyter needs to be installed on your machine ([see installation instructions](https://jupyter.readthedocs.io/en/latest/install.html)). Basic information on working with Jupyter notebooks can be found [here](http://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Notebook%20Basics.html). 

The next step before you can work with MuMoT is to follow [MuMoT's installation instructions](https://mumot.readthedocs.io/en/latest/getting_started.html) to install this Python package.

Now you are ready to import the MuMoT package into your notebook using `import mumot` and to try it out!


```python
import mumot
mumot.about()
```

    Created `%%model` as an alias for `%%latex`.
    Multiscale Modelling Tool (MuMoT): Version 1.0.0
    Authors: James A. R. Marshall, Andreagiovanni Reina, Thomas Bose
    Documentation: https://mumot.readthedocs.io/

It is a good sign if you have seen the message ``Created `%%model` as an alias for `%%latex``. Then everything went well with the installation and the import of MuMoT. As you can see, the `about()` command gives some further details.

## Defining your first model <a class="tocSkip">

MuMoT models are defined using the `%%model` keyword within a cell. The syntax is meant to be intuitive and all processes are described as chemical reaction-like expressions, including the *reactants* and *reaction rates*. Here is an example:

`A + A -> A + U: s`

where two particles of type $A$ interact, and one changes to type $U$, at rate $s$.

This means, reaction rules are quite general. Hence, MuMoT may be used to study a variety of different models that are based on interacting particels or agents. Our first model will be based on signalling behaviour observed in honeybee swarms, as described and modelled in [Seeley *et al.* (2012)](http://science.sciencemag.org/content/335/6064/108) and [Pais *et al.* (2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0073216)).

The `$` at the start and end of the input cell below just allow us to use [LaTeX](https://en.wikipedia.org/wiki/LaTeX) codes for our state and rate labels, allowing us to use  letters from different alphabets, such as Greek, and other nice formatting.

OK, let's define our first model ...

```python
%%model
$
U -> A : g_A
U -> B : g_B
A -> U : a_A
B -> U : a_B
A + U -> A + A : r_A
B + U -> B + B : r_B
A + B -> A + U : s
A + B -> B + U : s
$
```

$
U -> A : g_A
U -> B : g_B
A -> U : a_A
B -> U : a_B
A + U -> A + A : r_A
B + U -> B + B : r_B
A + B -> A + U : s
A + B -> B + U : s
$

Here, $A$, $B$ and $U$ represent population of bees in different commitment states during nest site selection. More precisly, $A$ denotes scout bees committed to option $A$, $B$ denotes scout bees committed to option $B$, and $U$ represents scout bees that are uncommitted. There are several spontaneous and interaction transitions with rates given as the last parameter in each line after the `:`.

The reaction rules should also be visible underneath the input cell. Following the model definition we need to parse the model so that we can work with it. This can be done with the `parseModel` command. In our example we can simply use:

```python
model1 = mumot.parseModel(In[2])
```

This creates the model instance `model1` but does not produce any output. The cell reference `In[2]` is a necessary link to the cell in which the model was defined.

## Model exploration <a class="tocSkip">

Now that we have a working model we can do some basic exploration. So, let MuMoT generate the set of Ordinary Differential Equations (ODEs) of our `model1` for us. 

```python
model1.showODEs()
```

$\displaystyle \displaystyle \frac{\textrm{d}A}{\textrm{d}t} := - A B s + A U r_A - A a_A + U g_A$

$\displaystyle \displaystyle \frac{\textrm{d}U}{\textrm{d}t} := 2 A B s - A U r_A + A a_A - B U r_B + B a_B - U g_A - U g_B$

$\displaystyle \displaystyle \frac{\textrm{d}B}{\textrm{d}t} := - A B s + B U r_B - B a_B + U g_B$


We can analyse these equations further but before we do that let's simplify them. One equation is redundant here because there is a constant number of individuals in the swarm during a decision, i.e. the system is conserved.

A simpler set of equations can be obtained using `substitute()` according to

```python
model2 = model1.substitute('U = N - A - B')
```

To see that this indeed simplifies the ODEs we do (note that we created the new instance `model2`) ...


```python
model2.showODEs()
```

$\displaystyle \displaystyle \frac{\textrm{d}A}{\textrm{d}t} := - A B s - A a_A + A r_A \left(- B + \left(- A + N\right)\right) + g_A \left(- B + \left(- A + N\right)\right)$

$\displaystyle \displaystyle \frac{\textrm{d}B}{\textrm{d}t} := - A B s - B a_B + B r_B \left(- B + \left(- A + N\right)\right) + g_B \left(- B + \left(- A + N\right)\right)$


... and see that the number of equations was reduced from three to two. This is because the population of uncommitted bees has been replaced by $U=N-A-B$, where $N$ is the total number of bees which is a constant. 

Now we can turn to more exciting graphical output and numerically *integrate* the ODEs using the MuMoT-method `integrate()`

```python
int1 = model2.integrate()
```

{{< figure src="/img//tutorialimg/gettingStartedInt2.png" width="500">}}

This should have created an interactive plot of the temporal evolution of populations over time. There are some sliders above the figure to manipulate this graph; MuMoT gives you a slider for every rate in the model, and by changing their values, you can see what happens to the behaviour of the system. There are more sliders in the `Advanced options` tab which you can try out.

Important information related to this plot can be retrieved be showing the logs with the `showLogs` command like so:


```python
int1.showLogs(tail = True)
```

    Showing last 3 of 3 log entries:
    Starting numerical integration of ODE system with parameters (a_{A}=2.0), (a_{B}=2.0), (g_{A}=2.0), (g_{B}=2.0), (r_{A}=2.0), (r_{B}=2.0), (s=2.0), (initA=1.0), (initB=0.0), (initU=0.0), (maxTime=3.0), (conserved=True), (substitutedReactant=U), at 2019-04-05 17:49:23.730840
    Last point on curve:

$\displaystyle A(t =3.0) = 3.4121$

$\displaystyle B(t =3.0) = 3.255$


As last part of this short introductory tutorial we will produce a vector of our system. This can be done using:

```python
vector1 = model2.vector('A', 'B', showNoise = True)
```

{{< figure src="/img//tutorialimg/gettingStartedVec.png" width="500">}}


This vector plot depicts how the system evolves depending on the initial conditions. Proportions of bees in states $A$ and $B$ are labelled $\Phi_A$ and $\Phi_B$ - we use the upper-case Greek letter $\Phi$ to denote concentrations (proportions) and the reactants are added as indices. This is done throughout MuMoT and you will encounter this notation again when you work through more examples. Hence, upper-case $\Phi$ cannot be used as a user-defined symbol in MuMoT to avoid confusion. The green ellipse displays noise in the system due to a finite system size (change the system size slider above the plot and see how the ellipse changes; don't increase the system size too much though, as this may increase computation time).

Again, model parameters may be altered via the sliders above the figure and useful information about the computation can be obtained using the `showLogs()` command:


```python
vector1.showLogs(tail = True)
```

    Showing last 3 of 3 log entries:
    Starting 2d vector plot with parameters (a_{A}=2.0), (a_{B}=2.0), (g_{A}=2.0), (g_{B}=2.0), (r_{A}=2.0), (r_{B}=2.0), (s=2.0), (aggregateResults=True), (maxTime=2.0), (randomSeed=1680863739), (runs=20), at 2019-04-05 17:49:30.713976
    Fixed point1:  A = -1.0000, B = -1.0000,  with eigenvalues:  4.0000, 8.0000,  and eigenvectors:  [-1.0000, 1.0000] and [1.0000, 1.0000]
    Fixed point2:  A = 0.3333, B = 0.3333,  with eigenvalues:  -8.0000, -1.3333,  and eigenvectors:  [1.0000, 1.0000] and [-1.0000, 1.0000]


This was just a very short introduction and there is much more to discover. A comprehensive *MuMoT User Manual* can be found on the [MuMoT GitHub page](https://github.com/DiODeProject/MuMoT) (in fact, the examples shown here were taken from this User Manual). Going through the User Manual is highly recommended if you are interested in using MuMoT. You don't even need to install MuMoT yourself, just start it as server and give it a go on MyBinder following [this link](https://mybinder.org/v2/gh/DiODeProject/MuMoT/master?filepath=docs%2FMuMoTuserManual.ipynb).
