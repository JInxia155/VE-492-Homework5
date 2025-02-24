Download Link : https://programming.engineering/product/ve-492-homework5/

# VE-492-Homework5
VE 492 Homework5
Question 1: Campus Layout

You are asked to determine the layout of a new, small college. The campus will have four structures: an administration structure (A), a bus stop (B), a classroom (C), and a dormitory (D). Each structure (including the bus stop) must be placed somewhere on the grid shown below.

The layout must satisfy the following constraints:

i. The bus stop (B) must be adjacent to the road.

    The administration structure (A) and the classroom (C) must both be adjacent to the bus stop (B).

    The classroom (C) must be adjacent to the dormitory (D).

    The administration structure (A) must not be adjacent to the dormitory (D).

    The administration structure (A) must not be on a hill.

    The dormitory (D) must be on a hill or adjacent to the road.

    All structures must be in different grid squares.

Here, adjacent means that the structures must share a grid edge, not just a corner.

We recommend you work out the solutions to the following questions on a sheet of scratch paper, and then enter your results below.

Part 1: Unary Constraints

    Which of the constraints above are unary constraints?

        i

        ii

        iii

        iv

        v

        vi

        vii

        None of the above

Sample Answer:

ABCD

(b) Write the domains of all variables after unary constraints have been applied.

Sample Answer:

A(1,1)(1,2)B(1,1)C(1,1)(1,2)D(1,1)(1,2)

Part 2: Arc Consistency

Let’s start from the table above (the answer to Part 1) and enforce arc consistency.

Initially, the queue contains all arcs (in alphabetical order).

Let’s examine what happens when enforcing A→B. After enforcing unary constraints, the domains of A and B are:

    Which of the following contains the correct domains after enforcing A→B? Pay attention to which variable’s domain changes and which side of the arc it’s on.

        i

        ii

        iii

        iv

    Starting from the answer to Part 1 (in which unary constraints are enforced), write the domains of all variables after A→B is enforced.

You should verify that enforcing consistency for A→C, A→D, B→A, B→C, B→D, and C→A do not change the domains of any variables. After enforcing these arcs, the next is C→B.

Continuing from the previous parts, write the domains of all variables after C→B is enforced.

Sample Answer:

A(1,1)(1,2)B(1,1)C(1,1)(1,2)D(1,1)(1,2)

    What arcs got added to the queue while enforcing C→B? Remember that the queue contained C→D, D→A, D→B, and D→C prior to enforcing C→B.

        A→B

        A→C

        A→D

        B→A

        B→C

        B→D

        C→A

        C→B

        C→D

        D→A

        D→B

        D→C

        None

    Continuing from the previous parts, select the domains of all variables after enforcing arc consistency until the queue is empty. Remember that the queue currently contains C→D, D→A, D→B, D→C, and any arcs that were added while enforcing C→B.

Sample Answer:

A(1,1)(1,2)B(1,1)C(1,1)(1,2)D(1,1)(1,2)

Part 3: Search with Arc Consistency

    If arc consistency had resulted in all domains having a single value left, we would have already found a solution. Similarly, if it had found that any domain had no values left, we would have already found that no solution exists. Unfortunately, this is not the case in our example (as you should have found in the previous part). To solve the problem, we need to start searching. Use the MRV (minimum remaining values) heuristic to choose which variable gets assigned next (breaking any ties alphabetically).

Which variable gets assigned next?

    A

    B

    C

D. D

    The variable you selected should have two values left in its domain. We will use the least-constraining value (LCV) heuristic to decide which value to assign before continuing with the search. To choose which value is the least-constraining value, enforce arc consistency for each

value (on a scratch piece of paper). For each value, count the total number of values remaining over all variables.

Which value has the largest number of values remaining (and therefore is the least constraining value)?

        (1,1)

        (1,2)

        (1,3)

        (2,1)

        (2,2)

        (2,3)

    After assigning a variable, backtracking search with arc consistency enforces arc consistency before proceeding to the next variable.

