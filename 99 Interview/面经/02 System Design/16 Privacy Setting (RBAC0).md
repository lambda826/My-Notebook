Different levels of privacy
-   PUBLIC:
-   FRIENDS_ONLY: 
-   PRIVATE:

```sql
db.documents.find( { $or : [
     { public : true },
     { users  : X },
     { groups : { $in : [list-of-X's-groups] } }
] } )
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTk5OTE2NzQ5LC01Nzg0MTY4NjVdfQ==
-->