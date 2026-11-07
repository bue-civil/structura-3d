# STRUCTURA 3D (v1)

An interactive 3D steel frame builder and stability simulator for school students. Build a frame from columns, beams, braces and floor slabs, then load it with wind and watch how it sways, twists or collapses.

**Live page:** https://bue-civil.github.io/structura-3d/

## Features
- **Build in 3D** on a 4 × 4 grid (4 m bays), up to 4 storeys (3.5 m). A read-only 2D floor plan follows each level.
- **Continuous beams and floors:** beams that meet without a column act as one continuous beam (each piece still counts as a beam in cost and steel mass), and beams and columns are drawn bending smoothly using the end rotations from the analysis. A floor placed between two continuous beams with no beam or column across the middle fills the whole area in one tap, is drawn as one slab with no gap, and is deleted as one.
- **Footings:** every ground-floor column automatically sits on a 0.6 × 0.6 m concrete pedestal over a 1.6 × 1.6 × 0.45 m isolated pad footing, with grout, a steel base plate and four anchor bolts. The ground-floor slab is see-through so the footings can be seen below it (dashed on the ground floor plan, included in the STL export).
- **Connections:** beam-to-column joints are realistic fin-plate shear connections ($5) or rigid moment connections ($10); click a joint with the Joint tool to toggle it. Every brace gets bolted gusset plates at both ends automatically.
- **Real 3D frame analysis:** direct stiffness method with 6 degrees of freedom per joint. Pinned base plates, pinned or rigid beam ends, pin-ended braces, and floor slabs acting as rigid diaphragms.
- **Wind loading:** Calm, Strong Wind (100 km/h), Storm (150 km/h) and Hurricane (250 km/h), blowing along +X or +Y, plus notional sway loads from gravity.
- **Earthquakes:** switch **Load** to Earthquake and pick **Mild** (PGA 0.10 g) or **Severe** (PGA 0.35 g), shaking along X or Y. The equivalent lateral force method applies storey forces in proportion to weight × height, with the natural period from Rayleigh's method on the 3D model and a design spectrum (plateau 2.5 × PGA up to 0.6 s). Response is elastic (no ductility credit), so braced frames survive and tall moment frames sway or collapse. In 3D the ground shakes and the building sways at its own period; damaged members give way once the strong shaking arrives. Drift above 0.5 % (H/200) is flagged as damage.
- **Torsion:** floors translate and rotate. The plan shows the centre of rigidity (CR), the wind resultant and the eccentricity between them, and a Torsion meter flags storeys where one column drifts more than 1.2× the average (ASCE 7 torsional irregularity).
- **Moment frames vs bracing:** moment frames resist sway by bending and come out far more flexible than braced frames, as in reality.
- **Failure checks:** mechanisms (including floors spinning when all bracing lines meet at one point), members yielding, and excessive drift with P-Δ amplification. Failed members fall.
- **Torsion demo:** the Sample button loads a frame braced on grid lines 2 and A with flexible moment frames on lines 3 and C, so the floors twist under wind. Brace lines 3 and C to fix it.
- **Phones and tablets:** tap a grid point to place the selected member, and long-press any member to delete it. **Hide all** clears every panel so the 3D model fills the screen while the last tool you picked (column, beam, brace…) stays active; a Run button stays on screen. **Mobile mode** (opens automatically on phones, with the earthquake test as the default, a Mild / Severe switch, and a card showing footprint area, total floor area and total cost) keeps only the member buttons (Column, Beam, Brace, Floor), the Joint and Delete tools, Run and the 2D plan / 3D views, with a thumb-sized bar at the bottom of the screen and a faint BUE logo watermark. Keyboard: H = Hide all, M = Mobile mode.
- **Plan and side views:** click the **Plan Level** label to switch the 2D pane to **Side S-N** (elevations of grid lines 1–4) and **Side E-W** (grid lines A–D). Side views show columns, beams, braces, slab edges, joints and footings, and the deformed shape while a test runs; the 3D view highlights the chosen grid line.
- **Save and Open:** save the structure as a small `.json` project file, then open it later or send it to someone else to open in STRUCTURA. In Mobile mode these are two icon buttons at the top-right of the 3D view.
- **Header figures:** total cost, footprint area, total floor area, steel mass, drift and torsion.
- **Exports:** PNG screenshot, 3D-printable binary STL (1:100, mm) and IFC 2x3 for Revit.

## Notes
- Sections: H-section columns, W-section beams and round HSS braces in S355-type steel (fy = 345 MPa). Slabs carry 5 kPa.
- Deformations in 3D are exaggerated so students can see them; the badge shows the scale.
- Progress is saved in each browser's local storage, so each student's structure stays on their own device.
- Single self-contained `index.html`; three.js r128, Tone.js and Tailwind are loaded from CDNs.
