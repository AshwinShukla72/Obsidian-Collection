> The Bash shell is also run in a Non-Interactive way, by usage of scripts, making shell not require human interaction and instead allow automation

- FileType of #bash scripts is .sh
```bash
#!bin/bash 
echo "Hello World"
```

- ==The First Line of the file, #!bin/bash== instructs the operating system to run /bin/bash , the Bash shell, passing it the script's path as an
argument.
- Run ==chmod +x fileName.sh== to run the file in executable form
- 