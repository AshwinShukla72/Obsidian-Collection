
- new folder
```powershell
New-Item -Path "./[File_Path]" -Item-Type Directory -Name "[FileName]" 
```

- new file
```powershell
New-Item -Path "./[File_Path]" -ItemType file -Name "main.go"
```

- Delete Files
```powershell
Remove-Item -v "[FileName]" || "*.[FileType]"
```

- Rename Files
```powershell
Rename-Item -Path "[./FilePath]" -NewName "[NewName]"
```

- List Items in File
```powershell
Get-ChildItem "./[Directory_Path]"
```

- Print Content of File
```powershell
Get-Content "./[File_Path]"
```
