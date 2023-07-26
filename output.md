
-  Goal : Compute the probability of a sentence or sequence of words.  $latex P(W) = P(w_1, w_2, w_3,..., w_n)$
-  Related Task:  Probability of an upcoming word - -> $latex P(w_4 | w_1, w_2, w_3)$.

-   A model that computes either of these is called a language model.

#### The Chain Rule in general
$latexP(x_1, x_2,...,\ x_n) = P(x_1)\cdot P(x_2 \ | \ x_1)\cdot P(x_3 \ | \ x_1, x_2) \cdot  ...  \cdot P(x_n \ | \ x_1,..., \ x_{n-1})$
$latexP(x_1, x_2,...,\ x_n) = \prod\limits_{i} P(w_i \ | \ w_1, w_2,..., \ w_{i-1})$

-  Example:
$latex
\begin{split}
P(about \ fifteen \ minutes \ from) = &P(about) \times P(fifteen \ | \ about)\\\\ & \times P(minutes \ | \ about \ fifteen) \\\\ & \times P(from \ | \ about \ fifteen \ minutes)
\end{split}
$

-  We can calculate these probabilities by,
$latexP(office \ | \ about \ fifteen \ minutes \ from) = \frac{Count(about \ fifteen \ minutes \ from \ office)}{Count(about \ fifteen \ minutes \ from )}$

Note:  Too many words lead to lesser chances of seeing such combination of words in the corpus.

-  Better Option is to make a simplifying assumption of using only the previous word or couple of previous words instead of the whole sentence.
-  Example:  
  $latex P(office \ | \ about \ fifteen \ minutes \ from) \approx P(office \ | \ from)$   OR $latex P(office \ | \ about \ fifteen \ minutes \ from) \approx P(office \ | \ minutes \ from)$ 

-  We can also use the Markov Assumption to only consider  $latex k$   previous words.
$latexP(x_1, x_2,...,\ x_n) = \prod\limits_{i} P(w_i \ | \ w_{i-k},..., \ w_{i-1})$

-  An N-Gram model uses only N - 1 words of prior context.
	- Unigram:  $latex P(office)$ 
	- Bigram:  $latex P(office \ | \ from)$
	- Trigram:  $latex P(office \ | \ minutes \ from)$
- So an N-Gram model is an  $latex N - 1$  order Markov Model.

-  In general, we cannot say that any N-gram model is sufficient  model for  a  language because language has long-distance dependencies: "The computer which I had just put into the machine room  on the fifth floor crashed". 
-  Here the word "crashed" is in context with the word "computer" which is not covered by trigram, 4-gram, 5-gram models as it is 12  words away from "crashed".
- I most of the applications, we can get away with N-gram models.


-  We can calculate these N-gram probabilities by :
  $latex
  \begin{split}
  P(w_i \ | \ w_{i-1}) &= \frac{count(w_{i-1}, \ w_i)}{count(w_{i-1})}\\\\
  &= \frac{c(w_{i-1}, \ w_i)}{c(w_{i-1})}
  \end{split}
  $
  
-  $latex count(w_{i-1}, w_i)$   or  $latex c(w_{i-1}, w_i)$ --> No of times  $latex w_i$  occurred in the corpus after $latex w_{i-1}$ .
-  $latex count(w_{i-1})$  or  $latex c(w_{i-1})$--> No of times  $latex w_{i-1}$  occurred in the corpus.

Example:
-  Bigrams frequency
![[Pasted image 20230523141607.png]]

-  Unigram frequency
![[Pasted image 20230523141717.png]]

-  Bigram Probabilities
![[Pasted image 20230523141802.png]]

Now if I have a sentence  "I want english food " then the probability of this sequence of words occuring in corpus  will be 
$latex
\begin{split}
P(<s> \ I \ want \ english \ food \ </s>) 
\ = & \  P(I \ | \ <s>) \times P(english \ | \ want) \times \\\\
& P(food \ | \ english) \times P(</s> \ | \ food)
\end{split}
$

### What knowledge does N-gram represent?

-  It can represent various patterns related to the domain of the corpus or the language grammar.
  
  For eg:
  ![[Pasted image 20230523142355.png]] 
  
  Here we can make an observation that Chinese food is 6 times more popular than the English food as per the corpus.  We can also see that  the probability of "to" occuring after "want" is pretty high which is logical because we often say "We want to", "I want to", "They want to" etc.


#### Practical Issues

-  Underflow
  we are multiplying probability values and those value lie between 0 and  1,  which can cause  value underlfow i.e the final value will be very close to zero.
  *Solution:*  Compute and add value in Log space and anyways addition is much faster than multiplication.
  $latexlog(p_1 \times p_2 \times p_3 \times p_4) = log(p_1) + log(p_2) + log(p_3) +log(p_4)$

-  Zeroes in  N-gram occurrence table
There may be words in the bigram that do not occur therefore the frequency value is zero but then the probability value will also come out to be zero in turn setting the probability of that whole sentence to  zero .	
*Solution:*  Use smoothing (comming soon!)


##### Toolkit for language modelling - SRILM
##### Large Corpus - Google N-grams
You can use this corpus to even analyse the popularity of a word from temporal aspect.


### Reference
-  [NLP NPTEL](https://youtu.be/Zy4UuCl_Gvg](https://youtu.be/Zy4UuCl_Gvg "Share link")
-  [Stanford University - N-gram Language Models](https://web.stanford.edu/~jurafsky/slp3/3.pdf)



