# Heredity
Heredity is a program that calculates probabilities related to Mendelian inheritance. Given a family tree of individuals, where the presence or absence of a certain genetic trait is known for some individuals, the program computes the probability that each individual in the tree has zero, one, or two copies of the gene responsible for the trait.

## Usage
The program expects a CSV file containing the genealogy of individuals in the family tree, along with information about their traits. The file must have the following format:

| name | mother | father | trait |
| --- | --- | --- | --- |
| Bob | Carol | Dave |  |
| Carol | || 0 |
| Dave |  |  | 1 |


To run the program, navigate to the directory containing the heredity.py file and the data file, and run the following command:

`python heredity.py data.csv`

where data.csv is the name of the data file.

## Dependencies
The program requires these modules below to run:
- csv
- itertools
- sys

## Implementation
The program works by computing joint probabilities of events using the chain rule of probability. The probability of an event is computed by considering the probabilities of its parent events. The events in this case are the number of copies of the gene and the presence or absence of the trait for each individual in the family tree.

The program first loads the data from the CSV file into a dictionary. It then loops over all possible sets of individuals who may have the trait, and for each such set, loops over all possible sets of individuals who may have one or two copies of the gene. For each combination of these sets, the program computes the joint probability of the events.

The joint probability of the events is computed recursively using the probabilities of the parent events, until the probability of the event for an individual with no parents is reached. The probabilities of the parent events are computed using the probabilities provided in the PROBS dictionary.

Finally, the program normalizes the probabilities and prints the results for each individual in the family tree.

## Credits
This program's relevant functions were written by me, and is based on a problem set for the course CS50AI from Harvard University. The course material and problem set were created by the staff at Harvard University, and are available at https://cs50.harvard.edu/ai/.
