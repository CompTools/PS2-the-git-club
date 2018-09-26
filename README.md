# Problem Set 2

## Group project
This is a group project.
You should work in groups of 2 to 4 (not alone and not more than 4). If this is a problem, please let me know ahead of time.

## Due date
You will have time in class between 9/12/18 and 9/21/18 to work on this project. **It is my hope that is can be turned in on Friday, 9/21**, but I will take it until 9/28 at the latest.

# The dataset
I have provided a dataset that you will use for this. The dataset and it's description are on the cluster as well as in github.
 * The dataset is at: `/ufrc/zoo6927/share/Class_Files/data/flights.May2017-Apr2018.csv`
 * The metadata (description of the data) is at: `/ufrc/zoo6927/share/Class_Files/data/flights_metadata.md`
     * It is also [nicely rendered on github](https://github.com/CompTools/Class_Files/blob/master/data/flights_metadata.md).

# Instructions

The goal of this project is to write a Bash script that:
1. Counts the number of flights that were delayed more than 15 minutes into or out of Gainesville, FL (airport code GNV) during the timeframe covered by the dataset. (*2 points*)

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $13 ~ /1.00/' | wc -l


awk 'BEGIN{FS=","} $7 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $16 ~ /1.00/' | wc -l



2. Produces a table (text is fine) with the data to fill in this table (*13 points*):


GNV to: | Total flights | Total flights delayed (>15min) | Total flights delayed due to Weather
--------|---------------|------------------------|-------------------------------
ATL |
CLT |
MIA |

#The following three lines of code count the total number of flights, total number of flights delayed greater than fifteen minutes, and the total number of flights delayed due to weather from GNV to ATL.

ATL
awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"ATL"/' | wc -l = 1476

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"ATL"/' | awk 'BEGIN{FS=","} $13 ~ /1.00/' | wc -l  = 262

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"ATL"/' | awk 'BEGIN{FS=","} $24 >0.00' | wc -l  = 15

#The following three lines of code count the total number of flights, total number of flights delayed greater than fifteen minutes, and the total number of flights delayed due to weather from GNV to CLT.

CLT
awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"CLT"/' | wc -l = 476

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"CLT"/' | awk 'BEGIN{FS=","} $13 ~ /1.00/' | wc -l  = 107

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"CLT"/' | awk 'BEGIN{FS=","} $24 >0.00' | wc -l  = 3

#The following three lines of code count the total number of flights, total number of flights delayed greater than fifteen minutes, and the total number of flights delayed due to weather from GNV to MIA.

MIA
awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"MIA"/' | wc -l = 205

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"MIA"/' | awk 'BEGIN{FS=","} $13 ~ /1.00/' | wc -l  = 30

awk 'BEGIN{FS=","} $3 ~ /"GNV"/' flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $7 ~ /"MIA"/' | awk 'BEGIN{FS=","} $24 >0.00' | wc -l  = 0



3. Within a function, prints a list of all unique airport codes contained in the dataset. (*3 points*)

#This code searches the flights csv file, selects two columns that contain unique airport codes both for Arrival and Destination, and lists the resulting contents of those columns. 

cat flights.May2017-Apr2018.csv | cut -d, -f3,7 | sort | uniq

4. Within a function lists the cities in Florida that have airports in the dataset. (*2 points*)
grep –F –w “FL” flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $5~/FL/ {print $4}
#origin cities in florida'

grep –F –w “FL” flights.May2017-Apr2018.csv | awk 'BEGIN{FS=","} $9~/FL/ {print $8} 
#destination cities in florida'

**Bonus question:**  Asks for user input (see chapter 28) to enter either a airport code or city, state name and then calculates the number of flights as in question 1. (*5 points extra credit*)

# To submit
You should submit your answer as one or more scripts in a git repository. Submit the link in Canvas.

You should start in Canvas, creating your group and then create the same group in github.

# Grading
For questions, 1, 3 and 4, I will mostly be looking for the right answer.

**Your score on 1,3,4 (I'll fill this in when I grade):**


For question 2, you will receive points for:

Rubric item | Points | Your score
------------|--------|-----------
Using github| 1 point |
Having at least one commit from each member of the team | 2 points |
Using meaningful commit messages | 2 points |
Using functions correctly | 2 points |
Using comments in code | 2 points
Using spacing to make code readable | 2 points |
Getting the correct answer | 2 points |

**Extra credit:**

**Total points:**
