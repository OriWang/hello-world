**Stopping**

- Stopwords: Function words, Prepositions(little meaning words).
  - Advantage: reduce index space, improve respond time, improve effectiveness.
  - Disadvantage: some function words can be important. Can not be removed.
- Stopword list from:
  - Domain knowledge and experience.
  - Identifying high-frequency words(Zipf).
- My thinking: About the disadvantage of stopwords.
  - Because one stopword can be meaningful in particular domain or when it combined with other words, adding this kind of words in the stoplist may cause meaning problem. So build the stoplist should base on the query and specific retrieve domain.



**Stopping**

In a text file some words are in high frequency and have little meaning on their own for example, prepositions a,an,this, that.etc. These words can be treated as stopwords. This means that the words are removed from the text during indexing.These stopwords have a lot of advantages like the increase in index space because of the removal of the words, there is an improvement in the response time and an improved effectiveness. But, sometimes due to the removal of these words some meaningful sequence of the words can be lost. These lists for stopwords are created from domain knowledge and experience which is called the standard list, or through a statistical identification of high frequency words. The lists can be customised for applications, domains and even for certain parts of documents. For example for the hospital records the stopwords would be customized accordingly. The query time is the best time to take decisions about the stop words list . This decision time does not make a difference to the index space.

**Stemming**

The words in a document can have various morphological variations like the plural forms for the words for example, dog->dogs, supply-> supplies. These morphological variations usually have the similar meaning since, these only vary according to the tenses and plurals. 
The stemmers usually reduce the words to a common stem hence, the word stemmers. These usually work by removing the suffixes of the words. Unlike, stopping this can be done at both the indexing time as well as during the query processing. The stemming varies from one language to the other. This can be very effective in one language and may not be as effective in another language. For some languages, since they contain a root for most of their words, stemmers are very useful compared to other languages.

Stemming can be of two types namely,
Dictionary based : Here, the stemmer compared the words in the text with a pre-existing list of words.
Algorithmic: For these kinds of stemmers, a program is used to determine related words. Here, the program removes the suffixes and then aligns the similar words. The algorithmic stemmers increase the chances of a false negative as well as a false positive. A subset of the algorithmic stemmer are the statistical stemmers
Statistical Stemmers: These stemmers make uses of supervised or unsupervised learning to learn the stemming rules of a language through corpus.This makes the stemming language independent and can be used without any prior knowledge of the language.
Based on the general types of stemming techniques, there are different types of stemmers. Some of these are:
Porter Stemmer
Krovetz Stemmer

**2.1. Porter Stemmer**

The porter stemmer is, essentially, an algorithmic stemmer. This technique has been around since the 1970s. The stemmer consists of a series of rules designed to remove the longest possible suffix. Like, the function of algorithmic stemmers they create stems. Inspite, of the rules the stemmer is bound to make errors and it is difficult to modify the stemmer.

**2.2. Krovetz Stemmer**

The Krovetz stemmer is a hybrid of an algorithm and dictionary. The stemmer first checks the word in the dictionary. If the word is present in the dictionary, then the word is separated. If the word is not present in the dictionary then the word is checked for suffixes that could be removed and after the removal of the suffixes the dictionary is checked again. Unlike the algorithmic stemmer, the Krovetz Stemmer produces words and not stems. It is more effective than the porter algorithm. The Krovetz algorithm produces lower false positive and higher false negative.

**Porter v/s Krovetz Stemmers**

| Porter                              | Krovetz               |
| :---------------------------------- | --------------------- |
| Algorithmic                         | Hybrid                |
| More errors and difficult to modify | More effective        |
| Higher false positive               | Higher false negative |
| Produce stems                       | Produce words         |




**INDEXING PROCESS**

The document goes through a series of text pre-processing as discussed above.We can extract more features like the links and metadata etc. The extracted features are stored in an index which is an inverted index which contains the frequency of occurrence of the terms along with the position information of the word. Separately, we store features(a feature is an automated document expressed  numerically).These data structures are used for retrieving and ranking documents according to the query.The ranking function depends upon from the index terms and additional features being extracted and sometimes, even query functions. 

**INVERTED INDEX**

Constituted of at least one index term. To each index term, there is a corresponding list of terms which is an inverted list. This inverted list is usually in increasing document order. THis is for efficiency purposes.Each inverted term contains one or more atomic elements called a posting. These are pointers to a specific document location. More advanced indexes exist for example, the ones the more positioning information or frequency information. 
How inverted lists can be used for faster retrieval? Scroll through the list of index terms starting from the first letter until we can find the target term. If there are more than two words then, we scroll through the list searching for entries on the two terms.We add the proximity of the query.

**Field Indexing**

Documents are semi-structured.e.g. Webpages. The content is mixed with some markup. A query might match a number of webpages.One of the webpage is a better match for the query.How to maintain a field information into an index? We can separate the inverted list for each field that is, forming an index for every field. Then, finding a word in the inverted list. We can, also, store the field information into each word posting. This can be done by adding one or more bits at the end of the posting. The disadvantage with this approach is that if there are many fields then we would require many bits for storing. This would increase index space and reduce the efficiency of the search engine. These approaches are also unable to determine if two worlds are in close proximity. The proximity problem can be solved with the help of an extent.  An extent is a contiguous region in a document.The extent can be expressed using word positions.The inverted list will record all the extents with the start and finish of a list.

