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
As we know, Each block on the chip, however, cannot have its own decap unlike the pre-placed macros. Therefore, a good power planning ensures that each block has its own VDD and VSS pads connected to the horizontal and vertical power and GND lines which form a power mesh.

Pin Placement
The netlist defines connectivity between logic gates. The place between the core and die is utilised for placing pins. The connectivity information coded in either VHDL or Verilog is used to determine the position of I/O pads of various pins. Then, logical placement blocking of pre-placed macros is performed so as to differentiate that area from that of the pin area.
