# [Naming Rules](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.NamingRulesDataTypes.html#HowItWorks.NamingRules)
-   All names must be encoded using UTF-8, and are case-sensitive.
-   Table names and index names must be between 3 and 255 characters long, and can contain only the following characters:
    -   `a-z`
    -   `A-Z`
    -   `0-9`
    -   `_`  (underscore)
    -   `-`  (dash)
    -   `.`  (dot)
-   Attribute names must be at least one character long, but no greater than 64 KB long.
	- The following are the exceptions. These attribute names must be no greater than 255 characters long:
	    -   Secondary index partition key names.
	    -   Secondary index sort key names.
	    -   The names of any user-specified projected attributes (applicable only to local secondary indexes).


Reserved Words and Special Characters
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ReservedWords.html
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTg5Njc1MV19
-->