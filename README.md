# Cities-Generator
Cities generator based on Yocto/GL Library. It generates random cities using context-free grammars.
This project is repository version of my yocto-gl [Fork](https://github.com/antoniomuso/yocto-gl).

The repository provides the user with a specialized grammar for a block-construction.
The grammar features:
- Methods for objects positioning in scene.
- Methods for rotation.
- Methods for scaling.
- Methods for avoiding collisions of objects.

The variables of grammar are called nodes, inside nodes there are the shapes of the object bound to the node.
The nodes can be empty and, in this case, they become support variables for the grammar.
The nodes will be added to graph struct that represents the grammar.
Rules of grammar are of this type `A := B | C | D ` this meaning that the node `A` can be replaced with the node `B` or node `C` or `D`, The variable selection is random in the algorithm. it is possible to do a substitution with more variables ` B := C and D | C and B ` this means that `B` can be replaced with `C` and `D`, or with `C` and `B`. 
The grammar costruction is based on three principal methods:
- **loadNode**: it takes a path of .obj in input and returns a node.
- **add_multi_nodes_or**: it takes a node `A` and a set of nodes `Bn` (with relative costants)and creates the following rule `A := .. | B | B1 | ... | Bn`. if just exist a rule for `A`, it merges the set with rule.
- **add_multi_nodes_and**: it takes a node `A` and a set of nodes `Bn` and create the following rule `A := .. | B1 and B2 and ... Bn`


## Images
![Image](Images/image7.png)
![Image](Images/out1.png)
![Image](Images/out9.png)
![Image](Images/out5.png)



## Getting Started
```
git clone --recursive https://github.com/antoniomuso/cities-generator.git
```
How to build.
```
mkdir build; cd build; cmake ..; cmake --build .
```
To run application
```
cd ..
./bin/build_generator
```
You can use option **-d** to change cities dimension, default 50, and **-o** to change output filename.
```
./bin/build_generator -d 100 -o myFile.obj
```

### Prerequisites

To Build you need of [OpenGL](http://freeglut.sourceforge.net/), [Glew](http://glew.sourceforge.net/) and [Glfw](http://www.glfw.org/) 

### Installing
You can install dependencis on Ubuntu with the following commands:
```
sudo apt-get update
sudo apt-get install freeglut3 freeglut3-dev
sudo apt-get install libglew-dev
sudo apt-get install libglfw3-dev
```










## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details
