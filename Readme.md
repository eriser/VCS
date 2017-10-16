# VCS - Voltage Controlled Switches for VCV Rack

Some voltage controlled switches for [VCV Rack](vcvrack.com).

## Building

This has been built against vcvrack 0.4.0.

You will need to include a pair of lines like:

createModel<VCS1x8Widget>(plugin, "VCS", "1x8 Voltage Controlled Switch");
createModel<VCS2x4Widget>(plugin, "VCS", "2x4 Voltage Controlled Switch");

in the init function for whatever plugin you integrate this with. Eg Fundimental.cpp for the fundimental plugins, or Core.cpp for the core system.

You will also need to add a the following to what ever header (Fundimental.hpp / Core.hpp / whatever):

struct VCS1x8Widget : ModuleWidget {
	VCS1x8Widget();
};

struct VCS2x4Widget : ModuleWidget {
	VCS2x4Widget();
};

You may also wish to adjust the BG_IMAGE_FILE_1x8 and BG_IMAGE_FILE_2x4 macros in VCS.cpp.


## Useage 

The 1x8 and 2x4 modules both work the same way, You apply a trigger to the trigger input and a signal in to the signal input. 

Then you wire up as many outputs as you'd like.

Recieving trigger events will cause the module to switch to the next active output plug.

The 2x8 module has 1 trigger input and 2 signal inputs and 4 outputs per input.