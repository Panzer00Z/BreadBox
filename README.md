<div align="center">

# BreadBox

**A 3D-printed modular bench station that puts a breadboard, a programmable supply, an oscilloscope and a panel meter in one instrument.**

<p><img src="https://img.shields.io/badge/Complete%20-%20in%20daily%20use-1a7f37" alt="Complete - in daily use" height="20"></p>

<p><img src="https://img.shields.io/badge/Fusion%20360-8250df" alt="Fusion 360" height="20"> <img src="https://img.shields.io/badge/3D%20Printing-8250df" alt="3D Printing" height="20"> <img src="https://img.shields.io/badge/Lab%20Tooling-8250df" alt="Lab Tooling" height="20"> <img src="https://img.shields.io/badge/Power%20Supply-8250df" alt="Power Supply" height="20"> <img src="https://img.shields.io/badge/Breadboard-8250df" alt="Breadboard" height="20"></p>

<img src="photos/18-full-front-panel.jpg" width="880" alt="Front panel with the programmable supply, the oscilloscope showing a live waveform, the voltmeter, and the touchscreen on the breadboard">

</div>

---

## At a glance

|  |  |
|---|---|
| **Focus** | Lab and bench tooling |
| **Started** | January 2026 |
| **Status** | Complete - in daily use |
| **Core hardware** | DPS5005 programmable DC supply, DSO154Pro oscilloscope, 48 V panel voltmeter/ammeter, BB1660 solderless breadboard |
| **Design tools** | Fusion 360, 3D printing, soldering, bench instrumentation |
| **Scope** | Enclosure and panel design, power distribution, integration of off-the-shelf instrument modules |

## Overview

BreadBox is a bench-top prototyping station. A full-size solderless breadboard forms the work surface, and the angled front panel carries a programmable DC supply, a small oscilloscope and a panel voltmeter/ammeter, so a prototype can be built, powered and measured from a single unit instead of a pile of separate instruments.

The panel meter is wired into the main supply feed, so it reports the voltage the station is running at and the current being drawn from it. It is a readout for the station rather than a general-purpose meter - for probing a circuit, a separate multimeter still lives on the bench next to it.

The body is a 3D-printed enclosure. The back panel is where the instruments live and the slope of the front panel is set so the displays stay readable while the unit is sitting on a desk.

The unit is built as two modules. The upper one carries the mains supply, the regulator stage and the instrument panel, and it lifts off the breadboard module. The two join on dovetail connectors on the bottom face, so the modules come apart for service and a different module can be dropped into the same footprint later. The interesting work was in the enclosure, the power distribution and getting everything to sit together without the wiring becoming a hazard.

### Goals

- Give a prototype a bench to sit on, a supply to run from and instruments to measure it.
- Keep the breadboard, the supply and the measurement gear in one footprint.
- Make the displays readable from a seated position.
- Route mains-side power once, safely, and derive the lower rails from it.
- Keep the internals repairable - every module should come out without destroying the others.
- Make the station modular, so the instrument module and the work surface can be separated and a different module dropped into the same footprint later.

### Planning and design

The form factor came first. I sketched the angle of the front panel against where the eye naturally sits at a desk, then sized the body around a standard full-size solderless breadboard so the work surface is a known quantity. The body was split into an upper instrument module and a lower breadboard module that join on dovetail connectors, so the two can be separated or swapped.

Power was the part that needed the most care. Rather than running separate adapters to each module, one internal 48&nbsp;V supply feeds the panel, and a step-down regulator stage produces the 5&nbsp;V and 3.3&nbsp;V rails the small modules need. The rail split is labelled on the housing so the wiring can be traced later.

The instrument modules were chosen as complete units so the front panel only has to carry mounting cut-outs and a USB passthrough, rather than needing its own analogue front end.

#### Design decisions

