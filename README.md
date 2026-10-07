SPACETIME DRIVE

Public engineering showcase repository
Computational mechanics, finite-element development, solver integration, and the transition from a calibrated digital model toward physical laboratory validation.



Project Summary

SPACETIME DRIVE is the name of an ongoing engineering and research project developed by Fatih Yaylacı, a Computer Engineering student at Goce Delčev University.

The current verified engineering work focuses on a precision very-low-net-stiffness mechanical research system built around guide flexures, preloaded anti-spring elements, a moving shuttle, finite-element analysis, prestressed modal analysis, tolerance studies, solver verification, and future physical measurement.

The engineering objective is to approach a very small positive net stiffness while maintaining a stable operating point:

Positive guide stiffness
        +
Negative anti-spring tangent stiffness
        ↓
Very low positive net stiffness

The intended condition is:

k_net → 0+

while still maintaining:

k_net > 0

Important Scientific Scope

The project name is SPACETIME DRIVE, but this repository does not claim experimental proof of warp drive, faster-than-light propulsion, antigravity, gravity shielding, or reactionless propulsion.

The current validated scope is computational and mechanical engineering: modeling, simulation, finite-element development, modal analysis, robustness evaluation, solver integration, and preparation for a future physical laboratory demonstrator.

Physical experimental validation is the next major phase.

Public Repository Notice

This repository is a selected public showcase, not the complete research archive.

The full SPACETIME DRIVE research master repository is maintained privately.

The private master contains the complete engineering history, full stage archive, raw solver evidence, detailed CAD assets, internal development files, research notes, unreleased technical material, integrity manifests, and other records that are intentionally not published here.

This public repository contains only material selected for demonstration, technical communication, reproducibility at an appropriate public level, and potential collaboration.

Current Engineering Status

Area

Status

Computer-side engineering

Complete to current retained computational release

Final calibrated FE release candidate

PASS

Prestressed modal computational gate G12

PASS

Robust critical-corner gate

PASS

Final high-resolution model

22,400 C3D20R elements

Real CalculiX execution through WSL

Verified

Engineering simulator

Working

H151 computational FE release

Locked internally

H152 physical-validation package

Prepared internally

G13 moving-assembly physical weighing

Open / physical phase

G14 moving cable/fiber mass measurement

Open / physical phase

G15 minimum physical clearance witness

Open / physical phase

Formal asymptotic mesh convergence

Open as a separate strict numerical item

The open physical gates do not invalidate the completed computational results. They define the next experimental layer of the program.

Final Computational Reference

The current retained high-resolution reference uses:

Element type:                 C3D20R
Element count:                22,400
Nominal preload:              10.408909815 N/blade
Mode-1 eigenvalue:            +2.657947
Mode-1 natural frequency:     0.2594737 Hz
Equivalent modal stiffness:   0.575494432 N/m
Target stiffness:             0.576054484 N/m
Critical-corner stiffness:    0.136281853 N/m
Required minimum stiffness:   0.100000000 N/m

The retained nominal stiffness differs from the target by approximately:

-0.000560052 N/m

or about:

-0.0972 %

The final nominal operating point remains positive and stable.

Reference Mechanical Architecture

The present digital reference architecture contains:

four guide flexure blades,

two anti-spring blades,

a moving shuttle / moving assembly,

preload control,

mechanical clamps and hard stops,

future actuator integration,

future force measurement,

future displacement measurement,

DAQ integration,

and a computer-side analysis workflow.

Guide Flexures

Quantity:   4
Length:     55 mm
Thickness:  0.09 mm
Width:      10 mm

Anti-Spring Blades

Quantity:   2
Length:     45 mm
Thickness:  0.30 mm
Width:      8 mm

Material Reference

Elastic modulus:  113800 N/mm²
Poisson ratio:    0.34
Density:          4.43e-9 tonne/mm³

Moving Assembly Reference

Reference moving mass: 0.215225557593 kg

The complete physical moving mass, including real cable/fiber contributions, remains a future measurement task.

A Major Modeling Finding

An important part of the project was identifying a systematic discrepancy in the original CalculiX B32R beam model.

The early beam model produced approximately 53.6% higher bending-related stiffness and buckling response than the analytical reference when the physical Poisson ratio was used.

Instead of changing the material properties merely to force agreement, the project followed a root-cause process and migrated to a true three-dimensional C3D20R continuum model while retaining the physical material value:

ν = 0.34

This transition is one of the key reasons the current computational release uses continuum solid elements rather than the original final beam representation.

Mesh Refinement and Calibration

The continuum model was refined through multiple element counts, including:

896
3,584
8,064
14,336
22,400 elements

Each refinement stage was evaluated for operating-point movement, preload recalibration, modal response, critical-corner stability, and numerical consistency.

The current retained final calibration uses:

22,400 C3D20R elements
10.408909815 N/blade

Formal asymptotic mesh convergence is intentionally still recorded as OPEN. This is kept separate from the calibrated engineering-release status.