Write the domains of all variables after assignment of the least-constraining value to the variable you selected and enforcing arc consistency. Note that you already did this computation to determine which value was the LCV.

Sample Answer:

A(1,1)(1,2)B(1,1)C(1,1)(1,2)D(1,1)(1,2)

(k) Is the answer to the previous part a solution to the CSP? Write Yes or No.

Question 2: CSP Properties

    Write all of the following statements about CSPs that are true.

        Even when using arc consistency, backtracking might be needed to solve a CSP.

        Even when using forward checking, backtracking might be needed to solve a CSP.

        None of the above

    Select all of the following statements about CSPs that are true.

        When using backtracking search with the same rules to select unassigned variables and to order value assignments (in our case, usually Minimum Remaining Values and Least-Constraining Value, with alphabetical tiebreaking), arc consistency will always give the same solution as forward checking, if the CSP has a solution.

        For a CSP with binary constraints that has no solution, some initial values may still pass arc consistency before any variable is assigned.

        None of the above

Question 3: 4-Queens

The min-conflicts algorithm attempts to solve CSPs iteratively. It starts by assigning some value to each of the variables, ignoring the constraints when doing so. Then, while at least one constraint is violated, it repeats the following:

    randomly choose a variable that is currently violating a constraint,

    assign to it the value in its domain such that after the assignment the total number of constraints violated is minimized (among all possible selections of values in its domain).

In this question, you are asked to execute the min-conflicts algorithm on a simple problem: the 4-queens problem in the figure shown below. Each queen is dedicated to

    its own column (i.e. we have variables
    		

    ,
    	

    ,
    	

    ,
    		

    and the domain for each one

    th

    th

    		

    configuration shown below, we have
    	

    of them is {A, B, C, D}). In the
    								

    row, diagonal,
    	

    . Two queens are in conflict if they share the same
    	

    th

or column (though in this setting, they can never share the same column).

You will execute min-conflicts for this problem three times, starting with the state shown in the figure above. When selecting a variable to reassign, min-conflicts chooses a conflicted variable at random. For this problem, assume that your random number generator always chooses the leftmost conflicted queen. When moving a queen, move it to the square in its column that leads to the fewest conflicts with other queens. If there are ties, choose the topmost square among them.

We recommend you work out the solutions to the following questions on a sheet of scratch paper, and then enter your results below.

Part 1

Sample Answer:

(2,A)

Part 2

Continuing off of Part 1, which queen will be moved, and where will it be moved to? Write your answer in a form of tuple (Queen,Position).

Sample Answer:

(2,A)

Part 3

Continuing off of Part 2, which queen will be moved, and where will it be moved to? Write your answer in a form of tuple (Queen,Position).

Sample Answer:

(2,A)

Question 4: Tree-Structured CSPs

There exist efficient solvers for tree-structured CSPs. We can use such solvers in the inner loop of a CSP solver for near-tree-structured CSPs as follows: First find a cutset (i.e. a set of variables such that if removed, the remaining constraint graph forms a tree), then loop over all instantiations of the cutset variables, and for each instantiation call the tree-structured CSP solver to verify if for that instantiation a solution exists; the algorithm terminates when a solution is found or when it has looped over all possible instantiations and no solution was found (and hence the CSP has no solution).

Consider the graph above. Write down the variables that are in the smallest cutset of this graph.

Note: in general, this is a computationally difficult problem. We have not seen an algorithm to compute the minimum cutset in lecture, but for a small graph you should be able to do it by hand (with some effort).

Sample Answer:

AB

Question 5: Solving Tree-Structured CSPs

Consider the following tree-structured CSP that encodes a coloring problem in which neighboring nodes cannot have the same color. The domains of each node are shown.

The algorithm for solving tree-structured CSPs starts by picking a root variable. We

    can pick any variable for this. For this exercise, we will pick
    		

    . There are several

    linearizations consistent with as the root; we will use the one
    	

    shown below.
    	

    	

Step 1: Remove Backward

