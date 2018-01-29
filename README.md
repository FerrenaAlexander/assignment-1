# assignment-1
####Alexander Ferrena
####apf2139


##Section 1: get data.

I had a problem with the Git Bash program (no permissions?) so I used MobaXTerm.
I could neither use nor install curl, so I just used wget:

'''
wget http://eaton-lab.org/pdsb/test.fastq.gz
wget http://eaton-lab.org/pdsb/iris-data-dirty.csv
```

I used both less and zless on both files. The test.fastq.gz is currently gzipped and therefore unintelligible. The iris-data-dirty file appears to be a data matrix of some kind, containing numbers in the 4 columns and the species name in the 5th; there are several NAs in the number columns and several misspellings in the species column.

