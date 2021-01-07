Before we begin it is assumed you have some prior knowledge about the properties of **Integers**, **Modular Arithmetic**,
**Complex Numbers**, **Induction**, **Equivalence Relations** and **Function**. If any of these topics are hazy, I would recommend
you study up on them before proceeding. Gallian provides a good introduction to these topic in his book "Contemporary Abstract Algebra".
(Please see the suggested reading list (bottom of page) for more information).

***

# Getting Started

This is the first lesson of Group Theory. I will go over some historical motivation for groups, and introduce some groups that will appear in subsequent lessons.

# Symmetries
Groups were first studied as a closed set of symmetries of a geometric object.
We will start by looking at the symmetries of a square, to develop the intuition
behind Groups.
Consider a transparent square (such as glass), with each corner marked by a different colour, say,
red, green, blue, and yellow. We wish to find the number of unique invariant transformations (fancy talk for symmetries) of this square.
That is, we are interested in the net effect of a motion, rather than the motion itself.
Thus, for example, a rotation of 90 degrees and 450 degrees result in the same motion, since they have
the same net effect on every point. The same goes for a rotation of 180 degrees and 540 degrees or
0 degrees and 360 degrees.
With that being said, we are now in a position to describe, in it's simplest form, all possible
symmetries of this square. See table below (Rotations are counter-clockwise).

 | Symmetry |                                    Image                                                | Description         |
 | :---     |                                    :----:                                               |         ---:        |
 | I        | ![alt text](https://github.com/davybob/GroupTheory/images/I.png "Original square")      | Original square     |
 | R        | ![alt text](https://github.com/davybob/GroupTheory/images/R.png "90° rotation")         | 90° rotation        |
 | R'       | ![alt text](https://github.com/davybob/GroupTheory/images/R2.png "180° rotation")       | 180° rotation       |
 | R''      | ![alt text](https://github.com/davybob/GroupTheory/images/R3.png "270° rotation")       | 270° rotation       |
 | H        | ![alt text](https://github.com/davybob/GroupTheory/images/H.png "Horizontal flip")      | Horizontal flip     |
 | V        | ![alt text](https://github.com/davybob/GroupTheory/images/V.png "Vertical flip")        | Vertical flip       |
 | D        | ![alt text](https://github.com/davybob/GroupTheory/images/D.png "Main diagonal flip")   | Main diagonal flip  |
 | D'       | ![alt text](https://github.com/davybob/GroupTheory/images/D2.png "Other diagonal flip") | Other diagonal flip |   


We can see that a square has exactly eight distinct symmetries.
Let us now do a little bit of investigation about these symmetries. Suppose a square
is rotated by 180° then flipped horizontally. The resulting 'multiplication' of transformation would be
equivalent to a vertical flip as shown in Figure 1.

![alt text](https://github.com/davybob/GroupTheory/images/D2.png "Other diagonal flip")

This example shows that applying two transformation is equivalent to applying some one
transformation.
Note that a horizontal flip then a 180° rotation would not be equivalent to a main diagonal flip (Exercise). So
the symmetries of a square are not commutative (i.e. HR<sub>180</sub> ≠ R<sub>180</sub>H = D).


We can interpret the eight transformations as functions from the square onto itself, and so we can combine them
using function composition. The eight transformations form a mathematical system called the *dihedral group of order 8* (D<sub>8</sub>).
A dihedral group is a group of symmetries of a regular polygon. The transformations of a square is called a *dihedral group of order 8* because
it contains 8 symmetries (order of a group is number of element in that group).
The transformations of a triangle would be called a *dihedral group of order 6* (Exercise).

In general, a symmetry of a geometrical figure is, by definition, a one-to-one and onto mapping of its points
which preserves distances. In the example of the square, a 90° rotation moves vertex 1->2, vertex 2->3, vertex 3->4 and
vertex 4->1. One can check that any symmetry of the square must carry vertex 1 into one of the other four vertices (itself included)
and that for each such choice, there are exactly 2 symmetries. Then in all, there are 8 symmetries; So we have them all accounted for.

We can directly calculate all the possible pairs of transformations by constructing an *operation table* or *Cayley table*. The
Cayley table for the square is constructed below.

|                     | **I**           | **R<sub>90</sub>** | **R<sub>180</sub>** | **R<sub>270</sub>** | **H**           | **V**           | **D**            | **D'**          |
| :---                | :----:          | :----:             | :----:              | :----:              | :----:          | :----:          | :----:           | :----:          |
| **I**               | I               | R<sub>90</sub>     | R<sub>180</sub>     | R<sub>270</sub>     | H               | V               | D                | D'              |
| **R<sub>90</sub>**  | R<sub>90</sub>  | R<sub>180</sub>    | R<sub>270</sub>     | I                   | D'              | D               | H                | V               |
| **R<sub>180</sub>** | R<sub>180</sub> | R2R<sub>270</sub>  | I                   | R<sub>90</sub>      | V               | H               | D'               | D               |
| **R<sub>270</sub>** | R<sub>270</sub> | I                  | R<sub>90</sub>      | R<sub>180</sub>     | D               | D'              | V                | H               |
| **H**               | H               | D                  | V                   | D'                  | I               | R<sub>180</sub> | R<sub>90</sub>   | R<sub>270</sub> |
| **V**               | V               | D'                 | H                   | D                   | R<sub>180</sub> | I               | R<sub>270</sub>  | R<sub>90</sub>  |
| **D**               | D               | V                  | D'                  | H                   | R<sub>270</sub> | R<sub>90</sub>  | I                | R<sub>180</sub> |
| **D'**              | D'              | H                  | D                   | V                   | R<sub>90</sub>  | R<sub>270</sub> | R<sub>180</sub>  | I               |

The table above shows some very interesting properties of symmetries. The table is completely
filled in with the eight transformations. This should be obvious, as we have already pointed out
in the previous example that any sequence of transformations turns out to be the same as one of the
eight. This property is known as *closure* and is one of the requirements for a mathematical system
to be a group.
Next, notice that the top row and left column (not in bold) are equal to the eight
symmetries in their order. The row/column is the composition Ia = a where a is some transformation.
An element with this property is known as an *Identity element* (hence the reason it's labelled I).

This is another requirement for a system to be a group, namely it must contain an identity element.

Moreover, we can see that for every element in the table, there is one element that combines with it
to create the identity element. I.E. for all elements A in D<sub>8</sub> there must exist one element
called an *inverse* element a<sup>-1</sup> that, when composed with a creates I.
For example HH = I, we say that H is it's own *inverse* (H=H<sup>-1</sup>).

So far, we have shown, through D4 as an example, three of the four conditions that define a group: closure, existence of an identity,
and existence of inverses. The remaining condition required for a system to be a group is associativity; that is (ab)c = a(bc) where
a, b, and c are elements in the system.
We could show this for D<sub>8</sub> but that would require calculating all 8<sup>3</sup> = 512 possible combinations of a, b, and c in D<sub>8</sub>.
There is a simpler way, simply observe that the eight motions are functions and the operation is function composition. Then,
since function composition is associative, we do not have to check the equations. Far easier that computing all 512 combinations!

### TO DO
* Groups of transformations
* end with advice some study into dihedral groups (book)
* Problems/Questions
