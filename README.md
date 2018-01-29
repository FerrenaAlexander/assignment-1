# assignment-1
#### Alexander Ferrena
#### apf2139


## Section 1: get data.

I had a problem with the Git Bash program (no permissions?) so I used MobaXTerm.
I could neither use nor install curl, so I just used wget:

```
wget http://eaton-lab.org/pdsb/test.fastq.gz
wget http://eaton-lab.org/pdsb/iris-data-dirty.csv
```

I used both less and zless on both files. The test.fastq.gz is currently gzipped and therefore unintelligible. The iris-data-dirty file appears to be a comma-separated data matrix, containing numbers in the 4 columns and the species name in the 5th; there are several NAs in the number columns and several misspellings in the species column.

## Section 2: clean data.

I scanned the list by eye and noticed two spelling errors, the first mispelled "setosa" to "setsa" and the second using the British spelling of "colour" rather than keeping with the matrix' pattern of spelling "versicolor". I used the following lines of code to determine the line of each:

```
grep -n setsa iris-data-dirty.csv
grep -n colour iris-data-dirty.csv
```

I determined there were spelling errors in lines 12 and 51. I corrected the mispellings in a backup file:

```
sed 's/setsa/setosa/g' 1iris-data-dirty.csv > 1iris-data-dirty.csv
sed -i 's/versicolour/versicolor/g' 1iris-data-dirty.csv
```

Then, I used the following in order to remove the NAs and save the output as "clean" data.

```
sed '/NA/d' 1iris-data-dirty.csv > iris-data-clean.csv
```

Finally, I used the following to count the number of rows associated with each species.
```
cut -b 22-26 iris-data-clean.csv | uniq -c
```

The output I received was:
     50 setos
     48 versi
     50 virgi

The Iris versicolor data originally contained two rows with NAs which were removed, leaving just 48 rows. The other two species, Iris setosa and Iris virginica, both had 50 rows of data.

