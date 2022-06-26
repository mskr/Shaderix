# Shaderix

Unix-like shell, but for executing shader programs on geometry- or image-files.

## Concept

1) Start as CLI,
2) scan cwd for shader/model/image files and 
3) prepare them for execution/processing.

[Command language](https://github.com/mskr/cmd)

String/filename/URL hashing:

1) Techniques from Gregory's Game Engine Technology book.
2) https://stackoverflow.com/questions/30695564/what-kind-of-hashing-function-algorithm-does-javascript-associative-array-use
3) https://mollyrocket.com/meowhash

## Example

```

> shadeVertices SomeMesh.obj | shadeFragments PRIM_TRIS; 

< [execution_id]: variables: [var1]...[varn]; 

> timeline; 

< |0ms| [execution_id] |xms| ... |20ms|; var1 |0ms| a ...|20ms| b; 

> save;

```

## GUI

Instead of rolling our own GUI, we integrate into the Open With... menu that most OS have. We can use the camera metaphor: open 3D file with camera.

It should be a tool that every Technical Artist can use for real-time projects in the industry (somewhere money has to come from).

There can be many little camera programs based on Shaderix.

## Advanced features

Advanced features can build on variables:

1) Declaration, definition and initialization is unified.
2) Once defined, the tool automatically generates shaders with the variables (uniforms and varyings).

Some variables can be simple commands:

1) Annotation for when it is executed: @init, @render (inside render loop).
2) Syntax should equal a subset of the intersection of C and GLSL.

## AI

Train on OBJ files from the web.

Use it to generate or autocomplete OBJ.

## File Format Based on Commands

"Getting modules to talk to each other, however, is not a trivial problem. I think the only way to design interfaces that's actually stood the test of time was not to design them in terms of function calls or classes, but to design them in terms of data formats." (https://isetta.io/interviews/ArasPranckevicius-interview/) 

And the nicest data/file formats are formulated in terms of commands + data, so that they can be interactively created in some kind of REPL.

A file format based on commands is more than a file format.

It is a REPL language.

It is a network protocol.

### Examples

Example GUI file format:

```
layout border
button PRESSME border.north
```

### Axioms

1. Favor file structure over code structure. Ignore indentations.

2. Many small files are friendly to version control and collaboration.

3. Files are considered objects as in OOP. This invites extension and reuse as in libraries.

4. Code files can be referenced. Hereby the file format integrates into the coding ecosystem.

5. Natively supported code file formats are c, cs, js, ts, py, glsl, frag, vert, spirv.
