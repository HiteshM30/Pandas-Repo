
# Pandas- Quick Recap

Pandas is a Python library used for working with data sets.

It has functions for analyzing, cleaning, exploring, and manipulating data.

Before Getting started with Pandas, let's revise file handling in python.


## File Handling

The key function for working with files in Python is the open() function.

The open() function takes two parameters; filename, and mode.

There are four different methods (modes) for opening a file:

"r" - Read - Default value. Opens a file for reading, error if the file does not exist

"a" - Append - Opens a file for appending, creates the file if it does not exist

"w" - Write - Opens a file for writing, creates the file if it does not exist

"x" - Create - Creates the specified file, returns an error if the file exists

To open a file for reading it is enough to specify the name of the file:
 
    f=open("demofile.txt","rt")

To write into an existing file, we use

    f = open("demofile2.txt", "a")
    f.write("Now the file has more content!")
    f.close()

    #open and read the file after the appending:
    f = open("demofile2.txt", "r")
    print(f.read())

To create a file called "myfile.txt":

    f = open("myfile.txt", "x")
## Pandas

-Importing the library
Pandas Library can be imported directly into your code using the import command

    import pandas as pd

-Reading a csv file

    poke=pd.read_csv('pokemon_data.csv')
    print(poke.columns)

-Printing Columns

    print(poke['Name'])

-Printing Rows

    print(poke.iloc[0:4])

-Iterating through each row

    for index, row in poke.iterrows():
    print(index,row['Name'])

-Getting rows based on condition

    poke.loc[poke['Type 1']=='Fire']

-Describing data (Describing provides all the mathematic values of the distribution like mean, mode, median etc.) 

    poke.describe()

-Sorting data (Single row), Make ascending=True for sorting in ascending order and vice-versa
    
    poke.sort_values('Name',ascending=False)

-Sorting data (Multiple rows)

    poke.sort_values(['Type 1','HP'],ascending=[1,0])

-Adding Columns
    
    poke['Total']= poke['Attack']+poke['Defense']
    poke.head(5)
 head(n) function provides the values of n rows of the distribution 

-Removing Columns

    poke=poke.drop(columns=["Total"])
    poke.head(5)

-Adding Columns using iloc and sum axis. Use axis=1 for horizontal and axis=0 for vertical
    
    poke["Total"]= poke.iloc[:,4:10].sum(axis=1)
    poke.head(5)

-Rearranging the columns
    
    cols=list(poke.columns)
    poke=poke[cols[0:4]+[cols[-1]]+cols[4:12]]
    poke.head(5)

-Saving the file
    
    poke.to_csv("NewPoke.csv", index=False)
 To remove the index values from the distribution, we make it's value false

