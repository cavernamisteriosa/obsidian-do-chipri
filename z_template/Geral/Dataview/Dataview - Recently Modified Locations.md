```dataview  
TABLE WITHOUT ID link(file.name) AS "Location Name", type, Government, Community-Size, size, population  
FROM "1. World"
WHERE (NoteIcon = "Settlement")  
SORT file.mtime DESC
LIMIT 10
```