| Decision | Reasoning |
|---|---|
| Solderless breadboard as the work surface | It keeps the prototyping area standard and removable, and it means a prototype can be moved between the box and the bench without being re-soldered. |
| Angled front panel rather than a flat top | A flat panel is readable from directly above but not from a seated position. The slope fixed that. |
| Modules over a single custom front end | Buying complete instrument modules moved the risk from analogue design into integration, which is where the actual problem was. |
| Separate 5 V and 3.3 V rails | The supply module, the scope and the small breakout modules do not agree on a rail, so the rails are split and labelled. |
| Upper instrument module split from the breadboard module | The two join on dovetail connectors on the bottom face. They can be separated for service, and a different module can be dropped into the same footprint later. |
| Panel meter wired into the supply feed | It reports the voltage the station is running at and the current being drawn from it. It is a readout for the station, not a bench meter, so a separate multimeter still lives on the bench beside it. |

### Key components

| Component | Specification | Qty |
|---|---|---|
| DPS5005 | Programmable DC supply module, buck, 50 V / 5 A, colour display, rotary encoder, CV/CC | 1 |
| ZEEWEII DSO154Pro | 2.4-inch digital oscilloscope, 1 MHz digital / 18 MHz analogue bandwidth, signal generator | 1 |
| DC 100 V / 10 A panel meter | Voltmeter and ammeter with LED display, wired into the main supply feed | 1 |
| BB1660 solderless breadboard | 1660 tie-points, 8 power rails, 165 x 110 mm plug-in board | 1 |
| MEAN WELL LRS-100-48 | Internal mains supply, 48 V / 2.3 A / 110 W | 1 |
| IEC C14 inlet module | Mains inlet with 10 A switch and 10 A / 15 A fuse on an 18 AWG lead | 1 |
| Step-down regulators | Buck converters for the 5 V and 3.3 V rails | 2 |
| Toroidal inductor and heatsink | On the regulator stage | 1 |
| 4 mm banana jack sockets | M4 x 36 copper terminal, panel and rail outputs | 5 |
| DSN-UC286 USB hub | Front-panel USB passthrough | 1 |
| Test hook clip leads | Silicone male/female test leads for the breadboard | 10 |
| Dupont to banana jumper cables | 26 AWG silicone, male Dupont to stackable banana plug | 10 |
| 3D-printed enclosure | Fused filament, angled front panel, dovetail module split | 1 |
| Pico and small modules | Test articles and instrumentation | varied |

### Build and testing

The build went from printing the enclosure, through fitting the instruments and wiring the power rails, to the finished unit on the bench with a breadboard full of test circuitry.

<div align="center">

<table>
<tr>
<td width="33%" align="center"><img src="photos/01-enclosure-printing-on-the-bed.jpg" width="280" alt="Blue 3D-printed enclosure frame sitting on the bed of a 3D printer mid-print"><br><sub>Printing the enclosure</sub></td>
<td width="33%" align="center"><img src="photos/02-first-assembly-open.jpg" width="280" alt="First assembled unit with the front panel open, showing the control panel and the breadboard area"><br><sub>First assembly</sub></td>
<td width="33%" align="center"><img src="photos/03-side-profile-first-assembly.jpg" width="280" alt="Side view of the assembled unit on a desk"><br><sub>Side profile</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/04-internal-supply-and-breadboard.jpg" width="280" alt="Interior of the unit showing the enclosed power supply and the breadboard"><br><sub>Internals: supply and work surface</sub></td>
<td width="33%" align="center"><img src="photos/05-top-down-panel-layout.jpg" width="280" alt="Top-down view of the open unit showing the breadboard in the centre and the control panel at the front"><br><sub>Panel and work surface layout</sub></td>
<td width="33%" align="center"><img src="photos/06-instrument-bay-open.jpg" width="280" alt="Instrument bay showing the display module, the regulator board with heatsink and toroidal inductor, and the mains switch"><br><sub>Instrument bay</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/07-empty-enclosure.jpg" width="280" alt="Empty printed enclosure bottom with the internal ribs and standoffs visible"><br><sub>Empty enclosure</sub></td>
<td width="33%" align="center"><img src="photos/08-rear-panel-detail.jpg" width="280" alt="Printed rear panel with its fixing points"><br><sub>Rear panel</sub></td>
<td width="33%" align="center"><img src="photos/09-internal-supply-installation.jpg" width="280" alt="Interior with the power supply installed and wired"><br><sub>Supply installed</sub></td>
</tr>
</table>
</div>

