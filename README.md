# RTN
The RTN-Method or Recursive Tree-based N-gram method, recursively calculates the weighted precision and recall scores from lower-grams to the higher-grams in a bottom-up approach. It also implements lemmatization for fairer evaluation.
## Approach
The RTN-Method takes upon BLEU’s as the base concept and builds upon it to eliminate some of its drawbacks.
* To address the problem of only considering false-positives (in BLEU), F1-score is introduced which is a combination of both precision and recall and hence deals with false positives and false negatives- striking a good balance between quality(precision) and completeness(recall).
* Weights are assigned to different parts-of-speech in a sentence so as to ensure the significance of different words in a sentence are reflected properly in the scoring unlike in BLEU where each word has the same weightage. The weights have been empirically determined to maintain consistency of scores and best reflect the significance of different words in a sentence.
* Initially only unigram could reflect this weighted measure of precision and recall. However, a tree-based bottom-up approach was eventually adopted that successfully propagated the effect of weighted scores from the lower-grams to the higher-grams in a recursive manner to get RTN-recall and RTN-precision scores as shown in 3.2 Demonstration. 
* The concept of lemmatization is introduced. When exact matches are not found, the words are lemmatized- which means they are reduced to their base forms called lemma- to establish a canonical representation.  Words having the same base form are penalized partially, while different base forms are assigned 0.
* Finally, to account for the discrepancies such as the presence of redundant words in candidate statement or shorter length of candidate statement than the reference statement, we multiply the precision score with the brevity penalty(bp) same as in the BLEU model, and a new penalty called the redundancy penalty(rp) given by the ratio of length of candidate statement without redundancy to the length of candidate statement with redundancy.
## Demonstration 

