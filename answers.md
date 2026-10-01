# CMPS 2200 Recitation 05
## Answers

**Name:** Nahema Dumonteil


Place all written answers from `recitation-05.md` here for easier grading.


- **3) (2 pts)** What is the work and span of `get_positions`? (assume our more efficient version of `scan` from class)

The more efficient version of scan from class has work O(n) and Span O(logn). What get_position adds to this, is simply slicing the list that scan gives us which has work O(n). Adding these gives us O(2n) and dropping the constant gives us O(n).

For Span, slicing the list can be O(1) if we assume it can be parallelized so with that span it would stay at (logn). If we keep the slicing sequential then it would be O(n) plus O(logn) and O(n) dominates so it would give us O(n). 



- **5) (2 pts)** What is the work and span of `construct_output`?
The work would be O(n) because it is a for loop looping through the list with n terms, for both the creation of the blank result list and the actual result list. 

The Span would also be O(n) because of the nature of our for loop, it needs the previous value to update to  the new value and because of this it has to run sequentially. 

- **6) (2 pts)** What is the work and span of `supersort`?
 Since it uses count_values, get_positions, and construct_output, the work would of those would be O(n +k),  O(n) and  O(n) respectively. (count_values has n + k because it has a list of k+1 elements in it and also loops through the list of n elements). Adding these gives O(3n +k ) and if we drop the constant we get O(n+k)
 
 We would get the same thing for Span, since the span for count_values is already O(n +k) it dominates. (Span for count_values is O(n+k) because it has to run sequentially).


- **8) (2 pts)** What is work and span of `count_values_mr`?
We need to look at all the functions within count_values_mr:

run_map_reduce:
it includes flatten which calls iterate, so loops through n lists and does concatination 
Work: O(n^2)
Span: O(n^2) too because it has to do it sequentially because of iterate.
next there is groups = collect(pairs) which calls sotred which has work O(nlogn) and Span(nlogn) since it runs sequentially in python.
So collect has 
Work: O(nlogn)
Span: O(nlogn)
next there is return [reduce_f(g) for g in groups] 
Work: O(n+k) because there are at most k different groups, with at most n elements across them.
Span: O(n+k) because it runs sequentially. 

[int2count.get(i,0) for i in range(k+1)]:
this has work O(k) because it runs through k+1, and Span(k) because it runs sequentially

Adding all up:
dominant terms in work: O(n^2 + k)
dominaint termts in span: O(n^2 +k)

We keep n and k because these are independent variables.




