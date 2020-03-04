Data Preparation - Assignment 1
================

### A Comprehesive Data Exploration and Analysis on CSV and JSON files:

The Open Data 500 is the first comprehensive study of U.S. companies
that use open government data to generate new business and develop new
products and services. Open Data is free, public data that can be used
to launch commercial and nonprofit ventures, conduct research, make
data-driven decisions, and solve complex problems

In this assignment you will be analyzing two datasets - US\_agency.csv
and US\_companies.csv. You can download the data from the website:
<https://www.opendata500.com/>

  - Libraries used : 3
      - dplyr
      - tidyverse
      - jsonlite

Loading the dataset :

``` r
us_ag <- read_csv("us_agencies.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   agency_name = col_character(),
    ##   agency_abbrev = col_character(),
    ##   agency_type = col_character(),
    ##   subagency_name = col_character(),
    ##   subagency_abbrev = col_character(),
    ##   url = col_character(),
    ##   used_by = col_character(),
    ##   used_by_category = col_character(),
    ##   used_by_fte = col_character(),
    ##   dataset_name = col_character(),
    ##   dataset_url = col_character()
    ## )

``` r
str(us_ag)
```

    ## Classes 'spec_tbl_df', 'tbl_df', 'tbl' and 'data.frame': 1123 obs. of  11 variables:
    ##  $ agency_name     : chr  "U.S. House of Representatives" "Arkansas" "Atlanta" "Austin" ...
    ##  $ agency_abbrev   : chr  NA "AR" "ATL" "AUS" ...
    ##  $ agency_type     : chr  "Federal Open Data" "State" "City/County" "City/County" ...
    ##  $ subagency_name  : chr  "General" "General" "General" "General" ...
    ##  $ subagency_abbrev: chr  NA NA NA NA ...
    ##  $ url             : chr  NA "http://catalog.data.gov/organization/arkansas-gov" "http://gis.atlantaga.gov/" "http://data.austintexas.gov/" ...
    ##  $ used_by         : chr  "Civic Impulse LLC" "Pave" "YourMapper" "Code for America" ...
    ##  $ used_by_category: chr  "Governance" "Finance & Investment" "Geospatial/Mapping" "Governance" ...
    ##  $ used_by_fte     : chr  "1-10" "1-10" "1-10" "51-200" ...
    ##  $ dataset_name    : chr  "Upcoming bills in the House" "Post-Completion Wages of Graduates" "Crime" NA ...
    ##  $ dataset_url     : chr  "http://docs.house.gov/" NA NA NA ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   agency_name = col_character(),
    ##   ..   agency_abbrev = col_character(),
    ##   ..   agency_type = col_character(),
    ##   ..   subagency_name = col_character(),
    ##   ..   subagency_abbrev = col_character(),
    ##   ..   url = col_character(),
    ##   ..   used_by = col_character(),
    ##   ..   used_by_category = col_character(),
    ##   ..   used_by_fte = col_character(),
    ##   ..   dataset_name = col_character(),
    ##   ..   dataset_url = col_character()
    ##   .. )

``` r
us_co<- read_csv("us_companies.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_character(),
    ##   year_founded = col_double(),
    ##   last_updated = col_datetime(format = "")
    ## )

    ## See spec(...) for full column specifications.

``` r
str(us_co)
```

    ## Classes 'spec_tbl_df', 'tbl_df', 'tbl' and 'data.frame': 529 obs. of  22 variables:
    ##  $ company_name_id    : chr  "3-round-stones-inc" "48-factoring-inc" "5psolutions" "abt-associates" ...
    ##  $ company_name       : chr  "3 Round Stones, Inc." "48 Factoring Inc." "5PSolutions" "Abt Associates" ...
    ##  $ url                : chr  "http://3RoundStones.com" "https://www.48factoring.com" "www.5psolutions.com" "abtassoc.com" ...
    ##  $ year_founded       : num  2010 2014 2007 1965 1999 ...
    ##  $ city               : chr  "Washington" "Philadelphia" "Fairfax" "Cambridge" ...
    ##  $ state              : chr  "DC" "PA" "VA" "MA" ...
    ##  $ country            : chr  "us" "us" "us" "us" ...
    ##  $ zip_code           : chr  "20004" "19087" "22003" "02138" ...
    ##  $ full_time_employees: chr  "1-10" "51-200" "1-10" "1,001-5,000" ...
    ##  $ company_type       : chr  "Private" "Private" "Private" "Private" ...
    ##  $ company_category   : chr  "Data/Technology" "Finance & Investment" "Data/Technology" "Research & Consulting" ...
    ##  $ revenue_source     : chr  "Data analysis for clients, Database licensing, Subscriptions" "Financial Services" "Subscriptions, User fees for web or mobile access" "Data analysis for clients, Database licensing" ...
    ##  $ business_model     : chr  "Business to Business, Business to Consumer" "Business to Business" "Business to Business, Business to Consumer, Business to Government" NA ...
    ##  $ social_impact      : chr  NA "Small Business Owners" NA NA ...
    ##  $ description        : chr  "3 Round Stones produces a platform for publishing data on the Web. 3 Round Stones provides commercial support f"| __truncated__ "The company mission is to provide finance to small business. We also provide financing to small business with b"| __truncated__ "At 5PSolutions, we wish to make all basic information of different categories easily available to via tablets or phones." "Abt Associates is a mission-driven, international company conducting research and program implementation in the"| __truncated__ ...
    ##  $ description_short  : chr  "Our Open Source platform is used by the Fortune2000 and US Government Agencies to collect, publish and reuse da"| __truncated__ "48 Factoring Inc. is one of the best financial services company using unique factoring 2.0 financial product wh"| __truncated__ "5PSolutions are artisans of mobile platforms." "Abt Associates is a mission-driven, global leader in research and program implementation in the fields of healt"| __truncated__ ...
    ##  $ source_count       : chr  NA "11-50" NA "101+" ...
    ##  $ data_types         : chr  NA "Business" NA NA ...
    ##  $ example_uses       : chr  NA NA NA NA ...
    ##  $ data_impacts       : chr  "[]" "[u'Cost efficiency', u'Job growth', u'Revenue growth']" "[]" "[]" ...
    ##  $ financial_info     : chr  "3 Round Stones is a profitable, self-funded, woman-owned start-up.  Our team has several successful serial entr"| __truncated__ NA NA "Employee-owned company. $552M/year." ...
    ##  $ last_updated       : POSIXct, format: "2014-11-12 14:44:25" "2015-05-18 11:36:39" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   company_name_id = col_character(),
    ##   ..   company_name = col_character(),
    ##   ..   url = col_character(),
    ##   ..   year_founded = col_double(),
    ##   ..   city = col_character(),
    ##   ..   state = col_character(),
    ##   ..   country = col_character(),
    ##   ..   zip_code = col_character(),
    ##   ..   full_time_employees = col_character(),
    ##   ..   company_type = col_character(),
    ##   ..   company_category = col_character(),
    ##   ..   revenue_source = col_character(),
    ##   ..   business_model = col_character(),
    ##   ..   social_impact = col_character(),
    ##   ..   description = col_character(),
    ##   ..   description_short = col_character(),
    ##   ..   source_count = col_character(),
    ##   ..   data_types = col_character(),
    ##   ..   example_uses = col_character(),
    ##   ..   data_impacts = col_character(),
    ##   ..   financial_info = col_character(),
    ##   ..   last_updated = col_datetime(format = "")
    ##   .. )

*The load time in reading the dataset using read\_csv of tidyverse
package is faster compared to read.csv. The main advantage of this
function is it parses the file while loading to environment.*

Tasks to explore the dataset and answering the following questions:

**1. Are there any missing columns?**

On a general exploration through data, there is no missing columns.
However if the datasets are related, their should be a primary key.
There is no primary/unique column in us\_agencies dataset which
concludes a missing column.

**2. Are there any missing column names or errors in the column names?
If so, name those columns.**

``` r
colnames(us_ag)
```

    ##  [1] "agency_name"      "agency_abbrev"    "agency_type"      "subagency_name"  
    ##  [5] "subagency_abbrev" "url"              "used_by"          "used_by_category"
    ##  [9] "used_by_fte"      "dataset_name"     "dataset_url"

``` r
colnames(us_co)
```

    ##  [1] "company_name_id"     "company_name"        "url"                
    ##  [4] "year_founded"        "city"                "state"              
    ##  [7] "country"             "zip_code"            "full_time_employees"
    ## [10] "company_type"        "company_category"    "revenue_source"     
    ## [13] "business_model"      "social_impact"       "description"        
    ## [16] "description_short"   "source_count"        "data_types"         
    ## [19] "example_uses"        "data_impacts"        "financial_info"     
    ## [22] "last_updated"

There are no missing columns or errors in the column names. Every column
name carries substantial meaning for understanding to its column values.

**3. Are there any values in the columns missing?**

``` r
#total no of missing values and missing values in each column
sum(is.na(us_ag))
```

    ## [1] 2718

``` r
sapply(us_ag, function(x) sum(is.na(x)))  # In us_agencies
```

    ##      agency_name    agency_abbrev      agency_type   subagency_name 
    ##                0              313                0                0 
    ## subagency_abbrev              url          used_by used_by_category 
    ##              709              292                0                4 
    ##      used_by_fte     dataset_name      dataset_url 
    ##               44              548              808

``` r
sum(is.na(us_co))
```

    ## [1] 2315

``` r
sapply(us_co, function(x) sum(is.na(x)))  # In us_companies
```

    ##     company_name_id        company_name                 url        year_founded 
    ##                   0                   0                   0                   1 
    ##                city               state             country            zip_code 
    ##                  33                   0                   0                  37 
    ## full_time_employees        company_type    company_category      revenue_source 
    ##                  29                  16                   3                  10 
    ##      business_model       social_impact         description   description_short 
    ##                  76                 512                   0                   0 
    ##        source_count          data_types        example_uses        data_impacts 
    ##                 303                 387                 521                   0 
    ##      financial_info        last_updated 
    ##                 387                   0

**YES**, A total of 2718 and 2315 missing values are there in
us\_agencies and us\_companies dataset. we can see the total missing
values in each column. in Us\_agencies, column 5 and column 9 has the
highest number of missing values. In us\_companies, social\_impact,
example\_uses, financial\_info, source\_count has highest number of
missing values.

4.  How is data organized in each column? Is it properly organized?

The data is not organized at various columns of the us\_agencies and
us\_companies. Has too many categorical values and has many
non-significant columns.

**5. Is data in the proper shape for further analysis? If not, why?
Explain.**

Though the data is structured, It still needs to a lot of pre-processing
for any analysis. The data is not in proper shape and has a lot of
missing values.

  - In Us\_companies,
      - Column last\_updated needs to be parsed.
      - Financial\_info column has aa lot of unwanted tags and
        characters
      - data\_impacts column is not organized and has unreadable
        characters
      - Coulmns source\_count & full\_time\_employees has values with
        incorrectly feeded data and needs to be parsed
      - A lot of missing values in columns
  - In us\_agencies,
      - used\_by\_fte column needs to be parsed.

**6. How will you fix this dataset? Describe the methods you will use to
fix this dataset for further analysis? It can be missing values, NAs,
etc. (OPTIONAL: Uploading clean dataset)**

  - Any dataset with too many missing values will not give any
    significant/Actionable insights. Usually a safe maximum threshold is
    5% missing values, NA’s of the total in each column is followed for
    further any analysis on the datasets.
  - We need to make sure there are no duplicates in the dataset.

<!-- end list -->

``` r
#Dataframe without Duplicates
us_ag_noDup<-us_ag %>% distinct()
us_co_noDup<-us_co %>% distinct()
```

  - If missing data for a certain feature or sample is more than 5% then
    we probably should leave that feature or sample out. We therefore
    check for features (columns) and samples (rows) where more than 5%
    of the data is missing using a simple function

<!-- end list -->

``` r
#Percentage of missing values at each column
us_ag_NoMissing <- function(x){sum(is.na(x))/length(x)*100}
apply(us_ag_noDup,2,us_ag_NoMissing)
```

    ##      agency_name    agency_abbrev      agency_type   subagency_name 
    ##        0.0000000       27.5089606        0.0000000        0.0000000 
    ## subagency_abbrev              url          used_by used_by_category 
    ##       62.9928315       25.6272401        0.0000000        0.3584229 
    ##      used_by_fte     dataset_name      dataset_url 
    ##        3.4946237       49.1039427       72.3118280

``` r
us_co_NoMissing <- function(x){sum(is.na(x))/length(x)*100}
apply(us_co_noDup,2,us_co_NoMissing)
```

    ##     company_name_id        company_name                 url        year_founded 
    ##           0.0000000           0.0000000           0.0000000           0.1890359 
    ##                city               state             country            zip_code 
    ##           6.2381853           0.0000000           0.0000000           6.9943289 
    ## full_time_employees        company_type    company_category      revenue_source 
    ##           5.4820416           3.0245747           0.5671078           1.8903592 
    ##      business_model       social_impact         description   description_short 
    ##          14.3667297          96.7863894           0.0000000           0.0000000 
    ##        source_count          data_types        example_uses        data_impacts 
    ##          57.2778828          73.1568998          98.4877127           0.0000000 
    ##      financial_info        last_updated 
    ##          73.1568998           0.0000000

As we can see, there are lot of columns with missing values more than 5%

  - There are alot of packages/libraries that deals with the imputation
    of missing values. One can also follow the conventional ways of
    imputation without using packages/libraries for numerical variables.
  - For mising values, five powerful R packages namely
      - MICE
      - Amelia
      - missForest
      - Hmisc
      - mi

*source:
<https://www.analyticsvidhya.com/blog/2016/03/tutorial-powerful-packages-imputing-missing-values/>*

**7. How are the two datasets linked to each other? Is there a common
“primary key” to connect the two datasets?**

As mentioned earlier, There is no Unique row identifier to access the
data to perform furtherr analysis using these two datasets.

## Exercise 2:

JSON (JavaScript Object Notation) is a most commonly used data format
today and as a data scientist, you must know how to access JSON data
sets. JSON is easy for machines to parse and generate. “It is based on a
subset of the JavaScript Programming Language Standard ECMA-262 3rd
Edition - December 1999. JSON is a text format that is completely
language independent \[JSON.ORG\].”

For this case study, you will parse JSON file, which has city traffic
details. “Average Daily Traffic (ADT)” counts are analogous to a census
count of vehicles on city streets. These counts provide a close
approximation to the actual number of vehicles passing through a given
location on an average weekday. Since it is not possible to count every
vehicle on every city street, sample counts are taken along larger
streets to get an estimate of traffic on half-mile or one-mile street
segments. ADT counts are used by city planners, transportation
engineers, real-estate developers, marketers and many others for myriad
planning and operational purposes. Data Owner: Transportation. Time
Period: 2006. Frequency: A citywide count is taken approximately every
10 years. A limited number of traffic counts will be taken and added to
the list periodically \[<https://catalog.data.gov/>\]”

**1.How many variables are in the dataset?**

``` r
# Convert JSON file to a data frame.
ChigoTraffic <- fromJSON("ChicagoTraffic.json")
# prints Total variables
print(nrow(ChigoTraffic$meta$view$columns))
```

    ## [1] 23

We have a total of 23 variables in the metadata that concerns with the
listed data in json file

**2. Name all the variables?**

``` r
# Prints Column names
print(ChigoTraffic$meta$view$columns$name)
```

    ##  [1] "sid"                                        
    ##  [2] "id"                                         
    ##  [3] "position"                                   
    ##  [4] "created_at"                                 
    ##  [5] "created_meta"                               
    ##  [6] "updated_at"                                 
    ##  [7] "updated_meta"                               
    ##  [8] "meta"                                       
    ##  [9] "ID "                                        
    ## [10] "Traffic Volume Count Location  Address"     
    ## [11] "Street"                                     
    ## [12] "Date of Count"                              
    ## [13] "Total Passing Vehicle Volume"               
    ## [14] "Vehicle Volume By Each Direction of Traffic"
    ## [15] "Latitude"                                   
    ## [16] "Longitude"                                  
    ## [17] "Location"                                   
    ## [18] "Boundaries - ZIP Codes"                     
    ## [19] "Community Areas"                            
    ## [20] "Zip Codes"                                  
    ## [21] "Census Tracts"                              
    ## [22] "Wards"                                      
    ## [23] ":@computed_region_awaf_s7ux"

**3. What is the total traffic of vehicles on 100th street to 115th
street?**

``` r
# Storing Data values to a variable
CT_data<-ChigoTraffic$data
# The total traffic of vehicles on 100th street to 115th street?
for(i in 1:1279){
  if(CT_data[[i]][[11]] == "100th St"){
    print(as.numeric(CT_data[[i]][[13]]))
  }
  if(CT_data[[i]][[11]] == "101th St"){
    print(as.numeric(CT_data[[i]][[13]]))
  }
  if(CT_data[[i]][[11]] == "102th St"){
    print(as.numeric(CT_data[[i]][[13]]))
  }
  if(CT_data[[i]][[11]] == "103th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "104th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "105th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "106th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
   if(CT_data[[i]][[11]] == "107th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "108th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "109th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "110th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "111th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "112th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "113th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "114th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
  if(CT_data[[i]][[11]] == "115th St"){
    print(as.numeric(CT_data[[i]][[13]]))
    }
}
```

    ## [1] 8200
    ## [1] 22600
    ## [1] 8000
    ## [1] 6300
    ## [1] 9100
    ## [1] 11000
    ## [1] 12800
    ## [1] 11700
    ## [1] 15500
    ## [1] 7900
    ## [1] 12600
    ## [1] 12200
    ## [1] 16500
    ## [1] 10900
    ## [1] 16500
    ## [1] 19800
    ## [1] 6300
    ## [1] 800
    ## [1] 12200
    ## [1] 20200
    ## [1] 29800
    ## [1] 7700
    ## [1] 12800

As we can see the traffic volume at each street in the output. The total
volume of traffic between 100th Street and 115th Street is **264,000**

**4. What is the total traffic of vehicles on geolocations, (41.651861,
-87.54501) and (41.66836, -87.620176)**

``` r
for(j in 1:1279){
  if(CT_data[[j]][[15]]=="41.651861" && CT_data[[j]][[16]]== "-87.54501"){t1<-as.numeric(CT_data[[j]][[13]])}
  if(CT_data[[j]][[15]]=="41.66836" && CT_data[[j]][[16]]== "-87.620176"){t2<-as.numeric(CT_data[[j]][[13]])}
}
Total_Traffic=t1+t2
print(Total_Traffic)
```

    ## [1] 13600

The Total traffic on the given geolocations is 13600.
