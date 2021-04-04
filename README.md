# Aha!

After reading through the source code and getting an idea of how Aha! works, I wrote several test programs to see how they'd be optimized.

### ispositive 
ispositive checks if a number is positive, zero, or negative, returning 1, 0, and -1 respectively. The different approaches Aha! took to optimizing this program were an interesting mix of logical and bit tricks. For example, one 4-instruction solution used negation, signed and unsigned right shifts along with an or, while another used subtraction and xor.

### min
I also wrote a simple program that returns the larger of two numbers. Aha! with its default instruction set couldn't find any solutions with 4 or less instructions, and after running for over 30 minutes on my machine didn't find any 5-instruction solutions. The original Massalin paper had an example of a similar program in 4 instructions, taking advantage of carry, something that Aha! lacks. 

### multiplication/division by constant
I wrote several programs that multiplied and divided by constants, as well as messed around with the instruction set used for optimizing. Without the multiplication and division instructions, both operations quickly grow too long to fit into Aha!'s default 5-instruction limit. Increasing the limit leads to confirmation of Massalin's claim in the paper: multiplication/division by thousands only takes a few more instructions than multiplication/division by tens. 

