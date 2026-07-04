# 3D Printing

The exercise 7 was the final exercise of this course, where students were tasks to understand about Computer-Aided Designing (CAD) in Onshape via the Onshape provided learning videos, and later design a product with practical use in daily life and then 3D printing it.

---

## Making Acquaintance with Onshape
The exercise seemed exciting. As the first step, I completed the 3 recommended trainings along with the included knowledge checks and hands-on exercises provided in the courseware. This helped me become confortable with the Onshape designing environemnt, unlike _Inkscape_ where I spend major chunk of time understanding the tool using the age-old "Hit-n-Trial" method.

<div align="center">
  <img src="media/onshape-training-introduction-to-CAD.png" height="600"> 
</div>

---

## 3D Modelling in Onshape

---

### Deciding the Product Design
Althought the task brief mentioned "Smartphone accessories" as default theme, but we where given freedom to choose anything with a practice use.

I decided to design a custom wall-mounted key-holder. The inspiration for this design came from a rather unpleasant incident that happened recently where my wife locked herself out of the apartment as we lack a designated spot for keys. By creating a custom wall-mounted key-holder instead of buying one, we can customise it to our liking and need, and prevent misplacing the keys in future.

---

### Sketching the Basic Outline
I kicked-off designing the key-holder by creating the first sketch to create a *schematic* matching the shape of a house.

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 1 (Base) | Right plane | Extrude 1 | Face of Sketch 1 (Base) | Solid/New | 10 mm |

---

<div align="center">

  |  Sketch 1 (Base) | Extrude 1 (View 1) | Extrude 1 (View 2) | 
  | :---: | :---: | :---: |
  | <img src="media/sketch-1-base.png" height="600"> | <img src="media/extrude-1.png" height="600"> | <img src="media/extrude-1-side.png" height="600"> |
  
</div>

---

### Building the Hanger and Hanger-Lips
After setting up the basic shape, I placed 5 equal sized circles having `diameter=06 mm`, placed at equal distance from each other and from the foundation line of the basic outline. These circles are where the material will extend to create key hangers. Then, I created 5 additional equal sized circles having `diameter=10 mm` and made them align concentrically to the hanger cirlces. Being slighltly larger in diameter, these circles after being extended will act as the hanger-lips which will prevent the keys from slipping off of the hangers.

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 2 (Hangers) | Faces of Sketch 1 (Base) | Extrude 2 | Faces of Sketch 2 (Hangers) | Solid/Add | 20 mm |
| Sketch 3 (hanger-lips) | Faces of Extrude 2 | Extrude 3 | Faces of Sketch 3 (Hanger Lips) | Solid/Add | 03 mm |

---

<div align="center">

  |  Sketch 2 (Hangers) | Extrude 2 (View 1) | Extrude 2 (View 2) | 
  | :---: | :---: | :---: |
  | <img src="media/sketch-2-hangers.png" height="600"> | <img src="media/extrude-2.png" height="600"> | <img src="media/extrude-2-side.png" height="600"> |
  
</div>

---

<div align="center">

  |  Sketch 3 (Hanger Lips) | Extrude 3 (View 1) | Extrude 3 (View 2) | 
  | :---: | :---: | :---: |
  | <img src="media/sketch-3-hanger-lips.png" height="600"> | <img src="media/extrude-3.png" height="600"> | <img src="media/extrude-3-side.png" height="600"> |
  
</div>

---

### Fortifying Hangers using Fillets
In order to introduce additonal strength in the design, I added fillets at the the inner edges of the hangers and hanger-lips.

_Fillet 1_  and assigned it a `Radius=2 mm`.

| Fillet Name | Fillet Type | Entities to Fillet | Measurement | Control | Radius |
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Fillet 1 | Edge | Edge of Extrude 2/3 | Radius | Distance | 02 mm |

---

<div align="center">

  |  Fillet (View 1) | Fillet (View 2) | 
  | :---: | :---: |
  | <img src="media/fillet-1.png" height="600"> | <img src="media/fillet-1-side.png" height="600"> | '

</div>

---

### Space to Paste a Mug-Shot
At this stage, I could see my design slowly taking shape. The design seemed quite bland and suddenly an idea struck me! I decided to add circular picture-slot having `diameter=70 mm`, which can be used to place a desired picture after fabricaion, to give the product even more personalized look and feel.

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 4 (Picture Slot) | Face of Extrude 1 | Extrude 4 | Face of Sketch 4 (Picture Slot) | Solid/Remove | 02 mm |

---

<div align="center">

  |  Sketch 4 (Picture Slot) | Extrude 4 | 
  | :---: | :---: |
  | <img src="media/sketch-4-photoslot.png" height="600"> | <img src="media/extrude-4.png" height="600"> | '

</div>

---

### Solving the Nail-Slot Puzzle
My design was almost at the finish line. Since I was designing the key-holder to be mounted on a wall, it was important include a nail-slot. I researched and found out that mostly nails used in household applications come with a nail-butt having `thickness=02 mm`. So, I creating the nail-slot at the backside of the key-holder and kept `thickness=04 mm` to keep the nail safely locked inside the material.

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 5 (Nail Slot) | Face of Extrude 1 | Extrude 5 | Faces of Sketch 5 (Nail Slot Front) | Solid/Remove | 04 mm |

---

