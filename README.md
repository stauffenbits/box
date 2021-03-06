# The Box Language

## Setup

I am no build engineer...

### Box Runtime

The standalone Box runtime can be installed like so: 
```sh
$ git clone https://github.com/stauffenbits/box
$ cd box
$ npm install
# npm link
```

### Box Kernel

If you're feeling adventurous, you can install the jupyter kernel that goes along
with it.

#### From Source

```sh
$ git clone https://stauffenbits/BoxKernel
$ cd BoxKernel
$ python -m pip install -e box_kernel
$ python -m box_kernel.install
```

might work...

#### Experimental (for me) with PyPi
Proceed with caution...
This is what I'm going for:

```
$ python -m venv jupyter
$ source jupyter/bin/activate
$ python -m pip install jupyter jupyterlab box_kernel-stauffenbits
$ python -m box_kernel.install
$ jupyter lab
```


## [Joshua Moore](mailto:joshua.moore@leudla.net)
Draws boxes either stacked horizontally or vertically, nested inside of each other.

To run the examples, run ./bin/box.js examples/*
Or choose a specific example.
Or pass in a string via the command line, just be sure to escape your characters using single quotes. 


  Usage: `./bin/box.js '[ [] ]'`
  Don't forget to escape your characters as appropriate for your shell if
  using this from the command line. 

  Welcome to Joshua Moore's implementation of the box challenge. This program
  draws nested ASCII boxes. Here's a quick rundown of the language used for 
  controlling box.js...

  For a single box, enter: 
  * `[]` to get

```
    +-+
    | |
    +-+
```

  You can nest boxes by including one in another.
  * `[ [] ]`

```
    +-----+
    | +-+ |
    | | | |
    | +-+ |
    +-----+
```

  The syntax for controlling stacking behavior is pretty literal:
  * `[- [] [] ]`, including a minus - after the opening box tag stacks boxes
    horizontally.
  
  ```
    +---------+
    | +-+ +-+ |
    | | | | | |
    | +-+ +-+ |
    +---------+
```

  * `[| [] [] ]`, while a pipe will stack a box's children vertically

```
    +-----+
    | +-+ |
    | | | |
    | +-+ |
    | +-+ |
    | | | |
    | +-+ |
    +-----+
```


  * Of course, writing out all the boxes by hand can get cumbersome, so here's
    some shortcuts: 

    `[-2[]]` will produce two horizontally stacked children
    `[|5[]]` will produce five vertically stacked children

    Please note that numbers can only be used inside of other boxes.


  * You can mix and match number and literal syntax:

   `[- 2[] [|5[]] [-3[]] ]` will produce 

```
    +---------------------------------+
    | +-+ +-+ +-----+ +-------------+ |
    | | | | | | +-+ | | +-+ +-+ +-+ | |
    | +-+ +-+ | | | | | | | | | | | | |
    |         | +-+ | | +-+ +-+ +-+ | |
    |         | +-+ | +-------------+ |
    |         | | | |                 |
    |         | +-+ |                 |
    |         | +-+ |                 |
    |         | | | |                 |
    |         | +-+ |                 |
    |         | +-+ |                 |
    |         | | | |                 |
    |         | +-+ |                 |
    |         | +-+ |                 |
    |         | | | |                 |
    |         | +-+ |                 |
    |         +-----+                 |
    +---------------------------------+
```

  * And finally, there's a shortcut for nesting boxes

    `./bin/box.js '[- 2[^5] 3[]]'`

```
    +-----------------------------------------+
    | +-+ +-+ +-----------------+ +-+ +-+ +-+ |
    | | | | | | +-------------+ | | | | | | | |
    | +-+ +-+ | | +---------+ | | +-+ +-+ +-+ |
    |         | | | +-----+ | | |             |
    |         | | | | +-+ | | | |             |
    |         | | | | | | | | | |             |
    |         | | | | +-+ | | | |             |
    |         | | | +-----+ | | |             |
    |         | | +---------+ | |             |
    |         | +-------------+ |             |
    |         +-----------------+             |
    +-----------------------------------------+
```

    Enjoy!
