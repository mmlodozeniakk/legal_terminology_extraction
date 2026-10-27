TERMINOLOGY EXTRACTION: AI-DRIVEN AND STATISTICAL APPROACH COMPARISON:
A comparative evaluation of statistical and generative extraction models conducted on European Union legal corpora

GOAL OF THE ANALYSIS:
This project aims to extract and evaluate key terminology from EU legal texts related to artificial intelligence by comparing statistical and AI-driven approaches. The corpora used in the analysis consist of documents retrieved from the official EU legal database, EUR-Lex (eur-lex.europa.eu). All of the chosen files regard the topic of use and regulation of artificial intelligence within the European Union 

METHODOLOGY:
In order to download, save and prepare the data, the pymupdf library was used. Furtherly, with help of pandas, the parsed legal PDFs could be converted into structured DataFrames. To conduct linguistic analysis of nominal candidate terms, the spacy extention was employed. It was also used to filter out grammatical words that do not provide desired linguistic information, in accordance to Zip'f law. The scikit-learn library was used to perform statistical weighting by configuring TfidfVectorizer in order to extract n-grams ranging from one to three words and assign scores to terms based on their relevance to the domain under study
Additionally, a comprative benchmark of possible terms was generated using an appropriate zero-shot prompt for a large language model (LLM). ChatGPT was chosen to ensure a more robust comparison, given its widespread adoption in contemporary NLP research and industry applications, as well as its advanced semantic and contextual understanding. Finally, both sets of candidate terms were subjected to Human-in-the-Loop Validation in order to assess the performance of each approach. Terms considered relevant to the topic and sufficiently specific to the domain were assigned a score of "1". Conversely, terms considered too generic ot insufficiently precise for the domain received a score of "0". Finally, precision was calculated for both approaches.

EVALUATION AND RESULTS: 
Precision was calculated as the proportion between true positive terms relative to all individuated candidates. Precision= TP/TP+FP
--> Statistical Approach: Precision 40% 
--> Generative Approach with LLM: Precision 40% 

KEY FINDINGS: 
The precision of statistical and generative approaches was exactly the same when comparing the extracted samples. This suggests that although both TF-IDF and LLMs can effectively identify high-frequency vocabulary, this does not necessarily translate into domain specificity.
The main source of receiving a FP result in both approaches was the truncation of multi-word terms to single words. Instead of considering the term as a whole, the methods often selected only a fragment that appeared more frequently across different contexts. This tendency was particularly noticeable in terms such as "services", "regulations" and "security". Interestingly, some false positives were identified by both approaches, suggesting that both struggle to determine whether a term should be treated as a single word or as a pert of a multi-word expression. Unigram candidates often captured general legal vocabulary or overly broad nouns. However, overlap was also observed among TPs, including terms such as "digital", "cybersecurity" and "Member States".
In conclusion, neither TF-IDF nor zero-shot LLMs provided a sufficiently accurate list of terminology extracted from the legal texts. Human expertise therefore remains indispensable, particulatly in institutional environments, where it is needed to filter out FPs and develop standardized glossaries. 

PROJECT STRUCTURE: 

terminology-extraction/
├── data/                    
├── notebooks/
│   └── terminology_extraction.ipynb  
├── results/
│   ├── candidate_terms.csv                           
└── README.md                