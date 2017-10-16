# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: Naked twins is a new constraint that we've added to the sudoku solver.
It constrains the possible values for the boxes in a given unit when the unit contains a pair of naked twins,
which is a set of two boxes in the unit with the same two possible values. The constraint we're enforcing is
that when a unit contains a pair of naked twins, the possible values of the twins may not appear in any other
boxes in that unit. This constraint can be applied repeatedly (propagated) on the same sudoku puzzle because
applying the constraint in one unit can enable you to apply the constraint in another unit. For example, if B5 and B7
are "naked twins" and through enforcement of the constraint a possible value is removed from B6 reducing its possible
values from 3 to 2, now B6 could be its own naked twin with another box, say A6, thus unlocking a new unit where you can
apply the naked twins constraint.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: The diagonal sudoku problem differs from traditional sudoku only in that there are two new units
to consider: the diagonals. This affects all three constraint techniques used by the solver, which are
Elimination, Only Choice, and Naked Twins. I would argue that from the perspective of the sudoku
solver, the new diagonal units actually makes the problem easier since the possible values of the
diagonal boxes are even more constrained than before. For example, take the middle box, E5, and assume its value is known.
In traditional sudoku you could use the elimination technique to remove the value of E5 from 20 different boxes
(all of its peers), but with the addition of diagonals it can be removed from 32 different boxes. In this way, the
method of constraint propagation has become more efficient.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project.
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - Fill in the required functions in this file to complete the project.
* `test_solution.py` - You can test your solution by running `python -m unittest`.
* `PySudoku.py` - This is code for visualizing your solution.
* `visualize.py` - This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.
