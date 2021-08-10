# Introduction to awk
<p>Awk is a scripting language used for manipulating data and generate reports. It is used for the advanced text processing and pattern matching. The awk command programming language requires no compiling, and allows the user to use variables, numeric functions, string functions and logical operators. 
<p>

<p>Awk is abbreviated from the names of developers- Aho, Weinberger, Kernighan.</p>

---

## What operations can AWK do?
* Scanning files line by line
* Splitting each input lines into fields.
* Comparing input lines and fields to pattern.
* Performing specified actions on matching line.
* It supports arithematic and string operations.
* It has conditionals and loops also.


## Awk Syntax

```
$ awk options 'selection_criteria { action }' input file > output file
```

## Commands
<p>Consider the following employee text file</p>

```
$ cat > employee.txt
```

```
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000
```
---
<p> Default behaviour awk: by default it prints all the line presents in the specified file. </p>

```
$ awk '{print}' employee.txt
```

<p>Output:</p>

```
ajay manager account 45000
sunil clerk account 25000
varun manager sales 50000
amit manager account 47000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
satvik director purchase 80000 
```

---
<p> Print the lines which matches with the given pattern. </p>

```
$ awk '/manager/ {print}' employee.txt
```

<p>Output:</p>

```
ajay manager account 45000
varun manager sales 50000
amit manager account 47000 
```

---

<p>Print the column that matches with the specific pattern
</p>

```
$ awk '/manager/{print $2 "\t" $4}' employee.txt
```

<p>Output:</p>

```
manager	45000
manager	50000
manager	47000
```

---

<p>Splitting a Line Into Fields </p>

```
$ awk '{print $1, $3}' employee.txt
```
<p>output:</p>

```
ajay account
sunil account
varun sales
amit account
tarun sales
deepak sales
sunil sales
satvik purchase
```

---

<p>Counting and printing matched pattern</p>

```
$ awk '/account/ {++cnt} END {print "Count = ", cnt}' employee.txt
```

<p>Output:</p>

```
Count =  3
```

---

<p>Print lines with more or less than a number of characters</p>

```
$ awk 'length($0) > 25' employee.txt
```

<p>Output:</p>

```
ajay manager account 45000
amit manager account 47000
satvik director purchase 80000
```
---

<p>Saving output of awk to different file</p>

```
$ awk '/manager/ {print $2 "\t" $4}' employee.txt > a.txt
```

<p>Output: Showing a.txt file</p>

```
manager	45000
manager	50000
manager	47000
```

---

<p>To find/check for any string in any specific column </p>

```
$ awk '{ if($3 == "sales") print $0;}' employee.txt
```

<p>Output:</p>

```
varun manager sales 50000
tarun peon sales 15000
deepak clerk sales 23000
sunil peon sales 13000
```

---

<p>To print the squares of the first n numbers</p>

```
$ awk 'BEGIN { for(i=1;i<=10;i++) print "Square of", i, "is" , i * i;}'
```

<p>Output:</p>

```
Square of 1 is 1
Square of 2 is 4
Square of 3 is 9
Square of 4 is 16
Square of 5 is 25
Square of 6 is 36
Square of 7 is 49
Square of 8 is 64
Square of 9 is 81
Square of 10 is 100
```
---

<p>To find the length of the longest line present in the file</p>

```
$ awk ' { if(length($0) > max) max = length($0) } END { print max }' employee.txt
```

<p>Output:</p>

```
30
```

---

# BUILT IN VARIABLES

<p>NR - To count the number of records in a file</p>

```
$ awk ' END {print "Number of records in a file is: ", NR}' employee.txt
```

<p>Output:</p>

```
Number of records in a file is:  8
```

---

<p>To display the line number using NR variable</p>

```
$ awk '{print NR,$0}' employee.txt 
```

<p>Output:</p>

```
1 ajay manager account 45000
2 sunil clerk account 25000
3 varun manager sales 50000
4 amit manager account 47000
5 tarun peon sales 15000
6 deepak clerk sales 23000
7 sunil peon sales 13000
8 satvik director purchase 80000
```

---

<p>NF - To display the number of fileds </p>

```
awk '{ print "Record:",NR,"has",NF,"fields" ; }' employee.txt
```

<p>Output:</p>

```
Record: 1 has 4 fields
Record: 2 has 4 fields
Record: 3 has 4 fields
Record: 4 has 4 fields
Record: 5 has 4 fields
Record: 6 has 4 fields
Record: 7 has 4 fields
Record: 8 has 4 fields
```

---

<p>To display the last field using NF variable</p>

```
$ awk ' {print $NF} ' employee.txt
```

<p>Output:</p>

```
45000
25000
50000
47000
15000
23000
13000
80000
```

---

# REFERENCES

* https://www.geeksforgeeks.org/awk-command-unixlinux-examples/

* https://www.journaldev.com/24871/awk-command-linux-unix

* https://www.tecmint.com/awk-built-in-variables-examples/







