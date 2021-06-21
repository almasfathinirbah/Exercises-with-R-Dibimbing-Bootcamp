# Data Cleansing With R

We will show you how to cleanse the dataset. __Why do we need to cleanse the dataset?__ Because the dirty dataset will be difficult to be analyzed and report the insight. 
![why](https://user-images.githubusercontent.com/85482667/122724266-f6f6cd00-d29d-11eb-9efa-d3713207ee3a.PNG)

The source of the dataset we will use for this case is Airbnb price. 

## Load Library
Load the necessary packages, like readr library, assertive library, and dplyr library. 
````
library(readr)
library(assertive)
library(dplyr)
````

## Importing
Import airbnb_price.csv to a new variable.
````
(airbnb_price <- read_csv('airbnb_price.csv'))
````
![import](https://user-images.githubusercontent.com/85482667/122723549-4be61380-d29d-11eb-9976-607384b6f14d.PNG)


## Checking
In this case, we will cleanse the prices column to the numeric type. We need to check the data type of that column before we will cleanse it.
````
assert_is_numeric(airbnb_price$price)
````
![Checking](https://user-images.githubusercontent.com/85482667/122723913-a97a6000-d29d-11eb-9e43-30283a8d94f2.PNG)

## Converting
Firstly, we need to load stringr library to use str_remove function. We will remove " dollars" in the prices column.
````
library(stringr)
price_trimmed = str_remove(airbnb_price$price, " dollars")
price_trimmed
````
![converting 1](https://user-images.githubusercontent.com/85482667/122724020-c0b94d80-d29d-11eb-9c61-8f1edf35e315.PNG)

Then, we will to converting the character type of the prices column to the numeric type by using as.numeric function.
````
prices_in_dollar <- as.numeric(as.character(price_trimmed))
class(prices_in_dollar)
````
![converting 2](https://user-images.githubusercontent.com/85482667/122724110-d3338700-d29d-11eb-8cfc-e6ae6a780948.PNG)

## The Result
Adding prices as numeric to the Airbnb prices table.
````
airbnb_price %>% 
  select(-price) %>% 
  mutate(prices_in_dollar)
````
![result](https://user-images.githubusercontent.com/85482667/122724183-e47c9380-d29d-11eb-8b44-b3839b6cff81.PNG)

## Summary
In this case, we used Airbnb price as the dataset we will cleanse. We need the important libraries to diagnose the data type and stringr library to remove the character we want to. Finally, we have the clean data to be analyzed.
