# Aha!

First I read through the source code, playd around with the instruction set, and modified the instruction implementations to get an idea of how Aha! works. Then, I wrote several test programs to see how they'd be optimized, under several instruction sets.

### ispositive

ispositive checks if a number is positive, zero, or negative, returning 1, 0, and -1 respectively. The different approaches Aha! took to optimizing this program were an interesting mix of logical and bit tricks. For example, one 4-instruction solution used negation, signed and unsigned right shifts along with an or, while another used subtraction and xor.

### min/max

I also wrote a simple program that returns the larger of two numbers. Aha! with its default instruction set couldn't find any solutions with 4 or less instructions, and after running for over 30 minutes on my machine didn't find any 5-instruction solutions. The original Massalin paper had an example of a similar program in 4 instructions, taking advantage of carry, something that Aha! lacks. Attempting to optimize a similar program for the maximum of two numbers met a similar fate.

### multiplication/division by constant

I wrote several programs that multiplied by constants, as well as messed around with the instruction set used for optimizing. Without the multiplication instruction, programs quickly grow too long to fit into Aha!'s default 5-instruction limit. Increasing the limit leads to confirmation of Massalin's claim in the paper: multiplications by thousands only takes a few more instructions than multiplication by tens. I also confirmed that division is difficult to optimize, as without the division instructions, programs became too long to optimize significantly quicker than multiplication programs.

### realavg

realavg computes the integer average of two numbers. This optimization is fairly straightfoward without division, but it's interesting that one of the two 4-instruction solutions uses subtraction and signs while the other does a more straighfoward addition before leftshifting to divide.

### 3args

3args tries to compute the integer average of three numbers. As expected, three arguments significantly lengthens Aha!'s runtime: I let this run for about 15 minutes with a 5-instruction limit before I cut it off. I would expect this solution to be similar to realavg's, just with significantly more instructions to account for the extra argument. Interestingly, even with division in the instruction set, Aha! cannot find a 3 or 4-instruction solution, and after 15 minutes cannot find a 5-instruction solution either. 
