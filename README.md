# Multi-dimension Diversification in Legal Information Retrieval

This page is a companion for the WISE 2016 paper on [Multi-dimension Diversification in Legal Information Retrieval] (http://dx.doi.org/10.1007/978-3-319-48740-3_12), written by Koniaris Marios (me), Ioannis Anagnostopoulos and Yannis Vassiliou. This page hosts the complete dataset, ground-truth data, queries and relevance assessments we utilize in the article. Our goal is to encourage progress on the diversification in legal IR.

## Dataset
* [CourtListener](https://www.courtlistener.com/api/bulk-info/)
> Our corpus contains 63,742 precedential legal cases from the [Supreme Court of the United States](http://supremecourt.gov/). The cases were originally downloaded from [CourtListener](https://www.courtlistener.com/). The legal corpus contains all cases from the Supreme Court of the United States, covering more than two centuries of legal history, spanning from 1754 up to 2015. We extracted from the cases text all the necessary information for our feature selection framework e.g. relationships to other documents, date of Judgment.  RESTful API detailed instruction can be found  [here](https://www.courtlistener.com/api/rest-info/).

* [Supreme Court Database](http://scdb.wustl.edu/data.php?s=6)
> Since our corpus was initially unclassified, we acquired topical taxonomies from the Supreme Court Database using commonly shared unique identification variable SCDB Case ID. Topical taxonomies within Supreme Court Database are the outcome of a manual analysis and interpretation of the legal provisions considered in each case. An introduction to the Online Code Book can be found [here](http://scdb.wustl.edu/documentation.php?var=intro), while download and use instructions can be found [here](http://scdb.wustl.edu/data.php?s=3).


## West Law Digest Topics

West Law Digest Topics  is a taxonomy of identifying points of law from reported cases and organizing them by topic and key number. It is used to organize the entire body of American law.

1. [WikiPedia entry](https://en.wikipedia.org/wiki/West_American_Digest_System)
2. [PDF list](https://info.legalsolutions.thomsonreuters.com/documentation/westlaw/wlawdoc/wlres/keynmb06.pdf) 
 > we downloaded this list from WestLaw, process it and acquired a textual representation of it.
3. [Original Topics/queries](https://github.com/mkoniari/MultiLegalDiv/blob/master/westlaw.txt)
> Each topic was issued as candidate query to our retrieval system. Outlier queries, whether too specific/rare or too general, where removed using the interquartile range, below or above values Q1 and Q3, sequentially in terms of number of hits in the result set and score distribution for the hits, demanding in parallel a minimum cover of min|N| results.
4. [Used Topics/queries](https://github.com/mkoniari/MultiLegalDiv/blob/master/QUERIES.txt) 
> Our final list of user queries. In total, we kept 330 queries.

## Query assessments and ground-truth.

For each topic/query we kept the top-n results. An LDA topic model, using an open source implementation ([mallet](http://mallet.cs.umass.edu/)) was trained on the  top-n results for each query. From the resulting topic distributions for each document, with an acceptance threshold of 15%, we consider relevance judgments for each query/ document and subtopic. In other words, we consider the topics created from LDA as aspects of each query, and based
on the topic/ document distribution we can infer whether a document is relevant for an aspect. In total, we acquired 1,650 subtopics for all the 330 queries. Our ground-truth data can be found:
* [Qrel format](https://github.com/mkoniari/MultiLegalDiv/blob/master/qrels.txt)
* [Compact format](https://github.com/mkoniari/MultiLegalDiv/blob/master/aspects.txt)

### Stop Words
Our stop word list can be found [here](https://github.com/mkoniari/MultiLegalDiv/blob/master/stopwords.en)