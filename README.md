# License Audit for Brightway

Repository to gather information about licenses used in brightway.


## Brightway2X dependencies

Using the official brightway2 docker image, we calculated the list of packages and their licenses,
as well as a dependency graph.

+ [list of bw2 dependencies](bw2-deps.csv)
+ [dependency graph for bw2](bw2-deps.pdf)
+ [list of dependencies](bw25-deps.csv)
+ [dependency graph for bw25](bw25-deps.pdf)

The container was created with:

```
# for brightway2
docker run --rm -it -p 8888:8888 -v `pwd`:/license-audit  brightway/bw2
```

```
# for brightway25
docker run --rm -it -p 8888:8888 -v `pwd`:/license-audit  brightway/bw25
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
# For bw25:
pip-licenses --with-urls --with-authors -f csv > bw25-deps.csv
```

### dependency graph

inside a container, add [graphviz](https://graphviz.org/) and [pipdeptree](https://pypi.org/project/pipdeptree/):

```
conda install python-graphviz
pip install pipdeptree
```

and create the dependency graph in pdf + dot file with:

for bw2:
```
pipdeptree -p brightway2 -l --graph-output pdf > bw2-deps.pdf
pipdeptree -p brightway2 -l --graph-output dot > bw2-deps.dot
```

for bw25:
```
pipdeptree -p brightway25 -l --graph-output pdf > bw25-deps.pdf
pipdeptree -p brightway25 -l --graph-output dot > bw25-deps.dot
```
