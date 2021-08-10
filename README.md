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








