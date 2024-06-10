![alt text](title_image.png)

# Kronark Compiler

## Separation of Readability and Optimisation

While traditional text-based programming enables human readability by representing instructions as a combination of words, numbers and brackets, this compiler utilises node graphs. Commonly found in the 3D industry as an artist-friendly approach to writing specialised code for specific contexts, the Kronark Compiler takes the concept a step further and applies it to arbitrary sequences of bytes. This design choice allows a user to assemble optimised instructions and hide them behind a more easily readable graphical representation. While traditional (usually lower level) programming languages often force a user to choose between readability and efficiency, the Kronark Compiler removes this tradeoff by allowing maximum control over the abstractions used to represent the instructions.

## Custom Abstraction Design

Out of the box, the Kronark Compiler provides a selection of fixed function nodes which can be used to easily assemble any desired sequence of bytes. Provided nodes not only allow for compile-time calculations (equivalent to traditional preprocessor directives) but also can be used to define the appearance of new custom nodes. This allows a user to hide complexities of a given sequence of instructions behind a graphical interface, without having to add runtime overhead via function calls as is commonly the case in traditional programming. Due to the fact that a custom node does not equal a function call in the output instruction stream, multiple outputs are possible without the need for wrapper structures (e.g. set or array of output values). Additionally, the type of a given node input can be utilised within a node's network to change the functionality and outside appearance of that node entirely. This acts as the conceptual equivalent to function overloading in traditional programming and can be used to group the same functionality for different data types into a single abstract node.

## Static Type System

A powerful capability of custom node design is the robust specification of data types. Which connections are permissable between different nodes is controlled solely by whether or not the output and input types match. This outright prevents multiple data type related issues and bugs commonly encountered in traditional programming since connectivity (equivalent to writing a variable name or value in text editors) is prevented if data types don't match. The compiler only provides three abstract data types for custom usage out of the box: text, number and truth. Any additional data types need to be entirely designed by users, allowing complete control over even the most primitive forms of data.

## Custom Compilation Target Specification

If it's represented by a sequence of bytes, the Kronark Compiler can target it. Since custom nodes can be used to group the same functionality for different inputs behind the same abstraction, multiple compilation targets are possible while writing the same "source code". Compilation targets for the Kronark Compiler are not equivalent to compilation targets of traditional compilers. While traditional compilers can only target a fixed selection of instruction set architectures (ISAs) no outside user has control over, this compiler implicitely allows the definition of any compilation target by design. Furthermore, this compiler can not only target ISAs but also any form of source code. This allows a user, for example, to write the javascript or python equivalent of a piece of code while actively only working on an x64 binary based project. All that needs to be done once a target's support is implemented in underlying nodes is quite literally flick a switch and the compiler will process a project's node graph in a different target representation.

## Millisecond Compilation Times

The choice of representing byte sequences as node graphs allows for a myriad of compilation time optimisations which are difficult to implement in traditional text editors. By caching the input and output states of all nodes in a node graph, only bytes affected by a user's actions need to be reprocessed. Since all instructions are provided in their target format and hidden behind custom node abstractions, no translation work from source code to machine instructions is needed. This design choice reduces the compilation problem down to a simple string concatenation. Most changes made by a user will therefore only result in a compile time of a few, at most tens of milliseconds, regardless of project size. The only tradeoff for this capability currently is, that the entire project needs to be compiled once on startup, which can be comparatively slow.

## Implicit Dead Code Elimination

Another feature provided by representing code as a network of nodes is the automatic elimination of dead code in any output byte sequence. This is due to the fact that dead code manifests itself in a node graph as a disconnected set of nodes. They are therefore never reached during the compilation process and consequently their bytes are never added to the output. This functionality comes at no additional computation cost, unlike traditional compilers which often only detect dead code segments after parsing their contents for processing.

## Maximum Code Reusability

Representing code as a network of graphs additionally allows for much more flexible reuse of previously "written" code. While traditional programming approaches often represent existing code as libraries containing data types and functions, the Kronark Compiler can reuse specific sequences of instructions without and wrapper constructs (i.e. functions, classes, etc.). This is implicitely facilitated by allowing the design of custom nodes which are all stored in their separate small files. For any given project, the Kronark Compiler provides access to all previously assembled custom nodes. Code reuse is not only enabled in its most fundamental form, it is strongly incentivised.




