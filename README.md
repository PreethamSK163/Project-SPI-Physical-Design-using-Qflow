# SPI Physical Design using Qflow
> RTL-to-GDSII Physical Design Implementation of a Serial Peripheral Interface (SPI) Controller

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-Qflow-blue)
![Tool](https://img.shields.io/badge/Tool-Yosys-blue)
![Tool](https://img.shields.io/badge/Tool-Magic-blue)
![PDK](https://img.shields.io/badge/PDK-OSU018-orange)
![Design](https://img.shields.io/badge/Design-SPI%20Controller-purple)
![Program](https://img.shields.io/badge/Program-Maven%20Silicon-red)

<h2>🔍 Overview</h2>

- Implemented the complete **RTL-to-GDSII** physical design flow for an **SPI Controller** using the open-source **Qflow** EDA framework — covering synthesis with Yosys/ABC, standard cell placement with Graywolf, static timing analysis with Vesta, detailed routing with Qrouter, and layout verification using Magic and Netgen.

- Achieved a **DRC-clean** and **LVS-verified** layout with **zero failed routes** — confirming circuit equivalence between the gate-level netlist and the final GDSII layout, and validating timing closure with the **OSU018 0.18 µm standard cell library**.

<h2>🛠️ Tools & Technology Stack</h2>

| Category | Tool / Technology |
|:---|:---|
| Flow Manager | Qflow 1.3.17 |
| RTL Synthesis | Yosys + ABC |
| Fanout & Buffering | blifFanout |
| Placement | Graywolf (Simulated Annealing) |
| Static Timing Analysis | Vesta |
| Routing | Qrouter |
| Layout & DRC | Magic 8.3 |
| LVS | Netgen |
| Standard Cell Library | OSU018 — 0.18 µm |
| HDL | Verilog |
| OS | Ubuntu Linux (VirtualBox) |

<h2>⚙️ Complete Design Flow</h2>

| Stage | Tool | Description | Status |
|:---|:---|:---|:---|
| Tool Setup & Invocation | Qflow GUI | Installation, project config, GUI launch | ✅ Complete |
| Synthesis | Yosys + ABC | RTL → gate-level netlist, cell mapping | ✅ Complete |
| Placement | Graywolf | Standard cell placement, power striping | ✅ Complete |
| Static Timing Analysis | Vesta | Pre-route STA, critical path analysis | ✅ Complete |
| Routing | Qrouter | Detailed routing, via minimization | ✅ Complete |
| DRC & LVS | Magic + Netgen | Design rule check, layout vs schematic | ✅ Complete |
| GDSII Generation | Magic | Final mask data — fabrication ready | ✅ Complete |

<h2>📊 Key Results</h2>

| Metric | Value |
|:---|:---|
| Design | SPI Controller (Full-Duplex, Master-Slave, 4-Wire) |
| Technology Node | 0.18 µm (OSU018 Standard Cell Library) |
| SPI Modes Supported | All 4 — Mode 0/1/2/3 (CPOL/CPHA) |
| Total Standard Cells | 3,106 |
| Total Routes Completed | 22,417 |
| Failed Routes | 0 |
| Routing Rows | 36 |
| Fill Cells Inserted | 553 (7 power stripes) |
| Critical Path Delay | 4,305.4 ps |
| Clock Skew | 348.187 ps |
| DRC Violations | 0 (drc = 0) |
| LVS Status | Circuits match uniquely — Clean |
| GDSII | Generated — Fabrication Ready |
| Qflow Checklist | All stages — Okay ✅ |

<h2>📁 Repository Structure</h2>

```
📁 Project-SPI-Physical-Design-using-Qflow
├── 📁 01 : Tool Setup & Invocation   → Qflow install, project config, GUI launch
├── 📁 02 : Synthesis                 → Yosys + ABC, gate-level netlist
├── 📁 03 : Placement                 → Graywolf, DEF, power stripes
├── 📁 04 : Static Timing Analysis    → Vesta, critical path, slack
├── 📁 05 : Routing                   → Qrouter, 22417 routes, no failures
├── 📁 06 : DRC & LVS                 → Magic DRC clean, Netgen LVS clean
├── 📁 07 : GDSII Generation          → Magic GDSII, fabrication ready
├── 📁 source                         → SPI RTL Verilog source files
│   ├── spi_top.v
│   ├── spi_clgen.v
│   ├── spi_shift.v
│   ├── spi_slave.v
│   ├── spi_defines.v
│   ├── timescale.v
│   └── spi_top.ys
└── 📄 README.md
```

<h2>📝 Stage Details</h2>

**01 — Tool Setup & Invocation** &nbsp;|&nbsp; `Qflow` `GUI` `osu018` `VirtualBox`

Installed Qflow on Ubuntu via `sudo apt-get install qflow` — automatically resolving all dependencies including Yosys, Graywolf, Qrouter, Magic, Netgen, and Vesta. Configured the project directory, selected OSU018 as the technology library, set `spi_top.v` as the Verilog source, and launched the Qflow Manager GUI using `qflow gui`.

> 📁 [View Stage Details](./01%20:%20Tool%20Setup%20%26%20Invocation/README.md)

---

**02 — Synthesis** &nbsp;|&nbsp; `Yosys` `ABC` `blifFanout` `Gate-Level Netlist`

Executed RTL synthesis using Yosys with ABC for logic optimization and technology mapping to the OSU018 standard cell library. blifFanout performed fanout balancing and buffer insertion. The synthesis process generated 3,106 standard cells and produced RTL Verilog, SPICE, and BLIF output files for downstream physical design stages.

> 📁 [View Stage Details](./02%20:%20Synthesis/README.md)

---

**03 — Placement** &nbsp;|&nbsp; `Graywolf` `Simulated Annealing` `DEF` `Power Stripes`

Placed 3,106 standard cells across 36 rows using Graywolf's simulated annealing algorithm — targeting wirelength minimization and congestion avoidance. Inserted 553 fill cells for 7 power stripes of 1.6 µm width, ran addspacers and arrangepins for pin optimization, and generated the final DEF file ready for routing.

> 📁 [View Stage Details](./03%20:%20Placement/README.md)

---

**04 — Static Timing Analysis** &nbsp;|&nbsp; `Vesta` `Critical Path` `Setup Time` `Slack`

Performed pre-route static timing analysis using Vesta on the OSU018 standard cell library — analyzing 321 timing paths. Identified the critical path (DFFSR_42/CLK → DFFSR_180/D) with a delay of 4,305.4 ps, clock skew of 348.187 ps, and setup time of 94.1149 ps. Generated the top 20 maximum delay paths report to guide optimization.

> 📁 [View Stage Details](./04%20:%20Static%20Timing%20Analysis/README.md)

---

**05 — Routing** &nbsp;|&nbsp; `Qrouter` `22417 Routes` `No Failed Routes` `DEF`

Executed detailed routing using Qrouter across 3 stages — completing 22,417 total routes with zero failed routes. Generated the routed DEF file (`spi_top_route.def`) and RC file for back-annotation. Ran the annotate script for power/ground connections and confirmed clean routing with post-route STA back-annotation.

> 📁 [View Stage Details](./05%20:%20Routing/README.md)

---

**06 — DRC & LVS** &nbsp;|&nbsp; `Magic` `Netgen` `drc=0` `LVS Clean`

Performed Design Rule Checking using Magic 8.3 — processed 50,000 rectangles across all standard cells and confirmed `drc = 0` with zero violations. Followed by LVS verification using Netgen — extracted the layout netlist and compared against the schematic netlist, confirming "Circuits match uniquely" with full pin and device equivalence.

> 📁 [View Stage Details](./06%20:%20DRC%20%26%20LVS/README.md)

---

**07 — GDSII Generation** &nbsp;|&nbsp; `Magic` `GDSII` `Tape-out` `Final Layout`

Generated the final GDSII file using Magic's `generate_gds_spi_top.tcl` script — writing all standard cells including CLKBUF1, DFFSR, FILL, INVX2, BUFX4, AOI21X1, NOR2X1, and 15+ additional cell types to the `.gds` output. All Qflow checklist stages confirmed Okay with "Project is completed" status.

> 📁 [View Stage Details](./07%20:%20GDSII%20Generation/README.md)

---

<h2>🤝 Connect</h2>

| **Author** | Preetham SK |
|:---|:---|
| **Organization** | Maven Silicon |
| **LinkedIn** | [linkedin.com/in/preethamsk16](https://www.linkedin.com/in/preethamsk16) |
| **GitHub** | [github.com/PreethamSK163](https://github.com/PreethamSK163) |
| **Email** | preethamsk163@gmail.com |
