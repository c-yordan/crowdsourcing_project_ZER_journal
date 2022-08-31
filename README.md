# Crowdsourcing Journalism Project

This repository includes several datasets used in the following article.

## Title:

"The ‘Wisdom of The Crowds’ and Their Knowledge of Puerto Rico’s Challenges Six Months After Hurricane Maria: Thoughts on David Begnaud’s Experiment on Journalism Crowdsourcing," ZER: Revista de Estudios de Comunicacion (November 2022).

## Abstract: 

This article analyzes CBS News Correspondent David Begnaud’s experiment with journalism crowdsourcing for his reporting on Puerto Rico’s challenges six months after Hurricane María. It answers two interrelated research questions. First, it examines why journalists and media organizations have experimented with crowdsourcing strategies, using Begnaud’s experiment as a case study. Second, using text-as-data methodologies, the article tests the collective intelligence of the people who responded to Begnaud’s request for information. Based on this investigation’s findings, the article shows that followers’ collective knowledge properly estimated Puerto Rico’s many challenges and some of the municipalities most affected by the storm. Even though crowdsourcing journalism is challenging, this article demonstrates that it can enhance the journalistic process. 

## Keywords:

Crowdsourcing, Journalism, Collective Intelligence, Hurricane María, Text as Data, Puerto Rico

## Datasets:

### dbegnaud_fb_comments_pr6months.csv

This dataset includes Facebook users' comments to Begnuad's "open call" for information for his reporting of Puerto Rico's challenges six months after Hurricane Maria made landfall. It includes 2657 comments and it is divided into seven columns.

- **text**: This variable stores the text of the comments to Begnaud's original post.
- **date**: The date the comments were uploaded.
- **lang**: The language of the comments found in the text column.
- **link**: These a dummy variable, where 0 means that the comment did not include an URL and 1 that the comment included an URL.
- **likes_count**: This variable measures the number of likes each comment received.
- **comments_count**: This variable measures the number of comments generated by each comment.
- **word_count**: This variable measures the number of words in each comment.

Using *quanteda*, an R pacakge for text analysis, the comments were used to create the worldcloud in Figure 6, Table 2's top words and Figure 7's Feature Co-Occurrence Matrix.

### usace_estimates_municipality_with_electricity_march_1_2018.csv

This dataset includes estimates produced by the US Army Corps of Engineers (USACE) and Puerto Rico Electric Power Authority (PREPA) on how many customers had electricity on March 1, 2018. It also includes other variables used to produce many of the infographics used in the article. The dataset includes seven columns.

- **municipality**: This column lists the names of Puerto Rico's 78 municipalities.
- **aee_region**: PREPA or the Autoridad de Energia Electrica (AEE) divides Puerto Rico's municipalities into seven administrative regions.
- **percent_customers_with_electricity**: The estimated percentage of customers with electricity per municipality on March 1, 2018.
- **percent_customers_with_electricity_region**: The estimated percentage of customers with electricity per AEE region on March 1, 2018.
- **mentions_electricity_corpus**: The number of times the municipality is mentioned in the "Electriticy Corpus". This corpus was created using the Facebook comments included in the CSV file in this respository.
- **percent_customers_no_electricity**: The estimated number of customers without electricity per municipality on March 1, 2018.
- **pecent_of_total_mentions**: The percent of mentions from the total number of references to each municipality in the "Electricity Corpus".

This dataset was used to create Figure 1, Figure 4,Table 3 and Figure 8. 

### usace_estimates_region_with_electricity_2018.csv

As noted above, PREPA (or the AEE) divides Puerto Rico's municipalities into seven administrative regions. In early 2018, the USACE started to publicly share the number of customers with electricity per region. The data was extrapolated from the [US Department of Energy's Situation Reports](https://www.energy.gov/ceser/downloads/hurricanes-nate-maria-irma-and-harvey-situation-reports). This dataset includes 9 columns.

- **Date**: The date of the recorded observations.
- **Arecibo**: The number of customers with electricity in the AEE's Arecibo region.
- **Bayamon**: The number of customers with electricity in the AEE's Bayamon region.
- **Caguas**: The number of customers with electricity in the AEE's Caguas region. 
- **Carolina**: The number of customers with electricity in the AEE's Carolina region.
- **Ponce**: The number of customers with electricity in the AEE's Ponce region.
- **Mayaguez**: The number of customers with electricity in the AEE's Mayaguez region.
- **San_Juan**: The number of customers with electricity in the AEE's San Juan region.
- **Average**: The average number of customers with electricity in Puerto Rico.

This dataset was used to create Figures 2 and 3.

### Data tracking Hurricane Maria's path over Puerto Rico

<!-- wp:paragraph -->
<p>Data on Hurricane Maria and other tropical storms in the Atlantic can be found in the National Hurricane Center's <a href="https://www.nhc.noaa.gov/data/#marine" data-type="URL" data-id="https://www.nhc.noaa.gov/data/#marine">Best Track Data</a> also known HURDAT2. This dataset includes spatial data tracking the location of the storm, maximum winds, central pressure, and so forth for all Atlantic hurricanes starting in 1851 and ending in 2021. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I downloaded this dataset into my working directory and uploaded it into <strong>R</strong> using the <strong>readr</strong> package. I then subsetted the dataset for entries connected to Hurricane Maria. Each hurricane has its own unique identifier and after some exploring, I realized that Maria's "key" was AL152017, representing the 15th tropical storm of the 2017 Atlantic hurricane season.</p>
<!-- /wp:paragraph -->

I used *ggplot2* to create the map of Puerto Rico, using spatial data from the US Census Bureau accessed via the *tigris* pacakge for R. For an explanation on how I produced this map, please visit the following [website](https://worldpoliticsdatalab.org/resources/how-to-create-maps-in-r-with-the-ggplot2-package-part-2/).

