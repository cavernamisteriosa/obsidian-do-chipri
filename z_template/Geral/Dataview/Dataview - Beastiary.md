```dataview
TABLE WITHOUT ID link(file.name) AS Monster
WHERE contains(file.inlinks, this.file.link) AND SourceType = "Bestiary"
```