In this s tep we start with the right-most node ( ), enforce arc- consistency fori ts parent ( ), then do the same for the second-to-right-most node ( ) and its parent ( ), and so on. Execute this process, and then write the remaining values for all the variables.

Sample Answer:

A(red)B(red,green)C(red,green,blue)D(red)E(red,green)

Step 2: Assign Forward

Now that all domains have been pruned, we can find the solution in a single forward pass (i.e. no need for backtracking). This is done by starting at the left-most node ( ), picking any value remaining in its domain, then going to the next variable ( ), picking any value in its domain that is consistent with its parent, and continue left to right, always picking a value consistent with its parent’s assignment.

If at any given node there are multiple colors left that are consistent with its parent’s value, break ties by picking red over green, and then green over blue.

What is the solution found by running the algorithm?

Question 6: Arc Consistency

    Consider the problem of arranging the schedule for an event. There are three time

    to be
    			

    		

    		

    , , and
    	

    . The variables for the CSP

    slots: 1, 2, and 3. There are three presenters:

    will then be
    		

    , , and , each with domain
    	

    {1, 2, 3}. The following constraints need
    		

    	

    2.
    	

    		

    				
    	

    satisfied:
    					

    1.
    	

    		

    all need to take on different values
    	

    ,
    		

    , and
    		

    Enforce consistency for the arc A→C, and then write down which values remain for each variable.

Sample Answer:

A(1)B(1,2)C(1,2,3)

    Starting from the result of the previous step, enforce consistency for the arc B→A, and then write down which values remain for each variable.

Sample Answer:

A(1)B(1,2)C(1,2,3)

    Starting from the result of the previous step, enforce consistency for the arc C→A, and then write down which values remain for each variable.

Sample Answer:

A(1)B(1,2)C(1,2,3)

Question 7: Arc Consistency Properties

Assume you are given a CSP and you enforce arc consistency. Which of the following are true?

    If the CSP has no solution, it is guaranteed that enforcement of arc consistency resulted in at least one domain being empty.

    If the CSP has a solution, then after enforcing arc consistency, you can directly read off the solution from resulting domains.

    In general, to determine whether the CSP has a solution, enforcing arc consistency alone is not sufficient; backtracking may be required.

    None of the above.

Question 8: Backtracking Arc Consistency

We are given a CSP with only binary constraints. Assume we run backtracking search with arc consistency as follows. Initially, when presented with the CSP, one round of arc consistency is enforced. This first round of arc consistency will typically result in variables having pruned domains. Then we start a backtracking search using the pruned domains. In this backtracking search we use filtering through enforcing arc consistency after every assignment in the search. Which of the following are true about this algorithm?

Part 1

Which of the following are true about this algorithm?

    If after a run of arc consistency during the backtracking search we end up with the filtered domains of all of the not yet assigned variables being empty, this means the CSP has no solution.

    If after a run of arc consistency during the backtracking search we end up with the filtered domain of one of the not yet assigned variables being empty, this means the CSP has no solution.

    None of the above.

Part 2

Which of the following are true about this algorithm?

    If after a run of arc consistency during the backtracking search we end up with the filtered domains of all of the not yet assigned variables being empty, this means the search should backtrack because this particular branch in the search tree has no solution.

    If after a run of arc consistency during the backtracking search we end up with the filtered domain of one of the not yet assigned variables being empty, this means the search should backtrack because this particular branch in the search tree has no solution.

    None of the above.

Part 3

Which of the following are true about this algorithm?

    If after a run of arc consistency during the backtracking search we end up with the filtered domains of all of the not yet assigned variables each having exactly one value left, this means we have found a solution.

    If after a run of arc consistency during the backtracking search we end up with the filtered domains of all of the not yet assigned variables each having more than one value left, this means we have found a whole space of solutions and we can just pick any combination of values still left in the domains and that will be a

solution.

    If after a run of arc consistency during the backtracking search we end up with the filtered domains of all of the not yet assigned variables each having more than one value left, this means we can’t know yet whether there is a solution somewhere further down this branch of the tree, and search has to continue down this branch to determine this.

