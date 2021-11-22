# What is Autocomplete (Typeahead)
- Autocomplete is a popular feature of search engines.
- As the user types something in the search box, this feature creates suggestions to complete the sentence for what the user has already typed.
	- These suggestions come from the queries that users have already searched in that search engine and the popularity of these searches.
	- A query that has been searched several times will appear among the top suggestions.

# Keyword
Trie
Realtime
Large scale

# Requirements
## Functional
- The service should suggest top 10 terms starting with whatever the user has typed.

## Non-functional
- Low latency (deliver the suggestions in **real-time**).
- High scalability (scale to a large number of requests).
	- Assume 10 billion queries per day.
- Highly available.


# Follow up questions
- **How to find top suggestion?**
- Case sensitive
- Handle different language






# References
- [System Design Interview: Autocomplete/Type-ahead System for a Search Box](https://medium.com/double-pointer/system-design-interview-autocomplete-type-ahead-system-for-a-search-box-1ac968f9f121)
- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMDUyNjY5NTgsLTc3MTc0MTkxOCw1Nz
MyNzY4MDUsLTk1MTU3ODI1Nl19
-->