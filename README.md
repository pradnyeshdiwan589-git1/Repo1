###Project 1

This project is a 4-bit priority encoder designed and simulated in Cadence Virtuoso using the gpdk90nm technology library.

What it does: The encoder takes four inputs (I0 to I3) and produces a 2-bit binary code (Y1, Y0) for the highest-priority active input, where I3 has the highest priority. A valid bit (V) goes high when any input is active.

Logic equations:
Y1 = I2 + I3
Y0 = I1·I2' + I3
V = I0 + I1 + I2 + I3

Implementation approach:
A transistor-level NAND2 gate was built from two parallel PMOS and two series NMOS transistors.
A NAND4 gate was built from four parallel PMOS and four series NMOS transistors.
Both were turned into symbols and used as building blocks to assemble the full encoder, with the equations rewritten in NAND-only form.

Transistor Sizing:
Transistor sizing was done directly in the Cadence Virtuoso schematic editor by setting the width (W) and length (L) of each MOSFET in the gpdk90nm library. The aim was to give the pull-up and pull-down networks balanced drive strength, so the rise and fall delays are roughly equal and the output swings fully between 0 and VDD.

Verification: A transient analysis was run in ADE L, with the inputs driven by VPULSE sources. The report concludes that the output waveforms match the truth table, confirming correct priority encoding.

A few things I noticed in the report:
The Boolean equations in the text appear to have lost their overbars during PDF conversion, so the NAND forms are hard to read exactly as written.
The report doesn’t include quantitative metrics such as delay, power, or transistor sizing, so the validation is qualitative (waveform inspection only).
