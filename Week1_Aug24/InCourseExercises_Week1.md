---
title: "Week 1— In Course Exercises"
author: "Brooke Anderson"
date: "August 23, 2015"
output: html_document
---

# About the dataset

For today's class, you'll be using a dataset of all the guests on Jon Stewart's *The Daily Show*. This data was originally collected by Nate Silver's website, [FiveThirtyEight](http://fivethirtyeight.com) and is available on [FiveThirtyEight's GitHub page](https://github.com/fivethirtyeight/data/tree/master/daily-show-guests) under the [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/). The only change made to the original file was to add (commented) attribution information at the start of the file.

**First, check out a bit more about this data and its source:**

* Check out [the Creative Commons license](http://creativecommons.org/licenses/by/4.0/). What are we allowed to do with this data? What restrictions are there on using the data?
* It's often helpful to use prior knowledge to help check out or validate your dataset. One thing we might want to know about this data is if it covers the whole time that Jon Stewart hosted *The Daily Show*. Find out the dates he started and finished as host.
* Briefly browse around [FiveThirtyEight's GitHub data page](https://github.com/fivethirtyeight/data). What are some other datasets available that you find interesting? You can scroll to the bottom of the page to get to the compiled README.md content, which gives the full titles and links to relevant datasets. You can also click on any dataset to get more information. 
* Look at [the GitHub page for this *Daily Show* data](https://github.com/fivethirtyeight/data/tree/master/daily-show-guests). How many columns will be in this dataset? What kind of information does the data include?

If you have extra time:

* Check out [the related article](http://fivethirtyeight.com/datalab/every-guest-jon-stewart-ever-had-on-the-daily-show/) on FiveThirtyEight. What are some specific questions they used this data to answer for this article?
* Who is Nate Silver?

# Getting the data onto your computer

First, download the data from GitHub onto your computer. Put it in your directory (folder) for this course. 

**Take the following steps to get the data onto your computer**

* If you do not yet have a directory (folder) just for this course, make one someplace straightforward like in your home directory.
* Download the file [from GitHub](https://github.com/geanders/RCourseFall2015/blob/master/Week1_Aug24/daily_show_guests.csv). Right click on `Raw` and then choose "Download linked file". Put the file into the directory you created for this course. 
* Find out what your home directory is in R. To do this, make sure R is set to your home directory using `setwd("~")`, and then get R to print that home directory path using `getwd()`.
* Outside of R, open Finder (or your system's equivalent). Go to your home directory (mine, for example, is `/Users/brookeanderson`). Figure out home to get from this to the directory you created for this course. For example, from my home directory, I would go `Desktop` to `RCourseFall2015` to `Week1_Aug24`. 
* Go back into R. Set R's working directory to your directory for this class using the `setwd()` command, now that you know the pathname for the directory. For example, I would use `setwd("Desktop/RCourseFall2015/Week1_Aug24")`. 
* Use the `list.files()` command to make sure that the `daily_show_guests.csv` file is in your current working directory.

The full R code for this task might look something like:

```r
setwd("~")
getwd()
```

```
## [1] "/Users/brookeanderson"
```

```r
setwd("Desktop/RCourseFall2015/Week1_Aug24")
getwd()
```

```
## [1] "/Users/brookeanderson/Desktop/RCourseFall2015/Week1_Aug24"
```

```r
list.files()
```

```
## [1] "daily_show_guests.csv"        "InCourseExercises_Week1.html"
## [3] "InCourseExercises_Week1.md"   "InCourseExercises_Week1.Rmd"
```

```r
"daily_show_guests.csv" %in% list.files()
```

```
## [1] TRUE
```

If you have extra time:

* See if you can figure out the last line of code in the example R code.

# Getting the data into R

Now that you have the dataset in your working directory, you can read it into R. This dataset is in the CSV (comma separated values) format. (We will talk more about different file formats next week.) You can read csv files into R using the `read.csv()` function. 

**Read the data into your R session**

* Use the `read.csv()` function to read the data into R and save it as the object `daily_show`.
* Use the help file for the `read.csv()` function to figure out how this function works. To pull that up, use `?read.csv`. Why are we using the option `header = TRUE`? Can you figure out why we're using the `skip` option, and why it's set to 4?
* Note that you need to put the file name in quotation marks.
* What would have happened if you'd used `read.csv` but hadn't saved the result as the object `daily_show`? (For example, you'd run the code `read.csv("daily_show_guests.csv")` rather than `daily_show <- read.csv("daily_show_guests.csv")`.)

Example R code:

```r
daily_show <- read.csv("daily_show_guests.csv",
                       header = TRUE,
                       skip = 4)
```

If you have extra time:

* Say this was a really big dataset. You want to check out just the first 10 rows to make sure that you've got your code right before you take the time to pull in the whole dataset. Use the help file for `read.csv()` to figure out how to only read in a few rows. 
* Look through the help file for other options available for `read.csv()`. Can you think of examples when some of these options would be useful?

Example R code:

```r
daily_show_first10 <- read.csv("daily_show_guests.csv",
                       header = TRUE,
                       skip = 4,
                       nrows = 10)
daily_show_first10
```

```
##    YEAR GoogleKnowlege_Occupation    Show    Group   Raw_Guest_List
## 1  1999                     actor 1/11/99   Acting   Michael J. Fox
## 2  1999                  Comedian 1/12/99   Comedy  Sandra Bernhard
## 3  1999        television actress 1/13/99   Acting    Tracey Ullman
## 4  1999              film actress 1/14/99   Acting Gillian Anderson
## 5  1999                     actor 1/18/99   Acting David Alan Grier
## 6  1999                     actor 1/19/99   Acting  William Baldwin
## 7  1999           Singer-lyricist 1/20/99 Musician    Michael Stipe
## 8  1999                     model 1/21/99    Media   Carmen Electra
## 9  1999                     actor 1/25/99   Acting  Matthew Lillard
## 10 1999         stand-up comedian 1/26/99   Comedy      David Cross
```

# Checking out the data

You now have the data available in the `daily_show` option. You'll want to check it out to make sure it read in correctly, and also to get a feel for the data. Throughout, you can use the help pages to figure out more about any of the functions being used (for example, `?dim`).

**Take the following steps to check out the dataset**

* Use indexing to look at the first two rows of the dataset. Based on this, what does each row "measure"? What information do you get for each "measurement"? Indexing uses square brackets immediately after the object name. If the object has two dimensions, like a dataframe (rows and columns), you put the rows you want, then a comma, then the columns you want. If you want all rows (or columns), you leave that space blank. For example, if you wanted to get the first two rows and the first three columns, you'd use `daily_show[1:2, 1:3]`. If you wanted to get the first five rows and all the columns, you'd use `daily_show[1:5, ]`. 
* Use the `dim()` function to find out how many rows and columns this dataframe has. Based on what you found out about the data from the GitHub page, does it have the number of columns you expected? Based on what you know about the data (all the guests who came on The Daily Show with Jon Stewart), do you think it has about the right number of rows?
* Use the `head()` function to look at the first few rows of the dataframe. Does it look like the rows go in order by date? What was the date of Jon Stewart's first show? Does it look like this dataset covers that first show?
* Use the `tail()` function to look at the last few rows of the dataframe. What is the last show date covered by the dataframe? Who was the last guest?

Example R code:

```r
daily_show[1:2, ]
```

```
##   YEAR GoogleKnowlege_Occupation    Show  Group  Raw_Guest_List
## 1 1999                     actor 1/11/99 Acting  Michael J. Fox
## 2 1999                  Comedian 1/12/99 Comedy Sandra Bernhard
```

```r
dim(daily_show)
```

```
## [1] 2693    5
```

```r
head(daily_show)
```

```
##   YEAR GoogleKnowlege_Occupation    Show  Group   Raw_Guest_List
## 1 1999                     actor 1/11/99 Acting   Michael J. Fox
## 2 1999                  Comedian 1/12/99 Comedy  Sandra Bernhard
## 3 1999        television actress 1/13/99 Acting    Tracey Ullman
## 4 1999              film actress 1/14/99 Acting Gillian Anderson
## 5 1999                     actor 1/18/99 Acting David Alan Grier
## 6 1999                     actor 1/19/99 Acting  William Baldwin
```

```r
tail(daily_show)
```

```
##      YEAR GoogleKnowlege_Occupation    Show  Group       Raw_Guest_List
## 2688 2015                     actor 7/28/15 Acting           Tom Cruise
## 2689 2015                biographer 7/29/15  Media Doris Kearns Goodwin
## 2690 2015                  director 7/30/15  Media         J. J. Abrams
## 2691 2015         stand-up comedian  8/3/15 Comedy          Amy Schumer
## 2692 2015                     actor  8/4/15 Acting          Denis Leary
## 2693 2015                  comedian  8/5/15 Comedy           Louis C.K.
```

If you have extra time:

* Say you wanted to look at the first ten rows of the dataframe, rather than the first six. How could you use an option with `head()` to do this?

Example R code:

```r
head(daily_show, n = 10)
```

```
##    YEAR GoogleKnowlege_Occupation    Show    Group   Raw_Guest_List
## 1  1999                     actor 1/11/99   Acting   Michael J. Fox
## 2  1999                  Comedian 1/12/99   Comedy  Sandra Bernhard
## 3  1999        television actress 1/13/99   Acting    Tracey Ullman
## 4  1999              film actress 1/14/99   Acting Gillian Anderson
## 5  1999                     actor 1/18/99   Acting David Alan Grier
## 6  1999                     actor 1/19/99   Acting  William Baldwin
## 7  1999           Singer-lyricist 1/20/99 Musician    Michael Stipe
## 8  1999                     model 1/21/99    Media   Carmen Electra
## 9  1999                     actor 1/25/99   Acting  Matthew Lillard
## 10 1999         stand-up comedian 1/26/99   Comedy      David Cross
```

# Using the data to answer questions

Nate Silver was a guest on *The Daily Show*. Let's use this data to figure out how many times he was a guest and when he was on the show.

**Find out more about Nate Silver on The Daily Show**

* Use the `subset()` function to create a new dataframe that only has the rows of `daily_show` when Nate Silve was a guest. Put it in the object `nate_silver`.
* Print out the full `nate_silver` dataframe by typing `nate_silver`. (You could just use this to answer both questions, but still try the next steps. They would be important with a bigger dataset.)
* To count the number of times Nate Silver was a guest, you'll need to count the number of rows in the new dataset. You can either use the `dim()` function or the `nrow()` function to do this. What additional information does the `dim()` function give you?
* To get the dates when Nate Silver was a guest, you can print out just the `Show` column of the dataframe. There are a few ways you can do this using indexing: `nate_silver[ , 3]` (since `Show` is the third column), `nate_silver[ , "Show"]`, or `nate_silver$Show`. Try these.

Example R code:

```r
nate_silver <- subset(daily_show, 
                      Raw_Guest_List == "Nate Silver")
nate_silver
```

```
##      YEAR GoogleKnowlege_Occupation     Show Group Raw_Guest_List
## 2123 2012              Statistician 10/17/12 Media    Nate Silver
## 2147 2012              Statistician  11/7/12 Media    Nate Silver
## 2509 2014              Statistician  3/27/14 Media    Nate Silver
```

```r
dim(nate_silver)
```

```
## [1] 3 5
```

```r
nrow(nate_silver)
```

```
## [1] 3
```

```r
nate_silver[ , 3]
```

```
## [1] 10/17/12 11/7/12  3/27/14 
## 2639 Levels: 1/1/07 1/1/08 1/10/00 1/10/01 1/10/02 1/10/05 ... 9/9/14
```

```r
nate_silver[ , "Show"]
```

```
## [1] 10/17/12 11/7/12  3/27/14 
## 2639 Levels: 1/1/07 1/1/08 1/10/00 1/10/01 1/10/02 1/10/05 ... 9/9/14
```

If you have extra time:

* When you print out the `Show` column, why does it also print out something underneath about Levels? Hint: This has to do with the class that R has saved this column as. What class is it currently? What other classes might we want to consider converting it to as we continue working with the dataset? Check out the example code below to get some ideas.
* Was Nate Silver the only statistician to be a guest on the show?
* What were the occupations that were only represented by one guest visit? Since `GoogleKnowlege_Occupation` is a factor, you can use the `table()` function to create a new vector with the number of times each value of `GoogleKnowlege_Occupation` shows up. You can put this information into a new vector and then pull out only the values that equal 1 (so, only had one guest). (Note that "Statistician" doesn't show up-- there was only one person who was a guest, but he had three visits.) Pick your favorite "one-off" example and find out who the guest was for that occupation.

Example R code:

```r
class(nate_silver$Show)
```

```
## [1] "factor"
```

```r
range(nate_silver$Show)
```

```r
nate_silver$Show <- as.Date(nate_silver$Show,
                            format = "%m/%d/%y")
range(nate_silver$Show)
```

```
## [1] "2012-10-17" "2014-03-27"
```

```r
diff(range(nate_silver$Show)) # Time between Nate's first and last shows
```

```
## Time difference of 526 days
```

```r
statisticians <- subset(daily_show,
                        GoogleKnowlege_Occupation == "Statistician")
statisticians
```

```
##      YEAR GoogleKnowlege_Occupation     Show Group Raw_Guest_List
## 2123 2012              Statistician 10/17/12 Media    Nate Silver
## 2147 2012              Statistician  11/7/12 Media    Nate Silver
## 2509 2014              Statistician  3/27/14 Media    Nate Silver
```

```r
num_visits <- table(daily_show[ , 2])
head(num_visits) # Note: This is a vector rather than a dataframe
```

```
## 
##          -          0   academic   Academic accountant   activist 
##          1          4          3          3          1         14
```

```r
names(num_visits[num_visits == 1])
```

```
##   [1] "-"                                                          
##   [2] "accountant"                                                 
##   [3] "administrator"                                              
##   [4] "advocate"                                                   
##   [5] "aei president"                                              
##   [6] "afghan politician"                                          
##   [7] "American football running back"                             
##   [8] "american football wide reciever"                            
##   [9] "assistant secretary of defense"                             
##  [10] "assistant to the president for communications"              
##  [11] "Associate Justice of the Supreme Court of the United States"
##  [12] "astronaut"                                                  
##  [13] "Astronaut"                                                  
##  [14] "Attorney at law"                                            
##  [15] "author of novels"                                           
##  [16] "aviator"                                                    
##  [17] "Baseball athlete"                                           
##  [18] "baseball player"                                            
##  [19] "Basketball Coach"                                           
##  [20] "bass guitarist"                                             
##  [21] "bassist"                                                    
##  [22] "Beach Volleyball Player"                                    
##  [23] "boxer"                                                      
##  [24] "business person"                                            
##  [25] "businesswoman"                                              
##  [26] "Businesswoman"                                              
##  [27] "Cartoonist"                                                 
##  [28] "celbrity chef"                                              
##  [29] "CHARACTER"                                                  
##  [30] "chess player"                                               
##  [31] "chief technology officer of united states"                  
##  [32] "Choreographer"                                              
##  [33] "civil rights activist"                                      
##  [34] "Coach"                                                      
##  [35] "comic"                                                      
##  [36] "Comic"                                                      
##  [37] "communications consultant"                                  
##  [38] "Composer"                                                   
##  [39] "comptroller of the us"                                      
##  [40] "coorespondant"                                              
##  [41] "Critic"                                                     
##  [42] "designer"                                                   
##  [43] "Director of the Consumer Financial Protection Bureau"       
##  [44] "doctor"                                                     
##  [45] "drummer"                                                    
##  [46] "Educator"                                                   
##  [47] "entrepreneur"                                               
##  [48] "Ethologist"                                                 
##  [49] "executive"                                                  
##  [50] "Executive"                                                  
##  [51] "fbi agent"                                                  
##  [52] "Fiction writer"                                             
##  [53] "Film critic"                                                
##  [54] "film producer"                                              
##  [55] "Film-maker"                                                 
##  [56] "Financier"                                                  
##  [57] "first lady"                                                 
##  [58] "first lady of egypt"                                        
##  [59] "First Lady of the United States"                            
##  [60] "First Minister of Scotland"                                 
##  [61] "Football coach"                                             
##  [62] "football player"                                            
##  [63] "foreign policy analyst"                                     
##  [64] "foreign policy expert"                                      
##  [65] "foreign policy strategist"                                  
##  [66] "Former American senator"                                    
##  [67] "former british prime minister"                              
##  [68] "former cia director"                                        
##  [69] "former director of the national economic counscil"          
##  [70] "Former Director of the Office of Management and Budget"     
##  [71] "Former First Lady of the United States"                     
##  [72] "former governor of arizona"                                 
##  [73] "former governor of arkansas"                                
##  [74] "former governor of california"                              
##  [75] "Former Governor of Indiana"                                 
##  [76] "former governor of louisiana"                               
##  [77] "former governor of massachusetts"                           
##  [78] "former governor of michigan"                                
##  [79] "former governor of missouri"                                
##  [80] "former governor of montans"                                 
##  [81] "former governor of new hampshire"                           
##  [82] "Former Governor of New Jersey"                              
##  [83] "Former Governor of New York"                                
##  [84] "former governor of rhode island"                            
##  [85] "Former Governor of Texas"                                   
##  [86] "former governor of washington"                              
##  [87] "former govrnor of masssachusetts"                           
##  [88] "Former Mayor of Cincinnati"                                 
##  [89] "Former Mayor of New Orleans"                                
##  [90] "former mayor of san antonio"                                
##  [91] "Former member of the United States Senate"                  
##  [92] "former mjority leader"                                      
##  [93] "former national security advisio\\r"                        
##  [94] "former omb director"                                        
##  [95] "Former President of Mexico"                                 
##  [96] "Former President of the Maldives"                           
##  [97] "former press secretary"                                     
##  [98] "former secretary of defense"                                
##  [99] "former senator"                                             
## [100] "former senator from kansas"                                 
## [101] "Former United States Deputy Secretary of State"             
## [102] "Former United States National Security Advisor"             
## [103] "Former United States Secretary of Education"                
## [104] "Former United States Secretary of Energy"                   
## [105] "Former United States Secretary of the Interior"             
## [106] "Former United States Secretary of the Treasury"             
## [107] "Former United States Secretary of Transportation"           
## [108] "former us representativ"                                    
## [109] "former us secretary of education"                           
## [110] "former white house counsel"                                 
## [111] "Futurist"                                                   
## [112] "game show host"                                             
## [113] "Geneticist"                                                 
## [114] "governor of new jersey"                                     
## [115] "guitarist"                                                  
## [116] "high-altitude mountaineer"                                  
## [117] "Host"                                                       
## [118] "Ice hockey coach"                                           
## [119] "illustrator"                                                
## [120] "Innovator"                                                  
## [121] "inspector general of homeland security department"          
## [122] "intellectual"                                               
## [123] "internet entrepreneur"                                      
## [124] "investment banker"                                          
## [125] "israeli official"                                           
## [126] "JOURNALIST"                                                 
## [127] "Law professor"                                              
## [128] "legal scholar"                                              
## [129] "magician"                                                   
## [130] "mathematician"                                              
## [131] "Mayor of Chicago"                                           
## [132] "mayor of london"                                            
## [133] "Media person"                                               
## [134] "minister of defense"                                        
## [135] "Music Producer"                                             
## [136] "Neurologist"                                                
## [137] "Neuroscientist"                                             
## [138] "non profit director"                                        
## [139] "non profit worker"                                          
## [140] "orca trainer"                                               
## [141] "pastor"                                                     
## [142] "peace activist"                                             
## [143] "photojournalist"                                            
## [144] "Photojournalist"                                            
## [145] "physicist"                                                  
## [146] "pianist"                                                    
## [147] "police officer"                                             
## [148] "political consultant"                                       
## [149] "political expert"                                           
## [150] "Political figure"                                           
## [151] "political psychologist"                                     
## [152] "political satirist"                                         
## [153] "political strategist"                                       
## [154] "Pop group"                                                  
## [155] "president of liberia"                                       
## [156] "priest"                                                     
## [157] "prince"                                                     
## [158] "Product line"                                               
## [159] "professional wrestler"                                      
## [160] "psychic"                                                    
## [161] "Psychologist"                                               
## [162] "public official"                                            
## [163] "public speaker"                                             
## [164] "publisher"                                                  
## [165] "Pundit"                                                     
## [166] "Puppeteer"                                                  
## [167] "Puzzle Creator"                                             
## [168] "race car driver"                                            
## [169] "Racing driver"                                              
## [170] "reality show contestant"                                    
## [171] "RNC chairman"                                               
## [172] "Scholar"                                                    
## [173] "secretary of state"                                         
## [174] "security expert"                                            
## [175] "Soccer player"                                              
## [176] "social activist"                                            
## [177] "speechwriter"                                               
## [178] "Sports Columnist"                                           
## [179] "Surgeon"                                                    
## [180] "swimmer"                                                    
## [181] "syrian politician"                                          
## [182] "television actor"                                           
## [183] "television Director"                                        
## [184] "television writer"                                          
## [185] "televison actor"                                            
## [186] "telvision actor"                                            
## [187] "telvision personality"                                      
## [188] "Tennis player"                                              
## [189] "Track and field athlete"                                    
## [190] "TV Producer"                                                
## [191] "united nations official"                                    
## [192] "United States Secretary of Agriculture"                     
## [193] "United States Secretary of Defense"                         
## [194] "United States Secretary of Housing and Urban Development"   
## [195] "United States Secretary of the Navy"                        
## [196] "us assistant attorney"                                      
## [197] "us official"                                                
## [198] "us permanent representative to nato"                        
## [199] "us secetary of education"                                   
## [200] "us secretary of defense"                                    
## [201] "us secretary of energy"                                     
## [202] "white house official"
```

```r
subset(daily_show, GoogleKnowlege_Occupation == "chess player")
```

```
##      YEAR GoogleKnowlege_Occupation    Show Group
## 2149 2012              chess player 11/8/12  Misc
##                            Raw_Guest_List
## 2149 Katie Dellamaggiore and Pobo Efekoro
```

```r
subset(daily_show, GoogleKnowlege_Occupation == "mathematician")
```

```
##      YEAR GoogleKnowlege_Occupation    Show    Group
## 1131 2005             mathematician 9/14/05 Academic
##              Raw_Guest_List
## 1131 Dr. William A. Dembski
```

```r
subset(daily_show, GoogleKnowlege_Occupation == "orca trainer")
```

```
##      YEAR GoogleKnowlege_Occupation    Show     Group Raw_Guest_List
## 2631 2015              orca trainer 3/26/15 Athletics  John Hargrove
```

```r
subset(daily_show, GoogleKnowlege_Occupation == "Puzzle Creator")
```

```
##     YEAR GoogleKnowlege_Occupation    Show Group Raw_Guest_List
## 798 2003            Puzzle Creator 8/20/03 Media    Will Shortz
```

```r
subset(daily_show, GoogleKnowlege_Occupation == "Scholar")
```

```
##      YEAR GoogleKnowlege_Occupation    Show    Group Raw_Guest_List
## 1085 2005                   Scholar 6/13/05 Academic  Larry Diamond
```
