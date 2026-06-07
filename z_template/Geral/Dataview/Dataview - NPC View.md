```dataview  
TABLE WITHOUT ID link(file.name) AS "NPC Name", Gender, Race, Age, Location, AssociatedGroup  
FROM "2. Mechanics/Non-Player Characters"
WHERE (NoteIcon = "npc") 
SORT file.mtime DESC
LIMIT 10
```