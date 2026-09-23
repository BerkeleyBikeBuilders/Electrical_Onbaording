# Section 6: G-code

Welcome to the software half of the lab. In the last few sections you designed hardware. Here you will learn G-code, the language that drives CNC machines and 3D printers, and then write a small program that generates it.

## What is G-code?

G-code is a plain-text language that tells a machine how to move. Each line is a command, and the machine runs the lines in order. A 3D printer slicer, for example, turns a 3D model into thousands of lines of G-code that move the print head along a path, one thin layer at a time.

Every line is usually one command word (like `G1`) followed by parameters (like `X10 Y5 F600`). Anything after a semicolon `;` is a comment and is ignored by the machine.

### The commands you need

You only need a handful of commands for this lab:

| Command | Meaning |
| --- | --- |
| `G21` | Set units to millimeters |
| `G90` | Absolute positioning (coordinates are measured from the origin) |
| `G91` | Relative positioning (each coordinate is measured from the current position) |
| `G0` | Rapid move (travel without working) |
| `G1` | Linear move (the normal working move) |
| `F` | Feedrate, the speed of a move in mm/min |
| `X` `Y` `Z` | Target position on each axis |

A real printer also uses an `E` value to push filament (extrude). For this lab you can ignore extrusion completely and only move in X, Y, and Z.

### A quick example

Here is a short program that sets millimeters and relative positioning, then traces a 20 mm square on a single layer:

```
G21          ; units are millimeters
G91          ; relative positioning
G1 F600      ; set the feedrate to 600 mm/min
G1 X20       ; move 20 mm in +X
G1 Y20       ; move 20 mm in +Y
G1 X-20      ; move 20 mm in -X
G1 Y-20      ; move 20 mm in -Y, back to the start
```

Because we set relative positioning with `G91`, every move is measured from where the head currently is, so `X20` followed by `X-20` returns you to where you started.

## The Assignment

Write a program in Java that generates the G-code to build a cube.

New to Java? Start here: [Java tutorial](https://www.w3schools.com/java/) (your lab staff can point you to the preferred resource).

Your program should:

1. Take an integer `size` (the side length of the cube in millimeters).
2. Create and write to a text file (for example `cube.gcode` or `cube.txt`).
3. Write a header with the setup commands: millimeters (`G21`), relative positioning (`G91`), and a feedrate (`F`).
4. Generate the moves to build a `size` x `size` x `size` mm cube, then close the file.

Assumptions to keep it simple:

- The filament lays down an ideal strip that is 0.2 mm wide and 0.2 mm tall. That means each printed layer is 0.2 mm tall, so a cube of height `size` has `size / 0.2` layers.
- Build each layer by tracing the square perimeter (four sides of length `size`), then raise the head by 0.2 mm in Z and trace the next layer.
- Ignore extrusion. Only `X`, `Y`, and `Z` moves are required.

### What your output should look like

The first few lines, for any size, should look like this:

```
G21          ; units are millimeters
G91          ; relative positioning
G1 F600      ; feedrate
```

Then, for a cube with `size = 10`, the first layer would be:

```
G1 X10       ; side 1
G1 Y10       ; side 2
G1 X-10      ; side 3
G1 Y-10      ; side 4
G1 Z0.2      ; step up one layer
```

Your program should repeat that layer `size / 0.2` times to reach the full height.

### A Java starting point

You do not have to use this, but here is a skeleton to get you going:

```
import java.io.FileWriter;
import java.io.IOException;

public class CubeGcode {
    public static void main(String[] args) throws IOException {
        int size = 10; // cube side length in millimeters

        FileWriter out = new FileWriter("cube.gcode");

        // 1. Write the header: G21, G91, and a feedrate

        // 2. Loop over the layers (size / 0.2 of them)
        //    - trace the square perimeter with four G1 moves
        //    - raise Z by 0.2 mm

        out.close();
    }
}
```

Stretch goal: fill each layer with parallel passes spaced 0.2 mm apart (the strip width) so the cube is solid instead of hollow.

### Deliverable

Show a lab staff member your Java source and the G-code file it produces, or come to office hours to get checked off. If you want to see it move for real, we can run your file on a printer.

### Good luck!
