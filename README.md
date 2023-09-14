# Visualization of procedurally generated cellular structures

A repository containing code developed as part of the Bachelor thesis at the University of Ljubljana, Faculty of Computer and Information Science by [Kovač Marina](https://github.com/MarinaUVP).

## Abstract
In this work, we were dealing with how to generate new models of cellular structures from real volumetric images. From the database of volumetric images with labeled cellular structures, we extracted two kinds of cellular structures (endolysosomes and fusiform vesicles), and prepared new volumetric images with only one object in each to later find points on their surfaces. With those points, we created a shape model used in the generation of new cellular structures. We defined a process to generate new models of cellular structures based on the three input parameters. Output is the same if none of those three parameters change. Thus, the user has the ability to generate countless different models. After we created a few new models with the proposed generator, we evaluated those new models with two approaches. First, calculating the root mean square error (RMSE) and then calculating and comparing norms of average vectors and vectors for standard deviations. A quick evaluation with an eye may reveal some of the generated models are nicer than existing ones. Nevertheless, new models could be even better if we would also modify the sizes of the learning and testing objects.


The thesis is accessible at:
[https://repozitorij.uni-lj.si/Dokument.php?id=150090]

Bibtex:
```
@thesis{Kovac2021,
    title = {Visualization of procedurally generated cellular structures},
    author = {Kovač, Marina},
    year = {2021},
    school = {University of Ljubljana, Faculty of Computer and Information Science},
    type = {Master thesis},
    address = {Ljubljana, Slovenia},
    note = {Mentor: Ciril Bohak, Co-mentor: David Murphy, Language: Slovenian, Slovenian title: Vizualizacija proceduralno generiranih celičnih struktur},
    url = {https://repozitorij.uni-lj.si/Dokument.php?id=150090}
}
```

...

# Statistic-Models-For-Cellular-Structures

A workflow to generated new objects of cellular structures.

Statistical shape model (SSM) is build based on volumetric data and automated calculating of intersection points (landmarks). Obtained SSM is the base for generating new models of cellular structures. Output is a 3D mesh (.obj file).

This workflow is completed for two types of cellular structures: endolysosomes and fusiform vesicles (FVs).

Initial volumetric data are obtained from: https://github.com/MancaZerovnikMekuc/UroCell

## Code files

Preprocessing:
- **single_objects.py**: Extracting objects with the same value from volumetric data and writing each extracted object in its own volumetric image.  (This was used for endolysosomes.)
- **single_objects_instance.py**: Extracting objects with different values from volumetric data and writing each extracted object in its own volumetric image.  (This was used for fusiform vesicles.)
- **framing.py**: Removing extra space from volumetic images.

Reference objects:

- **icosahedron.py**: The subdivided icosahedron is an object with reference points for endolysosomes.
- **hexagon_object.py**: An object made of two hexagons is an object with reference points for fusiform vesicles.

Calculting intersection points:
- **intersections.py**: Functions to calculate intersection points for one object.
- **all_intersections.py**: Calculating intersection points for all objects in one folder.
- **cog_position_fv**: Distinguish between FVs with a center of gravity (COG) in and out of the object.
- **rotation_matrix.py**: Calculating rotation matrix to rotate the object with reference points for FVs.

Generating new objects:
- **new_objects_generator.py**: Generating new objects (.obj files) based on calculated intersection points.

Evaluation:
- **model_evaluation.py**: Evaluating newly generated models with objects from a testing group.
