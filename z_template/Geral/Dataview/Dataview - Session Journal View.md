
```dataview
TABLE WITHOUT ID link(file.name) AS "Session Date", Status, players, OneLiner
from "2. Session Journals/Deadly Depth Inn"
where (type = "Session Journal")
SORT file.name DESC
```
