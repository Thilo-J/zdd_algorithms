# Zdd Algorithms

Zdd algorithms is a Python library that implements the zdd algorithms that are described on the [wikipedia page](https://en.wikipedia.org/wiki/Zero-suppressed_decision_diagram). With some additional functions for creating a zdd from a set, a set from a zdd and a function to create an image of the zdd.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install zdd_algorithms.

```bash
pip install zdd-algorithms
```

## Zero-suppressed decision diagram

Zdd are a special kind of binary decision diagram that represents a set of sets.

<p align="center">
  <img src="https://raw.githubusercontent.com/Thilo-J/zdd_algorithms/e4185fbbc28a4c59e93c847044b9b9964523dd19/13_23_12.png" alt="zdd"/>
</p>

This Zdd represents the set {{1,3},{2,3},{1,2}} \
Every node has a exactly 2 outgoing edges LO and HI. The LO edge is usally represented by a dotted line and the HI edge with a solid line.
The easiest way to get the set from a visual zdd by hand is to take every path from the root node to the {ø} node(⊤ is also often used as a label for this node).\
Every path represents a set and all paths combined is the set of sets that the Zdd represents.
In this example there are 3 paths from the root node to {ø}. \
If a node has a LO edge in the path that nodes value is ignored. All the other values together represents a set \
3 → 2 → {ø} This path represents the set {3,2} \
3 ⇢ 2 → 1 → {ø} This path represents the set {1,2} \
3 → 2 ⇢ 1 → {ø} This path represents the set {1,3} \
Therefor this zdd represents the set {{1,3},{2,3},{1,2}}

## Usage

Since we cannot have a set of sets in python we use set of frozensets when converting a zdd to the set representation and vice versa

```python
import zdd_algorithms as zdd

# Creates a set of frozensets
set1 = {
    frozenset({1,3}),
    frozenset({2,3})
}
# Create zdd from the set. This zdd represent now the set {{1,3},{2,3}}
zdd1 = zdd.to_zdd(set1)

set2 = {
    frozenset({1,2})
}
zdd2 = zdd.to_zdd(set2)

# Create an union of two zdds
union = zdd.union(zdd1, zdd2)

# Create .PNG image of the zdd. This needs graphviz to be installed! 
zdd.create_image(union)
```

<p align="center">
  <img src="https://raw.githubusercontent.com/Thilo-J/zdd_algorithms/e4185fbbc28a4c59e93c847044b9b9964523dd19/13_23_12.png" alt="zdd"/>
</p>

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)
