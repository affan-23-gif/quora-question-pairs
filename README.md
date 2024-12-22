# quora-question-pairs
A NLP project to find weather given 2 questions are same are not semantically speaking.


This repository explores machine learning models for identifying duplicate questions on the Quora platform.

**Problem Statement:**

Quora aims to provide users with the best possible experience by ensuring questions are not redundant. Duplicate questions can:

* **Decrease user experience:** Force users to sift through multiple versions of the same question to find the best answer.
* **Discourage writers:** Lead to writers answering the same question repeatedly.

By identifying and grouping duplicate questions, Quora can:

* **Improve user experience:** Direct users to the most relevant and comprehensive answers.
* **Enhance writer experience:** Reduce the need to answer repetitive questions.
* **Maintain data quality:** Ensure a high-quality dataset with unique and informative questions.

## Advanced Features for Quora Duplicate Question Detection

This document outlines the advanced features engineered for the Quora Duplicate Question Detection task. These features aim to capture nuanced similarities between questions beyond simple word counts.

**1. Token Features**

* **cwc_min:** This is the ratio of the number of common words to the length of the **smaller** question. This feature helps capture the relative abundance of common words in shorter questions.
* **cwc_max:** This is the ratio of the number of common words to the length of the **larger** question. This feature helps capture the relative abundance of common words in longer questions.
* **csc_min:** This is the ratio of the number of common stop words to the **smaller** stop word count among the two questions. Stop words are common words (e.g., "the," "a," "is") that often don't carry significant semantic meaning. This feature helps identify questions with similar stop word usage.
* **csc_max:** This is the ratio of the number of common stop words to the **larger** stop word count among the two questions.
* **ctc_min:** This is the ratio of the number of common tokens to the **smaller** token count among the two questions. Tokens can be individual words or sub-word units. This feature provides a more granular measure of commonality compared to word-level comparisons.
* **ctc_max:** This is the ratio of the number of common tokens to the **larger** token count among the two questions.
* **last_word_eq:** A binary feature that is 1 if the last word in the two questions is the same, and 0 otherwise. This captures potential semantic similarity based on the concluding words.
* **first_word_eq:** A binary feature that is 1 if the first word in the two questions is the same, and 0 otherwise. This captures potential similarity based on the initial keywords.

**2. Length-Based Features**

* **mean_len:** The average length of the two questions (measured in number of words). This feature captures the overall length of the question pair.
* **abs_len_diff:** The absolute difference in length between the two questions (measured in number of words). This feature helps identify questions with significantly different lengths, which might indicate lower similarity.
* **longest_substr_ratio:** The ratio of the length of the longest common substring between the two questions to the length of the **smaller** question. This feature captures the extent of sequential word matches.

**3. Fuzzy Features**

* **fuzz_ratio:** A string similarity score from the `fuzzywuzzy` library, capturing the overall similarity between two strings.
* **fuzz_partial_ratio:** A string similarity score from `fuzzywuzzy`, focusing on the best matching substring.
* **token_sort_ratio:** A string similarity score from `fuzzywuzzy` that compares strings after sorting their words alphabetically.
* **token_set_ratio:** A string similarity score from `fuzzywuzzy` that compares strings after converting them into sets of words.

These advanced features provide richer representations of question similarity beyond simple word counts. By incorporating these features into a machine learning model, we can significantly improve the accuracy of duplicate question detection.




