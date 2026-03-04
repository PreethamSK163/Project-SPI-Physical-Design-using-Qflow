# Placement
> Standard Cell Placement using Graywolf Simulated Annealing with Power Stripe Insertion

![Tool](https://img.shields.io/badge/Tool-Graywolf-blue)
![Tool](https://img.shields.io/badge/Tool-Qflow-blue)
![PDK](https://img.shields.io/badge/PDK-OSU018-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Placed 3,106 standard cells across 36 rows using Graywolf's simulated annealing algorithm — targeting wirelength minimization and congestion avoidance, with 553 fill cells inserted for 7 power stripes of 1.6 µm width at 49.6 µm pitch.
- Generated the final DEF file (`spi_top_mod.def`) with 3,659 total components after spacer insertion, ran arrangepins for optimal pin positioning, and completed placement on Wednesday 02 July 2025 at 11:33:31 PM IST.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Global Placement | Graywolf simulated annealing — 3,106 cells across 36 rows |
| Power Stripe Insertion | addspacers — 553 fill cells, 7 stripes, 1.6 µm width |
| Pin Arrangement | arrangepins — optimal I/O pin positions for routing |
| DEF Generation | Final DEF file with 3,659 components for Qrouter |

<h2>📝 Stage Details</h2>

**Task 1 — Global Placement** &nbsp;|&nbsp; `Graywolf` `Simulated Annealing` `36 Rows` `DEF`

Initiated placement from the Qflow Manager GUI — Graywolf launched with `graywolf spi_top` command. The simulated annealing algorithm placed all 3,106 standard cells across 36 rows with longest row width of 367.6 µm. place2def.tcl converted the placement output to DEF format with 6 metal routing layers (metal1–metal6) defined for subsequent routing.

**Task 2 — Power Stripe Insertion & Pin Arrangement** &nbsp;|&nbsp; `addspacers` `arrangepins` `553 Fill Cells`

addspacers inserted 553 fill cells to generate 7 power stripes of 1.6 µm width (2.0 µm requested) at 49.6 µm pitch — increasing total component count from 3,106 to 3,659. arrangepins recalculated and optimized I/O pin positions for routing accessibility, writing the final `spi_top_mod.def` file. blifanno.tcl annotated the BLIF netlist with placement data, completing placement at 11:33:31 PM IST.

<h2>📊 Placement Results</h2>

| Metric | Value |
|:---|:---|
| Total Standard Cells | 3,106 |
| Placement Rows | 36 |
| Longest Row Width | 367.6 µm |
| Fill Cells Inserted | 553 |
| Power Stripes | 7 stripes — 1.6 µm width, 49.6 µm pitch |
| Total Components (Post-Spacer) | 3,659 |
| Metal Routing Layers | 6 (metal1–metal6) |
| Output DEF File | spi_top_mod.def |
| Placement Script End | Wed 02 July 2025, 11:33:31 PM IST |

<h2>🖼️ Implementation Results</h2>

### Qflow Manager — Placement In Progress (Graywolf Visualization)
![6_Image_during_placement](6_Image_during_placement.png)

### Placement Log File
![7_Image_of_Placement_Logfile](7_Image_of_Placement_Logfile.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 02 : Synthesis](../02%20:%20Synthesis/README.md) &nbsp;|&nbsp; [Next : 04 : Static Timing Analysis](../04%20:%20Static%20Timing%20Analysis/README.md)
