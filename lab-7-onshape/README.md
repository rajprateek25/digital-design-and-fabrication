# 3D Printing

The exercise 7 was the final exercise of the course, where students were tasks to understand about Computer-Aided Designing (CAD) in Onshape via the Onshape provided learning videos, and later create a product which can find a practical use in daily file using CAD in Onshape and then 3D printing it.

---

## Getting Acquainted with Onshape
The exercise seemed exciting. As the first step, I completed the 3 recommended trainings along with the knowledge checks and hands-on exercises provided with the courseware. This helped me become confortable with the Onshape designing environemnt, unlike _Inkscape_ where I spend so much time understanding the tool using the famous Hit-n-Trial method.

<div align="center">
  <img src="media/onshape-training-introduction-to-CAD.png" height="600"> 
</div>

---

## Deciding the Product Design
Althought the tasksheet mentioned "Smartphone accessories" as default theme, but we where given freedom to choose anything with a practice use.

I decided to design a custom wall-mounted key-holder. The inspiration for this design came from a rather unpleasant incident that happened recently where my wife locked herself out of the apartment as we lacked a designated spot for keys. By creating a custom wall-mounted key-holder rather than buying one, I can ensure that it meets our requriements and prevents us from misplacing the keys in future.

## CAD with Onshape

### Sketch 1 (base) and Extrude 1
I started _Sketch 1 (Base)_ by selecting the Right Plane as _Sketch Plane_ and creating the foundation line of the model house `Length=150 mm`. Next, I create a construction line `Length=160 mm` from the middle of the foundation line to act as the guide for the roof height. Then I created the outer edges including the sloping roof and the walls to complete the base. 

Then, I created _Extrude 1_, selecting the _Face of Sketch 1 (Base)_ and type `Solid/New` to extrude with `Depth=10 mm`.

<div align="center">
  <img src="media/sketch-1-base" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-1" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-1-side" height="600"> 
</div>

---