### Results

**What went well**

- Printing the enclosure first was the right order - the printed body set the mounting pattern for everything else, so the modules were drilled to the part rather than the part being adapted to the modules.
- The angled panel is genuinely more usable than a flat one, and the difference is obvious the first time you use it while seated.
- Driving the instruments from one internal supply rather than several adapters removed a cluster of wall-wart cables from the desk.
- The breadboard and the instrument rail sit close enough together that a probe reaches both without stretching.
- The dovetail split paid for itself immediately - the upper module lifts straight off the breadboard module, so the two can be worked on separately and a different module can go into the same footprint later.
- The unit has stayed in daily use, which is the only real test of a bench tool.

**What went wrong**

- The first internal wiring pass had the regulators wired before the rail labels were settled, so the harness had to be pulled and redone.
- The USB hub was added late and its lead crosses the interior of the case, where it is still in the way.
- A small aux board was hand-soldered directly in the enclosure rather than on a daughterboard, so it is awkward to remove if it fails.
- The rear of the case has no cover - it is closed with the panel itself, which means every service job means taking the front panel off.

**What I would change in the next iteration**

- Add a proper rear cover with a screw fix, so the internals can be reached without disturbing the front panel.
- Route the USB hub lead along the case wall in a clip.
- Build a small daughterboard for the auxiliary circuitry instead of hand-wiring it in place.
- Raise the breadboard slightly and add a lip so a prototype cannot slide down onto the panel.
- Add a second, independently switched output from the programmable supply so a project can be powered down without switching the whole box off.
- Use the dovetail interface for what it was left for - a different instrument module, or a different work surface in the same footprint.

### Full build gallery

<div align="center">

