# Homework Activities

## General instructions

For all activities you are expected to produce html/pdf files with the discussed answers and the relevant code. You need to generate a markdown document and use `knitr` to generate the html file with your answer. Create one html file for each weekly submission. [This video](https://www.youtube.com/watch?v=-apyD5f9nwg) explains how to do this. The video uses an earlier version of `rmarkdown`, so you will notice that when you create a new markdown file instead a dialogue box open (select html) and you won't see in the working directory any reference to a .md file. Everything else pretty much remains the same. In any case, you can find further details about `rmarkdown` [here](http://rmarkdown.rstudio.com/) or in this [very detailed tutorial](http://galahad.well.ox.ac.uk/repro/?utm_content=bufferc4efb&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer). [This guide](http://stat545-ubc.github.io/block007_first-use-rmarkdown.html#troubleshooting), produced for a different course unit, helps you to test drive and troubleshoot common problems. Although it may take you a while to get used to produce your homework in this way, in the long run you will see the benefits.

Then you need to upload the file to Turnit In through Blackboard.

##Week 1: Basic Data Exploration and Filtering

###Part 1:
Create a data frame with the points achieved by all the Premiership teams in the 2014-2015 season. You can find the relevant information [here](https://en.wikipedia.org/wiki/2014%E2%80%9315_Premier_League). 

  1) What was the mean value of points for all the teams? 

  2) Using the filtering methods described compute the mean (and standard deviation) for the 4 top teams and compare it with the mean (and the standard deviation) of the remainder teams. 

###Part 2:
Load the [classic](https://en.wikipedia.org/wiki/Andr%C3%A9-Michel_Guerry) `Guerry` data available from the `Guerry` package.

1) How many variables and cases does this dataset have? Tip: `dim()`
2) What are the names of the variables? Tip: `names()`
3) What does the variable `Prostitutes` measures? Tip: `help()`
4) Produce a simple histogram of the `Crime_pers` variable. Any discernible patterns? *Discuss*.
5) Produce summary statistics of the `Crime_pers` variable by `Region`. Any discernible patterns? *Discuss*.

##Week 2: Basic visualisations

Download from the GitHub repository the following dataset `crossnat.csv`. You url for the dataset is: https://raw.githubusercontent.com/jjmedinaariza/R-for-Criminologists/master/crossnat.csv

Look at the instructions for how to download files from the web that we provided in Week 1. This comma-separated value file contains a number of variables about 194 countries. I put together this file for teaching purposes in January 2014. The information comes from a variety of sources (World Bank, United Nations, OCDE, etc) and it relates to the more recent year for which data was available then.

Sometimes students experience problems when downloading files within a rmarkdown file. If you are getting stuck you may try an alternative. First get the file in your hard-drive using the console or a script (not rmarkdown):  

1) Download the file into your global environment as covered in week 1; 
2) Save the file into your hard-drive, for example write.csv(crossnat, "crossnat.csv") to save it as .csv in your working directory; 

Then and only then read the data from your working directory into rmarkdown (e.g., using the read.csv function).

Ok, these are the exercises:

1) Display a histogram for the prison rate per 100,000 population (`prisonrate`). Discuss. Try to identify the identify of any outliers and discuss. Are these errors? Are there plausible explanations for the extreme values in these countries? 
2) Produce density estimates and boxplots to compare the prison rate according to various categories of the level of [human development](http://hdr.undp.org/en/content/human-development-index-hdi) per country. Discuss. 
3) Produce a scatterplot with a smoothed line to examine the relationship between `prisonrate` and `gdppercapita`. Discuss. 
4) Produce a scatterplot matrix to examine the relationship between `prisonrate`, `gdppercapita`, `urbanpop` (proportion of the population that lives in urban areas) and `homicide`(homicide per 100,000). Discuss. 

##Week 3

We are going to use a dataset that is often employed in econometric research to investigate methods to estimate causal effects in non experimental scenarios. You need to use the so-called "lalonde" data available with the "arm" package. You will be able to find details about this dataset in the reference articles cited in the Help file. This is a smaller subset of a study that look at the effectiveness of job programs in a number of outcomes. For the exercise you need to: 

1) Visually explore the relationship of treatment with real earnings in 1975 using some of the graphical tools we introduced in week 2. 

2) Use error bars, as descirbed in week 3, to compare the treatment and no treatment group in real earnings in 1975. 

3) Use the t.test function to obtain the confidence intervals for the real earnings in 1975 for each of these two groups. 

4) Use the procedures described in week 3 to estimate the confidence interval of the proportion of individuals with earnings being not zero in 1975 (u75) across the two levels of "treat". 


