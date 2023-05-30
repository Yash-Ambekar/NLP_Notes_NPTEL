-  It is used to handle probabilities of word having zero value  $i.e$  the words that exist in test set do not exist in the training set. Therefore the language model assigns zero probability to the test set.
For example:
![[Pasted image 20230525130612.png]]


With sparse statistics there is a problem of evaluating the model using perplexity.
-  To solve this problem we have to steal probability mass to generalize better.
  
  For example:
  ![[Pasted image 20230525131001.png]]


### Add  -  1  smoothing (Laplace Smoothing)

-  Pretend that we saw each word(N-Gram) one more time than we actual did  $i.e$  add  $1$  to all the counts.

**For Bigram**
![[Pasted image 20230525131430.png]]

$V$ --> Vocabulary size
$c$ --> count of the words

-  We are adding $V$ in the denominator since there are $V$ number of unique vocab words and we increase the count of each Bigram by 1 .
- We do this to normalize the probability value.


##### Effective Bigram Count
-  Just equate the P$_M$$_L$$_E$  to P $_A$$_d$$_d$$_-$$_1$  like this 
  
  ![[Pasted image 20230525133000.png]]

$C$ $^*$  ---> Effective Bigram Count
LSH ---> P$_M$$_L$$_E$
RHS ---> P $_A$$_d$$_d$$_-$$_1$ 

Example: 
![[Pasted image 20230525133225.png]]



### Unigram Prior Smoothing

-  The very first equation in the image below is the generalized formulation for smoothing  $i.e$ 
  $Add-k$   smoothing.
-  Suppose, we say  $kV = m$  then $k = m/V$ 
  
![[Pasted image 20230525134153.png]]

P(w $_i$) --> Unigram probability of each word.




