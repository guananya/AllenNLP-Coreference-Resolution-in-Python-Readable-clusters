# AllenNLP-Coreference-Resolution---Readable-clusters
## Using AllenNLP Coreference Resolution in Python (getting clusters which are ACTUALLY readable)

There's been a dearth of documentation on the front of how to use AllenNLP's amazing coreference resolution. While the code to use it as a library in python is available on the site (https://demo.allennlp.org/coreference-resolution), once you get the results its quite confusing initially to know what to make of them. I hope that this repository is useful to you in using this poweful, pre-trained Natural Language Processing model.

Here is the code on how to analyze the AllenNLP coreference clusters to make them "human readable".

The idea is that the clusters are formated as [[[a,b],[c,c]], [[d,d],[f,g]]. So, theres a list inside a list, and within that another 2 lists (okay this isn't helping). So, let me explain this using the "innovative" indexes I've used.

Let us begin with the innermost lists. Lets take [a,b] as an example. So, the document is first converted to a list of words. Now, 'a' is a number that corrosponds to the word at the 'a' index in the document and 'b' to the 'b'th word in the document. These two words and all the words between them together form a cluster with [c,c]. The [c,c] is only one word since all the words between the 'c'th and the 'c'th word are only the 'c'th word. Together, these two form a cluster and are hence part of their own, personal list. The same entity is referenced between the words from 'a' to 'b', as well as at 'c'.

We can take example of [[0,1],[5,5]]. The document for this example is "my(0) mother(1) was(2) happy(3).(4) She(5) gave(6) me(7) a(8) pat(9) on(10) the(11) back(12)". Hence, "my[0] mother[1]" is referenced again as "she[5]". As you can see, each word(and even the punctuation) is given an index, which is used within the coreference cluster. The same example is used in allennlp_coref.py and you can try it out yourself!!