##Week 4: Contrasting means.

For this exercise you need to download a dataset available in the [UK Data Archive](http://www.data-archive.ac.uk/). The dataset belongs to an old study comparing treatments for juvenile offenders. You can find out more details about it [here](http://discover.ukdataservice.ac.uk/catalogue/?sn=3168&type=Data%20catalogue). Make sure you read the User Guide and the Codebook at the bottom of the page. We are going to try to reproduce the results obtained by the researchers. In order to be able to download data from this repository you have to first register with it. To do so follow the instructions [here](http://ukdataservice.ac.uk/get-data/how-to-access/registration.aspx) and then follow the [instructions for downloading data](http://ukdataservice.ac.uk/get-data/how-to-access/downloadorder.aspx). Why so many loops? This will teach you how to use this most valuable resource. This repository is full of data you can use for your own purposes, including the full version of the Crime Survey of England and Wales. When downloading the file you will be given the choise of different formats. Save the file in .tab delimited format. Then you could adapt the code below to read it into R.


```r
Kingswood <- read.table("g168.tab", sep="\t", header=TRUE)
```

You will need to look at the Codebook to understand the meaning of the variable names and what they are measuring. But know that the `HOUSE` variable identifies the treatment condition. The class 2 corresponds to the comparison group and the class 3 corresponds to the experimental group. Notice however that this is an integer vector, so you will need to redefine it as a factor in order to be able to use it in your tests.

BEWARE: if you do not pay close attention to the codebook there is a very good chance you will get the wrong answers below. Exploring the data beforehand can also help you to identify things you may have to do before running your hypothesis test.

1. Is there a relationship between the experimental treatment and number of court appearances after release? Discuss.

2. Is there a relationship between the experimental treatment and the seriousness score of the first offence after release? Discuss.

3. Consider now whether including the third site in the study (House 1) allows us to see any differences in recidivism using the two outcome measaures used so far. Discuss.

4. Is there a relationship between criminal record of parents and number of court appearances after release? Discuss.

##Week 5: Assessing the relationship across factors

You need to use the data (BCS0708) we have been using so far for illustrations. I want you to examine the relationship that exist: 

-between victimisation and gender, a dichotomous nomimal measure, for which I will expect you to compute the odds ratio 

-between being employed (work) and respondent's understanding of the causes of crime (causem) 

-between victimisation and perceptions around the evolution of crime trends (crimerat) 



Discuss and aim to interpret your findings in a way that is consistent with theory and common sense.

##Week 6: Regression (due 8th December)

###Part 1

For this first exercise we use data made available by StatSci.Org, an Australian organisation that among other things, makes it easy to access teaching datasets. Please download the data from [here](http://www.statsci.org/data/general/uscrime.txt).

Description of the data

Criminologists are interested in the effect of punishment regimes on crime rates. This has been studied using aggregate data on 47 states of the USA for 1960. The data set contains the following columns:
 
  **Variable  	  	Description**
  
	M 		percentage of males aged 14-24 in total state population 
	So 		indicator variable for a southern state 
	Ed 		mean years of schooling of the population aged 25 years or over 
	Po1 		per capita expenditure on police protection in 1960 
	Po2 		per capita expenditure on police protection in 1959 
	LF 		labour force participation rate of civilian urban males in the age-group 14-24 
	M.F 		number of males per 100 females 
	Pop 		state population in 1960 in hundred thousands 
	NW 		percentage of nonwhites in the population 
	U1 		unemployment rate of urban males 14-24 
	U2 		unemployment rate of urban males 35-39 
	Wealth 		wealth: median value of transferable assets or family income 
	Ineq 		income inequality: percentage of families earning below half the median income 
	Prob 		probability of imprisonment: ratio of number of commitments to number of offenses 
	Time 		average time in months served by offenders in state prisons before their first release 
	Crime 		crime rate: number of offenses per 100,000 population in 1960 

Source
Ehrlich, I. (1973) Participation in illegitimate activities: a theoretical and empirical investigation. Journal of Political Economy 81, 521-565.

1.	You need to select 4 different explanatory variables to model crime with this observational dataset. You need to use common sense and technical knowledge in making your selection. 

2.	You need to fit the model, diagnose it, introduce any corrections to it you think are needed, interpret it and discuss it.


###Part 2

Use the BCS0708 dataset.

1.	Select 4 variables as explanatory inputs in a model oriented to predict victimisation. There's a limited choice of variables, so your model won't be great. 

2.	You need to fit the model, diagnose it, introduce any corrections to it you think are needed, interpret it and discuss it.

