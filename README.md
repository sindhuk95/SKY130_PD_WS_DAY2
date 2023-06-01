# later
FLOORPLANNING, LIBRARY CELLS and PLACEMENT

Table of contents  
Floorplanning considerations

Utilization Factor & Aspect Ratio
When it comes to floorplanning, the shape and size of the fllorplan is decided by Aspect Ratio and how good the floor plan is decided by Utilisation Factor. They are defined as follows:

Utilisation Factor =  (Area occupied by netlist)/(total Area of the core)
                   
Aspect Ratio = (height/width)

A Utilisation Factor of 1 signifies 100% utilisation leaving no place for routing and extra logic. However, In real scenario, the Utilisation Factor will usually be  0.5-0.6 ie., 50 to 60% of the area is used for macros, standard cells and rest is used for routing, extralogic. Likewise, an Aspect ratio of 1 signifies that the chip is square shaped. Any value other than 1 signifies rectanglular chip.

Pre-placed cells

Once the Utilisation Factor and Aspect Ratio has been decided, the locations of pre-placed cells need to be defined. lets say we have  a combinational logic which does some function, maybe clock buffers, complex cells like clock gating cell, mux, memory. so these cells are implemented separately. Pre-placed cells are IPs and have user defined locations hence are fixed in those locarions. Since they are placed before automated placement and routing, they are called pre-placed cells.

Decoupling capacitors

Once we place Pre-placed cells, these must be surrounded with decoupling capacitors (decaps). lets say we have logic cell that needs transition. The capcitor demands a huge current and this is provided by the power supply through physical wires. As we know, Physical wires have resistance, capaictance and inductance in it. when the signal/supply voltage travserse through these long wires, they will be voltage drop and the intende supply cannot reach the logic cell that is transitioning.The voltage can lead to undefined region in noise margin. To avoid this, Decaps are invented. These are placed very close to the critical cells.  Decaps are fully charged and have equivalent voltage as of the power supply. Since Decap is close to the logic, its hard for the voltage to drop and the lies with in the Noise Margin range. Their role is to decouple the circuit from power supply by supplying the necessary amount of current to the circuit. They pervent crosstalk.

Power Planning

As we know, there are millions of cells in our design and its hard to supplu power equally to all over the design. However we cannot place decaps cells everywhere in the design.  So, separate horizontal and vertical Vdd and Vss wires have been created forming like a mesh. Now, each cell can tap the required supply from the nearest wire. They way the power is supplied to all the standara cells is through rings,stripes and followpins.

Pin Placement

The netlist is the logical connectivity between cells. The area between the core and die is utilised for placing I/O pins. The connectivity information is defined in either VHDL or Verilog and is used to determine the position of I/O pins of various ports. Then, logical cell placement is bloackage is done inorder to avoid any cells getting placed by automated PnR.

Library Binding and Placement

Netlist Binding and initial place design

First we need to bind the netlist with physical cells. We have shapes for OR, AND and every cell for pratice purpose. But in reality we dont have such shapes, we have give an physical dimensions like rectangles or squares weight and width. This information is given in libs and lefs. Now we place these cells in our design by initilaising it. 

Placement Optimization

The next step is placement. Once we initial the design, the logic cells in netlist in its physical dimisoins is placed on the floorplan. Placement is perfomed in 2 stages:

Global Placement: Cells will be placed randomly in optimal positions which may not be legal and cells may overlap. 
Detailed Placement: It alters the position of cells post global placement so as to legalise them.
Legalisation of cells is important from timing point of view.
Optimization is stage where we estimate the lenght and capictance, based on that we add buffers. Ideally, Optimization is done for better timing.

Need for libraries and characterization