<div align="center">

  |  Sketch 5 (Nail Slot Front) | Extrude 5 | 
  | :---: | :---: |
  | <img src="media/sketch-5-nail-slot-front.png" height="600"> | <img src="media/extrude-5.png" height="600"> | '

</div>

---

As soon as Extrude 5 rendered the output, the realization dawned that the nail-slot I created has a design flaw and is incomplete. The current design allowed the nail-butt to get lodged but it didn't provide any mechanism to lock it in place. To address this issue, I had to create a nail-slot base component, which was wider than the nail-slot front to allow the nail-butt to move vertically and lock it in place. 

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 6 (Nail Slot Base) | Face of Extrude 5 | Extrude 6 | Faces of Sketch 6 (Nail Slot Base) | Solid/Remove | 2.5 mm |

---

<div align="center">

  |  Sketch 6 (Nail Slot Base) | Extrude 6 | 
  | :---: | :---: |
  | <img src="media/sketch-6-nail-slot-base.png" height="600"> | <img src="media/extrude-6.png" height="600"> | '

</div>

---

### Giving the Design Our Name
The final addition to the design was to emboss our names at the front key-holder. 

| Sketch Name | Sketch Plane | Extrude Name | Extrude Face | Extrude Type | Extrude Depth | 
| :--- | :--- | :--- | :--- | :--- | ---: | 
| Sketch 7 (Names) | Face of Sketch 4 (Picture Slot) | Extrude 7 | Faces of Sketch 7 (Names) | Solid/Add | 02 mm |

---

<div align="center">

  |  Sketch 7 (Name) | Extrude 7 | 
  | :---: | :---: |
  | <img src="media/sketch-7-name.png" height="600"> | <img src="media/extrude-7.png" height="600"> | '

</div>

---

### Finalising the Design
Here's how the CAD model of the wall-mounted key-holder I imagined, finally looked in Onshape:

---
<div align="center">
  <video src= "https://github.com/user-attachments/assets/ff8d8902-4b0d-4dd3-bbf7-61ebe8593c45" controls autoplay muted loop style="max-width: 100%;"> </video> 
</div>

---

To export the 3D Model, `Right-Click` > `Export` on the Part visible under Parts list in the left pane. Provide a custom file name, select format as STEP and click `Export`. 

<div align="center">

  |  Right-Click on Part | Export STEP file | 
  | :---: | :---: |
  | <img src="media/export-1.png" height="600"> | <img src="media/export-2.png" height="600"> | '

</div>

---

### Importing the Model in QIDI Studio (The Slicing Software)
After importing the Onshape project into the slicer software, I positioned the _backside_ on the build plate - which was the flattest face of the design - to maximize adhesion. Additionally, for the hangers and th  nail-slot, I enabled tree-type supports. Lastly, I saved the project 3MF file and handed it over to the tutor for 3D printing.

<div align="center">

  |  Importing into Slicer | Print Orientation | Slice Plate | 
  | :---: | :---: | :---: |
  | <img src="media/slicer-1.png" height="600"> | <img src="media/slicer-2.png" height="600"> | <img src="media/slicer-3.png" height="600"> |
  
</div>

---

## Final Product
The key-holder turned out just as I imagined, and designed. It was a fun experience ideating and then fabricating something of utility on my own.

<div align="center">

  |  Supports | Finished Product | Testing Nail-Slot | Stress-Test |  
  | :---: | :---: | :---: | :---: |
  | <img src="media/final-1.jpg" height="600"> | <img src="media/final-2.jpg" height="600"> | <img src="media/final-3.jpg" height="600"> | <img src="media/final-4.jpg" height="600"> | 
  
</div>

---

## Observations

---

### Modelling in Onshape
* Selecting the correct _Sketch Plane_ for every sketch is of utmost important.
* Sketches must be fully constraint. Sketches with errors appear with a blue dot in the features pane.
* In order to use the components residing on different plane, tilt the model slightly, select the desired component and then `Right-Click` > `Use` to apply constraints across planes, example for hangers and hanger-lips.
* _Fillets_ between intersecting surfaces or edges result in a smooth arc, reduced stress concentrations, prevent structural fatigue and provide strength to the design. In my design, fillets helped reinforce the hangers so they do not snap when a bunch of keys are hanged onto them.
* Designing a nail-slot appeared straightforward at first but soon I realised that it needs atleast two components, the wide base and a narrower front to allow nail-butt to lodge in and then allow vertical movement so that the key-holder stays securely may not securely hang on a nail.

---

### Modelling in QIDI studio
* Print orientation of the 3D model greatly impacts its strength and adhesion to the build plate. 
* Despite setting constraints in Onshape, we can scale-up or scale-down the size of the 3D model within the slicer.
* We can observe how and which components of the project will printed in chronological as well as reverse-chronological order to understand the fabrication process.
* 3D prints are anisotropic, which means they are much weaker along the Z-axis (between layers) than along the X and Y axes.
* Since the flattest and widest part was rhe backside, I enabled tree-type supports for the pegs to ensure stability while printing. 
  
---

### Exporting Models across Platforms 
* The CAD model can be exported from Onshape in the .STEP file format which can be imported in the slicer software.
* The CAD model can be exported from the slicer software in 3MF file format.

---

<br>

[← Back to Table of Contents](../README.md)
