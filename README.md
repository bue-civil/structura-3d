# STRUCTURA 3D (v1)

An interactive 3D steel frame builder and stability simulator for school students. Build a frame from columns, beams, braces and floor slabs, then load it with wind and watch how it sways, twists or collapses.

**Live page:** https://bue-civil.github.io/structura-3d/

## Features
- **Build in 3D** on a 4 × 4 grid (4 m bays), up to 4 storeys (3.5 m). A read-only 2D floor plan follows each level.
- **Connections:** beam-to-column joints are realistic fin-plate shear connections ($5) or rigid moment connections ($10); click a joint with the Joint tool to toggle it. Every brace gets bolted gusset plates at both ends automatically.
- **Real 3D frame analysis:** direct stiffness method with 6 degrees of freedom per joint. Pinned base plates, pinned or rigid beam ends, pin-ended braces, and floor slabs acting as rigid diaphragms.
- **Wind loading:** Calm, Strong Wind (100 km/h), Storm (150 km/h) and Hurricane (250 km/h), blowing along +X or +Z, plus notional sway loads from gravity.
- **Torsion:** floors translate and rotate. The plan shows the centre of rigidity (CR), the wind resultant and the eccentricity between them, and a Torsion meter flags storeys where one column drifts more than 1.2× the average (ASCE 7 torsional irregularity).
- **Moment frames vs bracing:** moment frames resist sway by bending and come out far more flexible than braced frames, as in reality.
- **Failure checks:** mechanisms (including floors spinning when all bracing lines meet at one point), members yielding, and excessive drift with P-Δ amplification. Failed members fall.
- **Torsion demo:** the Sample button loads a frame braced on grid lines 2 and A with flexible moment frames on lines 3 and C, so the floors twist under wind. Brace lines 3 and C to fix it.
- **Phones and tablets:** tap a grid point to place the selected member. **Hide all** clears every panel so the 3D model fills the screen while the last tool you picked (column, beam, brace…) stays active; a Run button stays on screen. **Mobile mode** (opens automatically on phones) keeps only the member buttons (Column, Beam, Brace, Floor), the Joint tool, Run and the 2D plan / 3D views, with a thumb-sized bar at the bottom of the screen. Keyboard: H = Hide all, M = Mobile mode.
- **Exports:** PNG screenshot, 3D-printable binary STL (1:100, mm) and IFC 2x3 for Revit.

## Notes
- Sections: H-section columns, W-section beams and round HSS braces in S355-type steel (fy = 345 MPa). Slabs carry 5 kPa.
- Deformations in 3D are exaggerated so students can see them; the badge shows the scale.
- Progress is saved in each browser's local storage, so each student's structure stays on their own device.
- Single self-contained `index.html`; three.js r128, Tone.js and Tailwind are loaded from CDNs.
