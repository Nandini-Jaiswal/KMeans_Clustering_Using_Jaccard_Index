---
Title: "Clustering Documents using K-means with Jaccard Similarity"
Author: "Nandini Jaiswal"
Date: "2024-07-07"
---

# Introduction

The "Bag of Words" data set from the UCI Machine Learning Repository contains five text collections in the form of bags-of-words. Our task is to cluster the documents in these datasets via K-means clustering for different values of K and determine an optimum value of K. We will use the Jaccard index as the similarity measure, which considers the overlap of words present in both documents, effectively changing the model from "bag of words" to "set of words".

The datasets are of different sizes. We will report results on the three smaller datasets (Enron emails, NIPS full papers, KOS blog entries).

# Data Description

Each text collection is summarized as a bag (multiset) of words. The individual documents are identified by document IDs and the words are identified by word IDs.

For each collection XYZ:

- `vocab.XYZ.txt` is the vocabulary file, listing all words that appear in the collection XYZ, one word per line. Each word has an implicit wordID that is its line number in this file, starting with 1.
- `docword.XYZ.txt` lists the number of times each word in `vocab.XYZ.txt` occurs in each document (only non-zero counts are recorded).

The `docword.XYZ.txt` file begins with 3 header lines:
- D
- W
- NNZ

where `D` is the number of documents, `W` is the number of words whose frequency is counted, and `NNZ` is the number of non-zero frequency entries.

This is followed by `NNZ` lines of the form:
- docID wordID count

where `count` is the number of times the word with id `wordID` appears in the document with id `docID`.

# Datasets Information

### Enron Emails
- Original Source: [www.cs.cmu.edu/~enron](http://www.cs.cmu.edu/~enron)
- `D=39861`
- `W=28102`
- `N=6,400,000` (approx)

### NIPS Full Papers
- Original Source: [books.nips.cc](http://books.nips.cc)
- `D=1500`
- `W=12419`
- `N=1,900,000` (approx)

### KOS Blog Entries
- Original Source: [dailykos.com](http://dailykos.com)
- `D=3430`
- `W=6906`
- `N=467714`

# Methodology

We will follow these steps:

1. Load and preprocess the data.
2. Compute the Jaccard distance for the documents.
3. Perform K-means clustering for different values of K using Jaccard distance as a similarity measure.
4. Determine the optimum value of K (elbow point).

# Conclusion

The elbow point for each dataset and the model fit point for each dataset is given as follows--

- For KOS blog entries, Elbow is 4, Model fit time is 1207.48 seconds.

- For NIPS full papers, Elbow is 2, Model fit time is 805.85 seconds.

- For Enron emails, Elbow is 1, Model fit time is 2196.09 seconds.
