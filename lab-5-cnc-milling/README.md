# 🪵 Lab 5: Subtractive Fabrication: The 8-Point Star CNC Tea Light

Welcome back to my digital fabrication chronicle! After conquering the squishy physics of uninsulated conductive threads and building automated pneumatic cushions, Exercise 5 hurled me headfirst into the heavy-hitting world of subtractive manufacturing.

The brief seemed dangerously innocent: jump into Inkscape, design a custom wooden tea light candle holder, and hand over the file to be milled out of a beautiful block of solid hardwood. Unlike laser cutting—which gracefully vaporizes material with focused light—CNC milling is a mechanical, chaotic dust storm of pure physics. It requires careful consideration of tool dimensions, material boundaries, and geometric constraints.

Naturally, to make things interesting, I decided to bypass boring circles and rectangles to design a perfectly sharp, symmetrically balanced **8-point star**.

But before the file could be processed, I had to survive an entire day of wrestling with vector paths.

---

## 🛠️ The Inkscape Existential Crisis (Design Phase)

Let's talk about the first 90% of my design timeline: **absolutely nothing**.

I spent an entire calendar day staring at Inkscape, locked in a brutal psychological standoff with vector anchors, node handles, and geometric alignment grids. For hours, my master canvas yielded exactly zero exportable files. Paths went rogue, standard shapes became warped geometry, and I managed to accidentally click buttons that I'm pretty sure changed the gravitational pull of the canvas.

Eventually, a truce was brokered between my brain and the software. After finally becoming comfortable with the interface, the vector geometry came together flawlessly to meet the lab's strict specifications:

* **The Stock Bounds:** Set a precise material canvas constraint of **100 × 150 mm** to simulate our physical hardwood block limits.
* **The Star-Spangled Vector:** Used the star tool paired with meticulous Bézier paths to engineer an 8-point geometric star layout.
* **The Candle Pocket:** Drew a perfectly centered circle set to an exact diameter of **39.5 mm**—the precise legal specification required to snugly host a standard tea light candle without letting it rattle around.

Once my digital vector baby was ready, I proudly exported the final **.svg file** and sent it over to the lab instructor, successfully concluding my hands-on battle with the digital canvas.

<div align="center">
  <img src="media/cnc-milling-inkscape-svg.png" height="600"> 
</div>

---

## 💻 CAM Automation & Hand-off

From there, my responsibility pivoted from designer to spectator. The instructor took the reigns to bridge the gap between my clean vector lines and physical toolpaths using CAM (Computer-Aided Manufacturing) software.

```text
[My Inkscape .svg File] ──> [Instructor's CAM Mapping] ──> [G-Code Execution]

```

The instructor mapped out two distinct operations based on my design:

1. **The Pocket Milling Operation:** Cleaning out the inner material of my 39.5 mm circle to create the perfect nested shelf for the candle.
2. **The Profile/Contour Outlining:** Slicing along the outside boundary of the 8-point star to drop it out of the raw stock material.

The software spit out a long scroll of **G-code coordinates**—the exact step-by-step path instructions the CNC controller needs to drive the heavy-duty stepper motors.

---

## 🪚 Machining Operations: Magic behind the Glass

With the G-code finalized, the instructor loaded the instructions onto the CNC machine, clamped down the hardwood block onto the machine bed, and executed the program.

I got to watch safely from behind the enclosure glass as the spindle spun up to its target RPM with an aggressive whine. The vacuum system kicked on, the machine executed the G-code, and the endmill sliced cleanly through the hardwood, transforming my hard-fought digital pixels into heaps of airborne sawdust.

---

## ⚠️ Engineering Insights & Lessons Learned

* **The Inside Corner Dilemma:** Even though I didn't push the button myself, I quickly learned that a spinning, cylindrical milling bit literally *cannot* cut a perfectly sharp internal 90° or acute angle. While the outer 8 tips of my star came out brilliantly sharp (because the bit tracks cleanly along the outside), the inner valleys of the star points retain a subtle micro-radius equal to the radius of the milling bit. Designing for subtractive manufacturing means always designing for tool geometry!
* **Software Constraints Matter:** The 24 hours of despair spent inside Inkscape taught me that physical manufacturing is entirely unforgiving. If a vector path isn't perfectly closed or scaled exactly to specifications (like that critical 39.5 mm candle diameter), the downstream automated fabrication process fails entirely.

---

## 📊 The Final Masterpiece

The end result is a structurally solid, geometrically striking 8-point star tea light holder. Despite the initial 24-hour standoff against Inkscape, the final 39.5 mm pocket fits the candle perfectly with just enough mechanical tolerance to swap it out easily while keeping it beautifully seated.

| | |
| :---: | :---: | 
| ![Image 1](media/IMG_8482.jpg) | ![Image 2](media/IMG_8483.jpg) | 

---

<br>

[← Back to Table of Contents](../README.md)
