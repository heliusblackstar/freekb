# Setting up TAWS G-Code for 3D Printers

## Summary
Totally Awesome Warm Startup (TAWS) warms up the hot-end only half way before perfoming mesh bed leveling, ensuring no oozing of filament onto the bed or out of the hot-end before the print actually starts.
After the print job is done, a series of musical notes will play from the printer's speaker, and the print head will move to the center of the X-axis to make cleaning the nozzle easier.

## Steps
1. In PrusaSlicer, click `Printer Settings`, then `Custom G-code`.
1. Replace `Start G-code` with this text:

                M862.3 P "[printer_model]" ; printer model check
                M862.1 P[nozzle_diameter] ; nozzle diameter check
                G90 ; use absolute coordinates

                ;TAWS BEGIN
                M83  ; extruder relative mode
                M104 S121 ; set extruder temp
                M140 S[first_layer_bed_temperature] ; set bed temp
                M190 S[first_layer_bed_temperature] ; wait for bed temp

                G28 W ; home all without mesh bed level
                G80 ; mesh bed leveling

                M83 ; extruder relative mode
                M104 S[first_layer_temperature] ; set extruder temp
                M140 S[first_layer_bed_temperature] ; set bed temp
                M190 S[first_layer_bed_temperature] ; wait for bed temp
                M109 S[first_layer_temperature] ; wait for extruder temp
                G1 Y-3.0 F1000.0 ; go outside print area
                G92 E0.0
                G1 X60.0 E9.0 F1000.0 ; intro line
                G1 X100.0 E12.5 F1000.0 ; intro line
                ;TAWS END

                G92 E0.0
                M221 S{if layer_height<0.075}100{else}95{endif}

1. Replace `End G-code` with this text:

                G4 ; wait
                M221 S100
                M104 S0 ; turn off temperature
                M140 S0 ; turn off heatbed
                M107 ; turn off fan
                {if layer_z < max_print_height}G1 Z{z_offset+min(layer_z+30, max_print_height)}{endif} ; Move print head up
                G1 X120 Y200 F3000 ; home X axis
                M84 ; disable motors


                ; musical notes begin
                M300 S987 P133 
                M300 S987 P133
                M300 S2489 P267
                M300 S987 P267
                M300 S2217 P267
                M300 S880 P267
                M300 S0 P1071
                M300 S987 P133
                M300 S987 P133
                M300 S987 P133
                M300 S987 P133
                M300 S880 P267
                M300 S987 P267
                M300 S0 P1071 
                ; musical notes end

                M73 P100 R0
                M73 Q100 S0

1. Changes will be effective in the next model you slice.






***
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

