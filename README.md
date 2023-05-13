# wordle-bot
A program written in **Python** that solves the Wordle Quiz using **Information Theory**.

**Wordle:**
Wordle is a web-based word game created and developed by Welsh software engineer Josh Wardle. Players have six attempts to guess a five-letter word, with feedback given for each guess in the form of colored tiles indicating when letters match or occupy the correct position.

In this project we take a Command Line based adaptation of the Wordle game and try to solve it using programming logic and Advanced Mathematics.

The working of the Wordle Game is handled by the _utils.py_ file. It takes as input the guess that is handled by the _main.ipynb_ file and returns the feedback on a 3-point scale:
0 - Letter doesn't exist either in the guess or the answer
1 - Letter exists both in the guess and the answer and on the same position as in the guess
2 - Letter exists both in the guess and the answer but not on the same position as in the guess
The possible answer is randomly selected from a list of [5757 words](https://github.com/charlesreid1/five-letter-words/blob/master/sgb-words.txt).
Logic of selecting the next guess is based on an advanced Mathematics theory - **Information Theory**.

## Information Theory
Information theory is the mathematical study of the quantification, storage, and communication of information. How Information theory handles quantification of information is very similar of how computer processes information - in the terms of **bits**!

### What is Information?
Information is measured in bits. When measuring information, we are measuring the number of bits, or the number of “yes or no” questions we would have had to ask to reach the same conclusion.
This information can be quantified by the following formula:

I = -log<sub>2</sub>(p)

Now if each outcome has a different probability, then we can calculate the expected **Information (Entropy)** by taking the sum of the product of probability of that outcome and the information gained when that outcome were true.

So to make a guess from the possible list of answers, we calculate the entropy of each word (for all the possible feedbacks that a guess can have) and then guess the word that has the highest entropy.
##
Here is the algorithm I used:
1. Compute the entropy for all possible words
2. Choose the word that has the highest entropy
3. Submit guess to Wordle and fetch the output
4. Update list of remaining possible words
5. Repeat steps 1–4 until the guess is equal to the answer

The average number of guesses the program requires to correctly guess the word comes out to be near 4.32
