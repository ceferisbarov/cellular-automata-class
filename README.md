# Cell class for Cellular Automata

# How to install
`pip install cellular-automata-class`

# How to use
Import the class as:
```python
from cellular_automata_class import cell
```
It can be used to set up a lattice:
```python
def set_lattice(length, choice):
    '''
    Given the choice of lattice pattern, sets a 2 dimensional, finite lattice,
    digits of which store a cell each
    '''
  
    lattice = []
    for n in range(length):
        lattice.append([])
    
    for x in range(length):
        for y in range(length):
            lattice[x] += [Cell(1,x,y) if x == math.floor(length/2) else Cell(0,x,y)]

    return lattice
```
In order to "play" the lattice, we need to iterate through the whole lattice calling `cell.evaluate()` method:
```python
def play(lattice, evaluation_count):
    '''
    After main() receives the input and sets the lattice,
    play() takes care of the rest. Just to keep main() tiny and neat.
    '''
    images = []
    for n in range(evaluation_count): 
        lattice_copy = copy.deepcopy(lattice)
        for x in lattice:
            for y in x:
                y.evaluate(lattice_copy)
```
The class can be expanded in various ways. E.g. we can add stochastic element to it, we can add new neighborhood types, etc.
