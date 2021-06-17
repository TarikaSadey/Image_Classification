
## Image Classification

* For Training:

The courier-train.png image is used the training data for calculating the probability distribution for the pixels in the image.
The tarin-text.txt file (sample of the corpus as a approximate language model) is used for the calculation of the prior probabilities and transition probabilities. These are used in the Naive Bayes Viterbi implementation.
1) We trained the data to get the dictionary of characters(P(w1|S), transition of characters(P(N|N)).
2) For emission probabilities we used match and miss counts and calculated the character probabilities .
3) Out of the 14 * 25 blocks we considered '*' to have higher probability folowed by ' ' and lesser probability for miss data.
4) We assigned weights to each type of character and returned the highest probability for a probable character.
5) For transition prbabilities, we noticed that they were dominating, so we added a large number and divided with a small number to normalize the values. This is done to avoid the domination of transition prob in our answers. (The idea was taken from a paper mentioned in refernces.)

* For Simplified algorithm:

hit/miss ratio: Weighted sum is taken by comparing two letters pixel by pixel. If there is a match, higher weights are given and vice versa. At end average of weighted sum is taken and the corresponding letter is predicted by most matching pixels.

1) We just check the match/miss ratio for a particular char and returned the maximum one.
2) we used match and miss counts and calculated the character probabilities.
3) Out of the 14 * 25 blocks we considered '*' to have higher probability folowed by ' ' and lesser probability for miss data..
 
* For Viterbi algorithm in case of HMM:

1) The transition probabilities are calculated first which specify the chances to move from one state to the other state in the model. These are calculated from the training data (from the train-text.txt file provided as an argument) as P [S(i+1)| S(i)] where S = a valid letter in the train data.
2) A matrix of rows equal to 72(= number of train letters) and column equal to no of letters in test data is created.
3) The first column of the matrix is filled with initial probabilities calculated by matching pixel to pixel.
4) The next emission probabilities are calculated using transition probabilities and previous corresponding value.
5) We also added weights to our transition probabilities and giving maximum weight to the emission probability to get better results.

The Dynamic Programming Approach. At each state of the HMM, the probabilities are calculated by multiplying three terms,
A) Transition probability from the previous letter to current letter P(Si/Si-1): How often a letter is followed by other leters in the training file.
B) Emission probability of the current letter P(Wi/Si): Learned through the Naive Bayes.
C) Probability calculated so far P(i-1) 

6) Our each cell is of this form [probability, PrevMaxValue]
7) once we fill our veterbi matrix, we perform back tracking and find the corresponding letter where we get maximum value.
8) return the string sequence.

* References:

1. Canvas Slides
2. http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.141.7177&rep=rep1&type=pdf


 

