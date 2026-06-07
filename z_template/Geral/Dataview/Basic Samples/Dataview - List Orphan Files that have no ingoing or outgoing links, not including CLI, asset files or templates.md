```dataview
LIST 
FROM "" AND !"3-Mechanics/CLI"
WHERE !contains(file.path, "zz_") AND (length(file.inlinks) = 0 AND length(file.outlinks) = 0) 
SORT file.name ASC
```