Engineering Simulator

The project includes a desktop SPACETIME DRIVE — Engineering Simulator.

The simulator includes:

Overview — current retained computational reference,

Quick Simulation — reduced-order local parameter exploration,

Real CalculiX — real finite-element solver execution through WSL,

History — recorded solver runs,

Evidence — retained engineering-gate summary.

Overview



Quick Simulation



The quick simulation is a calibrated local engineering estimate. It is not a replacement for a fresh full finite-element solve.

Real CalculiX



The real solver workflow is conceptually:

Windows application
        ↓
WSL
        ↓
CalculiX
        ↓
Finite-element solve
        ↓
DAT result
        ↓
Automatic parsing
        ↓
Engineering result display

Solver detection has been verified at:

/usr/bin/ccx

A solver-ready message verifies that the CalculiX executable is available. It does not by itself mean that a new simulation has finished.

Run History



The application can retain solver-run values such as job name, preload, eigenvalue, natural frequency, equivalent stiffness, stability state, and related traceability data.

Evidence Summary



The evidence view distinguishes completed computational gates from the measurements that still require physical laboratory work.

Computational vs Physical Evidence

This project intentionally separates different evidence layers.

Computational evidence includes finite-element inputs, solver outputs, calibration, modal results, tolerance studies, robustness testing, and reproducible software execution.

Physical evidence will require manufactured hardware and real measurements such as moving mass, cable/fiber contribution, clearances, static force-displacement behavior, natural frequency, repeatability, damping, and uncertainty.

The next stage is not to replace the simulation. The next stage is to compare it with reality.

Physical Validation Roadmap

Computational reference
        ↓
Manufacturing
        ↓
Metrology
        ↓
Mechanical assembly
        ↓
Moving-mass measurement
        ↓
Cable/fiber characterization
        ↓
Clearance verification
        ↓
Preload calibration
        ↓
Sensor integration
        ↓
Static testing
        ↓
Dynamic modal testing
        ↓
Experimental stiffness and frequency
        ↓
FE ↔ experiment correlation
        ↓
Model update

Future laboratory instrumentation is expected to include appropriate combinations of force measurement, displacement measurement, actuation, DAQ, calibration equipment, and mechanical metrology.

Public Presentation

A public-facing conference presentation is included in:

docs/SPACETIME_DRIVE_Public_Conference_Presentation.pptx

It is intended to communicate the project development path, computational engineering, major modeling findings, final retained results, simulator workflow, and physical-validation roadmap.

Repository Structure

SPACETIME-DRIVE-PUBLIC/
│
├── README.md
├── README_TR.md
├── PROJECT_STATUS.md
├── SCIENTIFIC_SCOPE.md
├── COLLABORATION.md
├── SECURITY.md
├── RIGHTS.md
├── CITATION.cff
├── .gitignore
├── .gitattributes
│
├── assets/
│   └── screenshots/
│       ├── overview.jpg
│       ├── quick-simulation.jpg
│       ├── real-calculix.jpg
│       ├── history.jpg
│       └── evidence.jpg
│
└── docs/
    └── SPACETIME_DRIVE_Public_Conference_Presentation.pptx

Reproducibility and Evidence Integrity

The internal research process preserves, where applicable:

model inputs,

solver version,

material properties,

mesh information,

preload values,

result files,

post-processing logic,

timestamps,

and cryptographic hashes.

The complete integrity records and locked computational release packages are maintained in the private master repository and are not reproduced in full here.

Collaboration

The next phase can benefit from collaboration in areas such as:

mechanical engineering,

flexure mechanisms,

quasi-zero-stiffness systems,

finite-element analysis,

precision manufacturing,

experimental mechanics,

instrumentation,

metrology,

sensors and DAQ,

vibration testing,

control systems,

uncertainty analysis,

and FE-to-experiment correlation.

Researchers, engineers, academics, laboratories, and students interested in these areas are welcome to make contact.

Contact

Fatih Yaylacı
Computer Engineering
Goce Delčev University
North Macedonia / Türkiye

Email: fatihyaylaci7@gmail.com
GitHub: https://github.com/fatihyaylacimk
LinkedIn: https://www.linkedin.com/in/fatih-yaylac%C4%B1-7ab821182
YouTube: tech LOGİC EXPLAined

Rights and Use

This public repository is provided for technical communication, research visibility, and collaboration.

No open-source license is granted unless a specific file or future release explicitly states otherwise. See RIGHTS.md.

The private master repository, unreleased technical assets, detailed CAD, raw evidence packages, and internal research records are not part of this public distribution.

Final Statement

The current computer-side engineering has been completed to the retained computational release level.

The next major objective is:

BUILD → MEASURE → COMPARE → UPDATE

The goal is to determine how closely the future physical system reproduces the computationally predicted low-net-stiffness behavior.

SPACETIME DRIVE
Fatih Yaylacı — Goce Delčev University, Computer Engineering
Public Engineering Showcase — Computational Release → Physical Validation
