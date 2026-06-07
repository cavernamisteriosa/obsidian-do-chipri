```dataview
TABLE WITHOUT ID link(file.name) as "Name", file.folder as "Folder"
WHERE contains(file.path, this.file.folder) AND file.name != this.file.name AND file.name != "Attachments"
SORT Folder ASC
```