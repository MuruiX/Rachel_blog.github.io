---
LINK:
  - ""
  - "[[Text Mining]]"
  - "[[Natural Language Processing NLP]]"
File: Data Science/Natural Language Processing NLP/Distributional Semantics-Word Embeddings -Word Sense Disambiguation.md
---

how do we learn new words - for computers
- Looking into a dictionary: How to teach computers the meanings of <font color="#ffc000">semi-aquatic半截流</font>, tropical and the whole paragraph?
- Pointing to an object: How to teach computers to "understand" images?
- Which strategy is used? Similar contexts suggest similar meanings.
		→ Distributional hypothesis 分佈假設
- But
	- need to understand the meaning of contexts



##  Distributional hypothesis 

### history:
The meaning of a word is its use in the language 單詞的含義是他在語言中的使用

- If A and B have almost identical environments we say that they are synonyms [Zellig Harris (1954)]
- We shall know a word by the company it keeps.  [Firth (1957)]

### Formalisation:

Given word w and all the contexts $C (w) = \{c_{1} ,c_{2} ,...\}$ it appears within, then
$$
meaning (w) = f (c_{1},c_{2},...)
$$meaning (w) = f (c1,c 2,...)
where <span style="background:#fdbfff">f is a function</span> compressing some statistics of C (w) into a <font color="#ffc000">vector</font>.
The ultimate goal: find f!


## Co-occurrence vectors: word-word matrixes


1. Collect a lot of documents / sentences (from, e.g. Wikipedia)
	- a. .... the first digital computers were developed.
	- b. … the system stores enough digital data ...
2. Apply basic <font color="#ffc000">pre-processing steps</font>: lowercase小寫, tokenisation像征化, lemmatisation誘餌
3. Count how many times a word u appearing with a word v count (digital, computer) = 1670
4. The meaning of word u is vector [count (u, v1), count (u, v2),...]
![](PICTURE/Distributional%20Semantics/Pasted%20image%2020250202041159.png)


## 

Pros
The meaning of a word is represented by a vector (named word vector), therefore





Summary
● Distributional semantics is originated from distributional hypothesis
	○ Tell me who your friends are, I’ll tell you who you are
● A word is represented by a co-occurrence word vector
● Co-occurrence word vectors can be used to:
	○ detect the similarity among words
	○ visualise word meanings
	○ input to machine learning models

