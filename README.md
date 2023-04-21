# License Audit for Brightway

Repository to gather information about licenses used in brightway.


## Brightway2 dependencies

Using the official brightway2 docker image, we calculated the list of packages and their licenses,
as well as a dependency graph.

+ [list of dependencies](bw2-deps.csv)
+ [dependency graph](bw2-deps.pdf)

The container was created with:

```
docker run --rm -it -p 8888:8888 -v `pwd`:/license-audit  brightway/bw2
```

### list of dependencies

Use [pip-licenses]()

inside a container, add [pip-licenses](https://pypi.org/project/pip-licenses/)

```
pip install pip-licenses
```

and create the list with:

```
pip-licenses --with-urls --with-authors -f csv > bw2-deps.csv
```

### dependency graph

inside a container, add [graphviz](https://graphviz.org/) and [pipdeptree](https://pypi.org/project/pipdeptree/):

```
conda install python-graphviz
pip install pipdeptree
```

and create the dependency graph in pdf + dot file with:

```
pipdeptree -p brightway2 -l --graph-output pdf > bw2-deps.pdf
pipdeptree -p brightway2 -l --graph-output dot > bw2-deps.dot
```
