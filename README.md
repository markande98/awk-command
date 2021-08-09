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




