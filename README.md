# TSP-Genetic-Algorithm
Travelling Salesman Problem optimization using Genetic Algorithm
This is my first project in Python. Motivation for learning Python is primarily to code AI and ML algorithms. As I have done this project to test myself on Python basics, I have on-purpose avoided use of advanced python packages such as numpy or pandas. The program imports only 2 packages - random (to shuffle and generate random numbers) and xlrd (to read excel file).

Travelling Salesman Problem (TSP)
I chose TSP as a good candidate to solve, as its a simple problem to understand and yet, solving via brute-force, it grows in complexity by n! (n factorial).

https://en.wikipedia.org/wiki/Big_O_notation

https://en.wikipedia.org/wiki/Travelling_salesman_problem

TSP asks the following question: "Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city and returns to the origin city?

Genetic Algorithm (GA)
https://en.wikipedia.org/wiki/Genetic_algorithm Genetic Algorithm is a heuristic algorithm inspired by process of natural selection based on the concept of Darwin's theory of evolution. GA is one of the meta-heuristics that has been frequently utilized to find near-optimum solutions of many combinational problems. In GA, a randomly generated 'population' of possible solutions is iteratively 'mated' to produce successive generations of 'children' population, which converge toward better and better solutions.

https://iccl.inf.tu-dresden.de/w/images/b/b7/GA_for_TSP.pdf

The above is the primary paper I have referenced to develop my GA algorithm code. As the paper notes, TSP is not a straight forward candidate to apply GA, as encoding of a TSP solution as a bit string is not convenient. TSP, as opposed to most problems tackled by GA, is a pure ordering problem. Hence, the original GA algorithm must be modified to handle combinatorial optimization problems like TSP. The paper thoroughly discusses various extensions of GA for 'encoding', 'mating' and 'mutating' solution population. It also gives computational results comparing the superiority of the various extensions.

I have selected the "Order Crossover (OX)" as mating technique along with simple 'Swap' technique for mutation. Short explanation of the 2 techniques is below

Order Crossover (OX): This allows two cut points to be randomly chosen on the parent chromosomes. In order to create an offspring, the string between the two cut points in the first parent is first copied to the offspring. Then, the remaining positions are filled by considering the sequence of cities in the second parent, starting after the second cut point (when the end of the chromosome is reached, the sequence continues at position 1). The OX tries to prserve the order of cities in parents rathen than absolute position. Example

parent 1: 1 2 | 5 6 4 | 3 8 7

parent 2: 1 4 | 2 3 6 | 5 7 8

offspring

(step 1): - - | 5 6 4 | - - -

(step 2): 2 3 | 5 6 4 | 7 8 1

In step 2, city 5 is first considered to occupy position 6, but it is discarded because it is already included in the offspring. City 7 is the next city to be considered, and it is inserted at position 6. Then, city 8 is inserted at position 7, city 1 is inserted at position 8, city 4 is discarded, city 2 is inserted at position 1, city 3 is inserted at position 2, and city 6 is discarded.

Swap: Two cities are randomly selected and swapped (i.e. their positions are exchanged). This mutation operator is the closest in philosophy to the original mutation operator, because it only slightly modifies the original tour.
