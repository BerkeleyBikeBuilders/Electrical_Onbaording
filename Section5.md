# Section 5: PCB Layout

Now that your schematic passes ERC, it is time to lay out the physical board. In this section you will assign footprints, learn the hotkeys, place your components, draw the board outline, route traces, add vias, and pour a ground plane. Make sure your schematic is finished before you start.

## Step 1: Assign footprints
A schematic symbol tells KiCad WHAT a component is. A footprint tells KiCad how that component physically mounts on the board. Each component can come in many sizes and packages, so you have to pick a footprint for every symbol in your schematic.

- Open the "Assign Footprints" tool from the schematic editor.
- For passives (resistors and capacitors), Bike Builders of Berkeley uses the 0603 hand-solder footprint.
- For every other part, match the footprint to the specific component you are using.

![Components](./images/Footprint%20Assignment.png)

Two common package types you will see:
- SMD (Surface-Mount Device): sits on pads on the surface of the board. Smaller, but harder to hand-solder.
- THT (Through-Hole Technology): legs pass through drilled holes. Larger, cheaper, and easier to hand-solder.

## Step 2: Learn the hotkeys
You will move much faster once these are second nature:
- `M`: Move the selected component.
- `R`: Rotate the selected component.
- `X`: Route a trace.
- `V`: Add a via.
- `B`: Fill (pour) zones.
- `E`: Edit the properties of the selected item (for example, set a via's net).

## Step 3: Place your components
- Group components from the same subcircuit close together.
- Keep orientations clean and consistent instead of random.
- Keep the board as small as is reasonable, but leave yourself room to route.
- You are allowed to run traces over or under component footprints.

## Step 4: Draw the board outline (edge cuts)
- Select the Edge.Cuts layer.
- Use the Line or Rectangle tool to draw the outline that defines the size and shape of your board.

## Step 5: Route traces and add vias
- Use the Route Tracks tool (`X`) to connect the pads, following the ratsnest lines.
- This is a two-layer board, so you can use both the top and bottom copper layers.
- Add a via (`V`) to move a trace from one layer to the other. After placing a via, press `E` and set its net (for example, GND).
- Keep the number of vias low, and use a wider trace for the +12V power net.

## Step 6: Pour a ground plane
- Add a filled zone (`B`) on the bottom copper layer.
- Assign it to the GND net. This ties all of your grounds together and cleans up the board.

## Step 7: Run the DRC
- Open the Design Rules Checker (DRC) from the top toolbar, just like ERC in Section 3.
- Fix any errors before you finish. Warnings can usually be ignored for this lab.

# Checkpoint and Deliverables
Unlike the schematic, there is no pre-designed layout for you to copy. This is where the real learning happens! When you have a layout you are happy with, submit a screenshot of the board along with your DRC results to a lab staff member, or get checked off during office hours.

You may get feedback and need more than one try, and that is completely normal!
