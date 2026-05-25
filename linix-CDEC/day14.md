linux serching and filter utilities 
## commands 
```
cat --> concatinate file containtaints 
grep --> file containent scerch ; 
sort --> to sort the files in alfabatical order 
uniq ---> not showing duplicate data 
find --> fiend the file (size, type, date ,name)
head ---> print first 10 lines 
tail ---> print last 10 line 
- Overview of Key Utilities: grep, cat, sort, UNIQUE
```

## practice (HW)
- read file using grep 
- read file using cat
- read file using sort  
- read file using uniq 
- see the difference between all the commands 

scerch file using find 
- scerch using name 
- scerch using type 
- scerch using size 


- Basic Syntax of FIND

---------------------------------
```
 sudo find /etc -name os-release
    9  sudo find /etc -size 10m
   10  sudo find /etc --size 10m
   11  sudo find /etc -size 10M
   12  sudo find /etc -size 1M
   13  sudo find /etc -type .txt
   14  sudo find /etc -type txt
   15  sudo find /etc -type txt --help
   16  sudo find /etc -type f -iname "*.txt"
   17  ls /etc/
   18  sudo find /etc -type f -iname "*.conf"
   19  sudo find /etc -date f -iname "*.conf"
   20  sudo find /etc -type f -mtime -10
   21  sudo find /etc -type f -mtime -1
   22  man find 
```








