# GDSII Generation
> Final Layout Generation using Magic — Fabrication-Ready GDSII Output

![Tool](https://img.shields.io/badge/Tool-Magic-blue)
![Tool](https://img.shields.io/badge/Tool-Qflow-blue)
![PDK](https://img.shields.io/badge/PDK-OSU018-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Generated the final GDSII file for the SPI Controller using Magic's `generate_gds_spi_top.tcl` script — writing all 20+ standard cell types to the `.gds` output after DRC-clean and LVS-verified layout confirmation.
- All Qflow checklist stages confirmed Okay with "Project is completed" status — producing the fabrication-ready GDSII layout representing the complete RTL-to-GDSII physical design flow for the SPI Controller.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| GDSII Generation | Magic — generate_gds_spi_top.tcl, all cells written to .gds |
| Final Verification | All Qflow checklist stages — Okay, Project is completed |
| Final Layout View | Magic layout viewer — complete routed SPI Controller |

<h2>📝 Stage Details</h2>

**Task 1 — GDSII File Generation** &nbsp;|&nbsp; `Magic` `generate_gds_spi_top.tcl` `20+ Cell Types`

GDSII generation executed using Magic 8.3 revision 105 via the script `generate_gds_spi_top.tcl`. Magic loaded the OSU018 LEF file and processed 50,000 rectangles before writing the complete cell hierarchy to the `.gds` output. Standard cells written to GDSII:

| Cell | Cell | Cell | Cell |
|:---|:---|:---|:---|
| spi_top | CLKBUF1 | DFFSR | FILL |
| INVX2 | BUFX4 | AOI21X1 | NOR2X1 |
| OAI22X1 | OAI21X1 | AOI22X1 | NAND2X1 |
| INVX1 | AND2X2 | BUFX2 | INVX8 |
| MUX2X1 | INVX4 | NOR3X1 | XNOR2X1 |
| XOR2X1 | OR2X2 | NAND3X1 | — |

GDS generating script ended Thursday 03 July 2025 at 12:06:12 AM IST.

**Task 2 — Final Qflow Checklist Verification** &nbsp;|&nbsp; `All Okay` `Project Completed` `Magic Layout`

After GDSII generation, the Qflow Manager confirmed all checklist stages as Okay — Preparation, Synthesis, Placement, Static Timing Analysis, Routing, Post-Route STA, Migration, DRC, LVS, GDS, and Cleanup. Terminal log confirmed:
- `qflow exited with status 0`
- `Current qflow status: Next project action is clean`
- `Current qflow status: Project is completed`

The final GDSII layout was opened in Magic's layout viewer — displaying the complete routed SPI Controller with all metal layers, standard cells, and interconnects visible across the full chip area.

<h2>📊 GDSII Generation Results</h2>

| Metric | Value |
|:---|:---|
| Tool | Magic 8.3 revision 105 |
| Script | generate_gds_spi_top.tcl |
| Standard Cell Types Written | 23 |
| Rectangles Processed | 50,000 |
| Output File | spi_top.gds |
| GDS Script End | Thu 03 July 2025, 12:06:12 AM IST |
| Qflow Exit Status | 0 (Success) |
| Final Qflow Status | Project is completed ✅ |

<h2>🖼️ Implementation Results</h2>

### Qflow Manager — GDS Completed
![16_Image_Post_GDS_Completion](16_Image_Post_GDS_Completion.png)

### GDSII Generation Log File
![17_Image_of_GDSii_Logfile](17_Image_of_GDSii_Logfile.png)

### Qflow Manager — All Stages Okay, Project Completed
![18_Image_Post_Completion_of_all_Process](18_Image_Post_Completion_of_all_Process.png)

### Final GDSII Layout in Magic
![19_Image_of_The_Final_GDSii_File](19_Image_of_The_Final_GDSii_File.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 06 : DRC & LVS](../06%20:%20DRC%20%26%20LVS/README.md)
