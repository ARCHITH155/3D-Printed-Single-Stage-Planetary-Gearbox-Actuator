<h1 align="center">3D-Printed Single-Stage Planetary Gearbox Actuator</h1>

<p align="center">
  A fully 3D-printed 3.25:1 planetary gearbox, designed as a modular joint for a 2-DOF SCARA-style robotic arm.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/CAD-Fusion%20360-orange" alt="Fusion 360">
  <img src="https://img.shields.io/badge/Material-PLA-blue" alt="PLA">
  <img src="https://img.shields.io/badge/Ratio-3.25%3A1-green" alt="3.25:1">
  <img src="https://img.shields.io/badge/Controller-Arduino-teal" alt="Arduino">
  <img src="https://img.shields.io/badge/Cost-~%E2%82%B9436%20filament-lightgrey" alt="Cost">
</p>

<p align="center">
  <img src="IMG/hero.jpg" width="600" alt="Assembled planetary gearbox actuator">
</p>

---

## Contents

- [Overview](#overview)
- [Gallery](#gallery)
- [Design](#design)
- [Printed parts](#printed-parts)
- [Bill of materials](#bill-of-materials)
- [Assembly](#assembly)
- [Results](#results)
- [What's next](#whats-next)
- [Acknowledgements](#acknowledgements)

---

## Overview

Built as my Project Based Learning III project (B.Tech Robotics & AI, Manipal University Jaipur, 2026). Every structural part is modelled in Fusion 360 and printed in PLA, and the whole gearbox costs about ₹436 in filament.

| Item | Value |
|---|---|
| Configuration | Sun 24T + 3 × Planet 15T + Ring 54T |
| Reduction ratio | **3.25 : 1** |
| Module / pressure angle | 1.5 / 25° |
| Face width | 8 mm |
| Motor | RS-555 brushed DC |
| Driver | L298N |
| Output support | 2 × 608 2RS bearings |
| Outer diameter | 95 mm |

---

## Gallery

<p align="center">
  <img src="IMG/Exploded%20viewv2.png" width="500" alt="Exploded view of the gearbox"><br>
  <sub>Exploded view: ring gear, carrier plates, sun gear, planets and motor plate</sub>
</p>

---

## Design

**Gear ratio**, with the ring gear held fixed and the sun as input:

```
Ratio = 1 + (N_ring / N_sun) = 1 + (54 / 24) = 3.25 : 1
```

**Meshing check:** N_sun + 2 × N_planet = N_ring → 24 + 2 × 15 = 54 ✔

**Equal planet spacing:** (N_sun + N_ring) / 3 must be a whole number → 78 / 3 = 26 ✔

Three planets share the load, so each tooth carries about a third of the torque. The 25° pressure angle gives a wider, stronger tooth root than the standard 20°, which helps printed teeth.

---

## Printed parts

| Part | Outer dia. | Height | Notes |
|---|---|---|---|
| Ring body | 95 mm | 18 mm | 54T internal gear, 6 ear mounts |
| Carrier plate A | 75 mm | 4 mm | 3 axle pockets |
| Carrier plate B | 75 mm | 4 mm | 3 axle pegs, standoffs |
| Motor plate | 95 mm | 6 mm | Motor boss pocket |
| End cap | 95 mm | 8 mm | 22.2 mm bearing bore |
| Output flange | 40 mm | 4 mm | 8 mm shaft, 4 arm bolt holes |
| Sun gear hub | 10 mm | 8 mm | 3.3 mm bore, radial set screw |
| Planet gear × 3 | 24.9 mm | 8 mm | 5.2 mm bore |

<details>
<summary><b>Print settings</b></summary>

| Parts | Printer | Layer | Walls | Infill |
|---|---|---|---|---|
| Sun and planet gears | Bambu Lab | 0.10 mm | 5 | 40% gyroid |
| Carrier plates, output flange | Bambu Lab | 0.15 mm | 5 | 40% gyroid |
| Ring body, motor plate, end cap | Ender 3 | 0.20 mm | 4 | 30% gyroid |

No supports needed. Tolerance ±0.2 mm.
</details>

---

## Bill of materials

| Component | Spec | Qty |
|---|---|---|
| DC motor | RS-555 | 1 |
| Ball bearing | 608 2RS (8 × 22 × 7 mm) | 2 |
| Screws | M2.5 × 8 / 10 / 15 mm | 2 / 6 / 3 |
| Hex nuts | M2.5 | 11 |
| Adhesive | Cyanoacrylate | — |
| Lubricant | Petroleum jelly | — |
| Filament | 1.75 mm PLA | ~218 g |

---

## Assembly

1. Press a 608 bearing into the end cap.
2. Mount the motor on the motor plate (2 × M2.5 × 8).
3. Press the sun gear onto the motor shaft and tighten the set screw.
4. Grease the ring gear teeth.
5. Place the three planets inside the ring gear.
6. Fit carrier plate A, then plate B, and bolt them together (3 × M2.5 × 15).
7. Stack motor plate, ring body and end cap; fasten with 6 × M2.5 × 10.
8. Glue the output flange to carrier plate B.
9. Spin the output by hand to check, then power test.

---

## Results

- ✅ Achieved the target 3.25:1 reduction.
- ✅ Minimal gear-mesh backlash with gears printed at 0.10 mm layers.
- ✅ Smooth output rotation on the 608 bearings.
- ⚠️ With open-loop PWM on a brushed motor and a low ratio, the output was fast and hard to control at low speed. The motor stalled at low duty cycles and jumped when it broke free.

---

## What's next

The control problems above led to my next project: a 3D-printed **36:1 cycloidal actuator** driven by a brushless motor with field-oriented control (SimpleFOC) and an AS5600 encoder, built for force-controlled joints and sim-to-real experiments in MuJoCo.

For this gearbox: closed-loop position control with an AS5600 magnetic encoder and PID.

---

## Repository structure

```
stl/        Print-ready STL files
IMG/        Photos and renders used in this README
```

---

## Acknowledgements

- **Mr. Hemant Kumar**, project guide, Department of Mechatronics Engineering, Manipal University Jaipur
- **Naman Saluja**, for help with 3D printing

## License

Code: MIT · CAD and documentation: CC BY 4.0
