Brandeis transition-based AMR Parser
==========

A Transition-based parser for [Abstract Meaning Representation](http://amr.isi.edu/).

Reference:

- Chuan Wang, Nianwen Xue, and Sameer Pradhan.2015. [A transition-based algorithm for amr parsing](http://aclweb.org/anthology/N/N15/N15-1040.pdf). In Proceedings of the 2015 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, pages 366–375, Denver, Colorado, May–June. Association for Computational Linguistics.

```
@InProceedings{wang-xue-pradhan:2015:NAACL-HLT,
  author    = {Wang, Chuan  and  Xue, Nianwen  and  Pradhan, Sameer},
  title     = {A Transition-based Algorithm for AMR Parsing},
  booktitle = {Proceedings of the 2015 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies},
  month     = {May--June},
  year      = {2015},
  address   = {Denver, Colorado},
  publisher = {Association for Computational Linguistics},
  pages     = {366--375},
  url       = {http://www.aclweb.org/anthology/N15-1040}
}
```


# Dependencies
First download the project:
      
      git clone https://github.com/Juicechuan/AMRParsing.git

Here we use a modified version of the [Stanford CoreNLP python wrapper](https://github.com/dasmith/stanford-corenlp-python), [Charniak Parser]() and [Stanford CoreNLP toolkit](http://nlp.stanford.edu/software/corenlp.shtml).
To setup dependencies, run the following script:
   
      ./scripts/config.sh



# Parsing with Pre-trained Model
The input data format for parsing should be raw document with one sentence per line. 
##Preprocessing
To preprocess the data, run:
   
      python amr_parsing.py -m preprocess [input_sentence_file]

This will give you the tokenized sentences(.tok), POS tag and name entity (.prp) and dependency structure (.charniak.parse.dep) (generated by Charniak parser and Stanford Dependency converter).
Download the model trained on training set of LDC2013E117 newswire section [here](www.cs.brandeis.edu/~cwang24/LDC2013E117.train.basic-abt-charniak.m). Then use the following command to parse the sentence:

      python amr_parsing.py -m parse --model [model_file] [input_sentence_file] 2>log/error.log


> **Note:** We use [JAMR](https://github.com/jflanigan/jamr) to get the alignment between sentence and its AMR annotation. You need to download and set up JAMR, then run the following script to get the aligned amr file:
```
      ./scripts/jamr_align.sh [input_file]
```