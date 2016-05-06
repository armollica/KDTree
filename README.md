# KDTree

Create [*k*-d trees](https://en.wikipedia.org/wiki/K-d_tree) using JavaScript. 

### Examples

<table>
  <tr>
    <td>
      k-Nearest Neighbors (k-NN) Search <br>
      <a href="http://bl.ocks.org/armollica/1593f53c0c8346d067491f39255d0b84"><img src="img/k-nn.png" width="230"></a>
    </td>
    <td>
      1-NN Search <br>
      <a href="http://bl.ocks.org/armollica/64ffc3bd8fc76c5657719a842e39c4e3"><img src="img/1-nn.png" width="230"></a>
    </td>
  </tr>
</table>

### API Reference

*#* **KDTree**()

Creates a new *k*-d tree `generator`.

*#* **generator**(*data*)

Partitions the points in the array `data` into a *k*-d tree of nodes. 
The returned tree will be the root `node` that contains all other nodes as
descendants, or subnodes.

*#* generator.**point**([callback])

Sets the *point*-accessor function for the generator. The callback should 
return a *k*-dimensional point as an array of length *k*. If `callback` is
not specified, it return the current *point*-accessor function. Defaults to:
```function(d) { return d; }```

*#* **node**

The *k*-d tree generator returns the *k*-d tree as a node with descendants. 
Each `node` has four properties:
- `location`: position of the node (array of length *k*)
- `axis`: axis the node splits (integer < k)
- `datum`: data object associated with this node from the original `data` array
- `subnodes`: array of children nodes where `subnodes[0]` is the left child and `subnodes[1]` is the right child 

*#* node.**find**(*point*, [*k*])

Finds the *k*-nearest neighbors of the specified point. Returns an
array of nodes. *k* defaults to 1.

*#* node.**flatten**()

Returns this node and all of its descendants as a flat array of nodes.

*#* node.**toArray**()

Returns this node and its descendants as a nested array.

*#* node.**lines**(*extent*)

Returns an array of points denoting the lines that partition the nodes. This
currently only works when *k* is 2. The *extent* defines how far these lines
go. It's specified as [[*x0*, *y0*],[*x1*,*y1*]] where *x0* and *y0* are the
lower bounds and *x1* and *y1* are the upper bounds.