### Observations
To fully constraint the sketch, I utilized the following:
* _Middle point constraint_ to align the vertical construction line to the middle of the foundation line.
* _Vertical constraint_ for both the lines represeting the walls.
* _Equal constraint_ for the lines representign slop[ping roof
* _Dimension constraint_ for the vertical and horizontal lines to lock their length.

---

### Sketch 2 (hangers) and Extrude 2
For _Sketch 2 (hangers)_, I started by selecting the _Faces of Sketch 1 (Base)_ as the _Sketch Plane_ and placed 5 equidistant circles with same `Diameter=06 mm` to represent hangers. Further, I used the construction line to align them at equal distances.

Next, I created _Extrude 2_ by selecting all 5 hanger circles which constitute the _Faces of Sketch 2 (hangers)_, to extend an additional `10 mm` with respect to the _Extrude 1_. Hence, for _Extrude 2_ I selected the type `Solid/Add` and `Depth=20 mm`. 

<div align="center">
  <img src="media/sketch-2-hangers" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-2" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-2-side" height="600"> 
</div>

---

### Observations
To fully constraint the sketch, I utilized the following:
_Equal constraint_ to make all the circles and construction line segments identical in measurement.
_Dimension constraint_ to lock the distance of circles from the founation line, the radius of the circles and the distance between the circles.

---

### Sketch 3 (hanger-lips) and Extrude 3
To stop the keys from falling off of the hangers, I introduced hanger-lips in _Sketch 3 (hanger-lips)_ by selecting the _Faces of Extrude 2_ as the _Sketch Plane_. Again, I created 5 equal circle, this time with `Diameter=10 mm`, larger than the diameter of hangers so the additional material acts as a stopper or a lip. 

Thenafter, I created _Extrude 3_ to give hanger-lips some thickness by selecting the type `Solid/Add` and `Depth=3mm`.

<div align="center">
  <img src="media/sketch-3-hanger-lips" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-3" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-3-side" height="600"> 
</div>

---

### Observations
To fully constraint the sketch, I utilized the following:
_Concentric constraint_ I tilted the model slightly, selected outer face of all the hangers and then `Right-Click` > `Use` to align the hanger-lip circles along the same center as the hangers.
_Dimension constraint_ to lock the diameter of circles.

---

### Fillet 1
To strengthen the bases of sticking out hangers and hanger-lips, I introduced _Fillet 1_, by selecting all the inner circular edges of the hangers and hanger-lips constituting the edges from _Extrude 2_ and _Extrude 3_ and assigned it a `Radius=2 mm`.

<div align="center">
  <img src="media/fillet-1" height="600"> 
</div>

<div align="center">
  <img src="media/fillet-1-side" height="600"> 
</div>

---

### Observations
_Fillet_ at the base of hangers and hanger lips provides additional structural strength to the design and prevents the hangers from snapping when a bunch of keys are hanged onto them.

---

### Sketch 4 (Picture Slot) and Extrude 4
At this point, an idea struck me! The base of the key-holder appeared very bland to me, so I thought about adding a circular picture-slot, where I can fix a family picture later and personalize the design even further.

I began with the _Sketch 4 (Picutre Slot)_ and selected the _Face of Extrude 1_ as the _Sketch Plane_. At the intersection of the two construction lines created in _Sketch 1 (Base)_, I created another circle representing the picture-slot with `Diameter=70 mm`.

Now, to create a depression along the picture slot, I initiated  _Extrude 4_ selecting the circular picture slot which constitutes _Face of Sketch 4 (Picture Slot)_ to extrude, but this time selected the type  `Solid/Remove` and assigned it `Depth=2 mm`.

<div align="center">
  <img src="media/sketch-4-photoslot" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-4" height="600"> 
</div>

### Sketch 5 (Nail Slot Front) and Extrude 5
At this stage, I began thinking how to go about designing the nail slot! I started by creating the nail slot similar to what I observed on other wall mounted products like photoframes, wall clock, etc. I flipped my design vertically, and bring the back side to the front. Here, I initialized _Sketch 5 (Nail Slot)_ and selected the _Face of Extrude 1_ as the _Sketch Plane_. I drew a circle having `Diameter=08 mm` and a rectangle having `Length=10 mm` and `Width=4 mm` following the construction lines to mimic a nail slot along the center of the design.

It was now time to create _Extrude 5_ to create a depression so I selected _Faces of Sketch 5 (Nail Slot Front)_ to extrude and type `Solid/Remove`. Also, since most nail butts are roughly `2 mm` thick, I decided to keep `Depth=4mm` so the nail stays locked inside the material.

<div align="center">
  <img src="media/sketch-5-nail-slot-front" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-5" height="600"> 
</div>
---

### Observations
I realised that with the current design, the nail-butt would not travel along the rectangular slot since there is no space for the nail-butt to move vertically, as a result the key-holder may not securely hang on a nail.

To fully constraint the sketch, I utilized the following:
_Symmetric constraint_ to make the rectange aling symmetrically along the vertical construction line.
_Coincident constraint_ to make the circle and rectangle coincide at the center of the circle.
_Dimension constraint_ to lock the diameter of circle, dimensions of the rectange,a distance of the rectangle from the sloping roof.

---

### Sketch 6 (Nail Slot Base) and Extrude 6
After the realisation about the nail-slot design flaw, I created _Sketch 6 (Nail Slot Base)_ to design the base for nail slot that allows vertical movement so the nail-butt can stay locked inside securely.

Keeping the same width as the circular slot, I created two more lines vertically originating from the circle and ending exactly where the rectangle-slot ended.

Now, I had to extrude the base so I created _Extrude 6_, which sits under the _Extrude 5_. I selected _Faces of Sketch 6 (Nail Slot Base)_ to extrude and type `Solid/Remove` with `Depth=2.5 mm` 

<div align="center">
  <img src="media/sketch-6-nail-slot-back" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-6" height="600"> 
</div>

---

### Observations
To fully constraint the sketch, I utilized the following:
_Tangent constraint_ to create lines for the base originating from the circle.
_Vertical constraint_ to make the lines vertical.
_Coincident constraint_ to end the lines at the same level as the rectangular slot so the length of base and front remains the same.

---

### Sketch 7 (Name) and Extrude 7
The final edition to my design was to emboss the names at the front of the design. For this, I created _Sketch 7 (Names)_ selecting _Face of Sketch 4 (Picture Slot)_ as the _Sketch Plane_, typed the text and aligned it to the vertical center as well as horizontally between the hangers and picture slot.

I then created the last _Extrude 7_, aimed to emboss the names, selecting _Faces of Sketch 7 (Names)_ and type `Solid/Add` with `Depth=2 mm`.

<div align="center">
  <img src="media/sketch-7-names" height="600"> 
</div>

<div align="center">
  <img src="media/extrude-7" height="600"> 
</div>
### Finalizing Design


### Slicer Software


### Final Product

---

<br>

[← Back to Table of Contents](../README.md)
