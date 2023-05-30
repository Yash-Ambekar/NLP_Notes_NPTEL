- **Extrinsic evaluation**. This involves evaluating the models by employing them in an actual **task** (such as machine translation) and looking at their final loss/accuracy. This is the best option as it’s the only way to tangibly see how different models affect the task we’re interested in. However, it can be computationally expensive and slow as it requires training a full system.
  
- **Intrinsic evaluation**. This involves finding some metric to evaluate the language model itself, not taking into account the specific tasks it’s going to be used for. While intrinsic evaluation is not as “good” as extrinsic evaluation as a final metric, it’s a useful way of **quickly** comparing models. **Perplexity is an intrinsic evaluation method.**

### Perplexity ( PP(W) )

-  Perplexity is the inverse probability of the test data, normalized by the number of words: 
  
![[Pasted image 20230525112844.png]]
![[Pasted image 20230525112903.png]]

-  **Lower** the **perplexity** **better** is the **model**. It means the model is less confused (perplexed) to select the next word.

Example I: 
![[Pasted image 20230525122545.png]]

Example II : 
Wall Street Journal
![[Pasted image 20230525122830.png]]


## Shannon Visualization Method

-  It is a method of generating sentences from the trained language model.
- Suppose the trained language model is bigram then Shannon Visualization Method creates sentences as follows:
-  Choose a  bigram ($<S>$, w) according to its probability. Now choose a  bigram (w, x) according to its probability and so on until we choose $</S>$ . Then string the words together .
-  Here $<S>$ and $</S>$ signifies the start and end of sentences respectively.

For Example
![[1 WNyDJ177qNDAkTPBDCGCYw.webp]]