<table>
<tr>
<td width="33%" align="center"><img src="photos/01-enclosure-printing-on-the-bed.jpg" width="280" alt="Blue 3D-printed enclosure frame sitting on the bed of a 3D printer mid-print"><br><sub>Printing the enclosure</sub></td>
<td width="33%" align="center"><img src="photos/02-first-assembly-open.jpg" width="280" alt="First assembled unit with the front panel open, showing the control panel and the breadboard area"><br><sub>First assembly</sub></td>
<td width="33%" align="center"><img src="photos/03-side-profile-first-assembly.jpg" width="280" alt="Side view of the assembled unit on a desk"><br><sub>Side profile</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/04-internal-supply-and-breadboard.jpg" width="280" alt="Interior of the unit showing the enclosed power supply and the breadboard"><br><sub>Internals: supply and work surface</sub></td>
<td width="33%" align="center"><img src="photos/05-top-down-panel-layout.jpg" width="280" alt="Top-down view of the open unit showing the breadboard in the centre and the control panel at the front"><br><sub>Panel and work surface layout</sub></td>
<td width="33%" align="center"><img src="photos/06-instrument-bay-open.jpg" width="280" alt="Instrument bay showing the display module, the regulator board with heatsink and toroidal inductor, and the mains switch"><br><sub>Instrument bay</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/07-empty-enclosure.jpg" width="280" alt="Empty printed enclosure bottom with the internal ribs and standoffs visible"><br><sub>Empty enclosure</sub></td>
<td width="33%" align="center"><img src="photos/08-rear-panel-detail.jpg" width="280" alt="Printed rear panel with its fixing points"><br><sub>Rear panel</sub></td>
<td width="33%" align="center"><img src="photos/09-internal-supply-installation.jpg" width="280" alt="Interior with the power supply installed and wired"><br><sub>Supply installed</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/10-regulator-stage-detail.jpg" width="280" alt="Close-up of the regulator stage: heatsink, toroidal inductor, regulator board and the alligator clips carrying output"><br><sub>Regulator stage</sub></td>
<td width="33%" align="center"><img src="photos/11-power-rail-distribution.jpg" width="280" alt="Power distribution with the rail breakout box and its labelled connections"><br><sub>Power rail distribution</sub></td>
<td width="33%" align="center"><img src="photos/12-bench-use-with-prototype.jpg" width="280" alt="Unit open on the desk with a prototype on the breadboard and the programmable supply running"><br><sub>Bench use with a prototype</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/13-front-panel-complete.jpg" width="280" alt="Front panel with the programmable supply, display and meter, and the breadboard below"><br><sub>Front panel complete</sub></td>
<td width="33%" align="center"><img src="photos/14-panel-in-use.jpg" width="280" alt="A hand pointing at the panel, showing the readout while the unit is in use"><br><sub>Using the panel</sub></td>
<td width="33%" align="center"><img src="photos/15-supply-readout.jpg" width="280" alt="Close-up of the supply readout showing voltage and current with the output clips attached"><br><sub>Supply readout</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/16-side-view-with-badge.jpg" width="280" alt="Side view of the finished unit with its side badge"><br><sub>Side view</sub></td>
<td width="33%" align="center"><img src="photos/17-dc-jack-detail.jpg" width="280" alt="Barrel power jack mounted on the side of the enclosure"><br><sub>DC jack</sub></td>
<td width="33%" align="center"><img src="photos/19-complete-station-on-the-bench.jpg" width="280" alt="The complete station open on the bench with the touchscreen running on the breadboard"><br><sub>Complete station</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/20-adjusting-the-supply.jpg" width="280" alt="A hand on the rotary encoder of the programmable supply"><br><sub>Adjusting the supply</sub></td>
<td width="33%" align="center"><img src="photos/21-aux-board-in-place.jpg" width="280" alt="The auxiliary board set down beside the open enclosure"><br><sub>Auxiliary board</sub></td>
<td width="33%" align="center"><img src="photos/22-internal-wiring-overview.jpg" width="280" alt="Interior overview showing the power board and the cable runs"><br><sub>Internal wiring overview</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/23-station-on-the-bench-with-multimeter.jpg" width="280" alt="The station on the bench next to an orange multimeter"><br><sub>Station alongside a bench multimeter</sub></td>
<td width="33%" align="center"><img src="photos/24-station-side-view-on-desk.jpg" width="280" alt="Side view of the station on the desk"><br><sub>Station on the desk</sub></td>
<td width="33%" align="center"><img src="photos/25-rear-of-the-enclosure.jpg" width="280" alt="Closed rear of the enclosure showing the power switch and the incoming cable"><br><sub>Rear of the enclosure</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/26-panel-held-in-hand.jpg" width="280" alt="The front panel held in hand, showing the supply, oscilloscope and voltmeter"><br><sub>The panel as a unit</sub></td>
<td width="33%" align="center"><img src="photos/27-station-fully-assembled.jpg" width="280" alt="The fully assembled station on the bench"><br><sub>Fully assembled</sub></td>
<td width="33%" align="center"><img src="photos/28-front-panel-reinforcement.jpg" width="280" alt="Interior of the upper module showing the reinforcing strips around the front panel perimeter"><br><sub>Front panel perimeter reinforcement</sub></td>
</tr>
<tr>
<td width="33%" align="center"><img src="photos/29-station-on-the-desk.jpg" width="280" alt="The station on the desk in front of a monitor, next to a keyboard"><br><sub>Station at the desk</sub></td>
</tr>
</table>
</div>

### Credits and references

- Enclosure designed in Fusion 360. Printing done on a BambuLabs X1C.

---

<p align="center"><sub>Part of the <a href="https://github.com/Panzer00Z">Panzer00Z</a> hardware portfolio &middot; <a href="https://github.com/Panzer00Z/Panzer00Z">profile &rarr;</a></sub></p>
