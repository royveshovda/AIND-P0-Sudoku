# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
* Q: How do we use constraint propagation to solve the naked twins problem?
* A: Naked twins strategy looks for boxes with similar pairs inside the same unit. If two such pairs (for example 23) is found inside the same unit, we know that the values (23) has to be in thos two boxes.
We therefore remove the values from all the other boxes in that unit.
It is important to note that this has to be process on one unit at the time.

The function (naked_twins) first looks for all boxes with only two values inside.
The function then iterates over these boxes, finds all units the current box is a member of.
Now having a box and a unit, the function looks for identical boxes. I a match is found, the boxes are called naked twins, and the values of this naked twins can be removed from all other boxes in the current unit.

One important note to make is that it is tempting to detect pairs in all boxes, and flag them as candidates, and process through them one at the time.
My first attempt did just this. It is important to chech if the box previously flagged as pair, can have been pruned down to a single value in an earlier naked twin detection.
A last check if the box is still a pair is important.

The naked_twins function is a constraining function which is called in from the solved function at the same time as the other constraining functions (eliminate and only_choice).
I included the function inside the solution from the class, only having to implement the function, and include it inside the already working "solve" function.

# Question 2 (Diagonal Sudoku)
* Q: How do we use constraint propagation to solve the diagonal sudoku problem?
* A: In the code from the class the strategy is to apply different constraint propagations one unit at a time.
To solve the diagonal sudoku problem, we need to add two more units. One going from the upper left down to the lower right, and one from upper right down to lower left.
In the code these are called "diagonal_units", and are hard coded (as there are only two of them).
These diagonal units are then included with all the other units, and used in all the constrating functions (including the one from question 1) to solve the sudoku problem.

# General
I based both additions on the code used during the lecture.
This was a great foundation which only required to add constraints as described above.
Being able to implement these new strategies this easy, is an indication that the foundation from class is a very good model for the sudoku problem.
