# Bring Plant-Based Dining to Franklin 
What drives vegetarian/vegan restaurants to open in certain areas? Do any of these factors play a roll? Education, age/size of population, culture, wealth, other businesses. 

## Motivation
I have been a vegetarian for 13 years and also have a severe dairy allergy. (I think at least briefly pointing out allergens would be beneficial in a business plan.) While I love living in Franklin, TN, there are no vegetarian/vegan specific restaurants here. I have always been an avid traveler, but since March of this year, I am unable to visit veggie friendly cities. I want to look into the areas with high numbers of these restaurants and find out what it would take for one (or more) to open in my own neighborhood. 

## Challenges
After pulling in (and cleaning) 10 or more census datasets, I decided to go with age, household income, and education. These datasets were extremely granular, so I needed to do some calculations in order to get the brackets desired for my analysis. I added together several of the age brackets broken down by male and female. Later, I decided to add these together to end up with total population under 25, 25-44, 45-64, and 65 and up. From there, I divided by the total population to get a percentage of the pop in each of these categories. I left it as a decimal, since I knew I was going to work some visuals in Tableau. Once in Tableau, I converted these columns to %. I did a similar thing with education, adding columns together until I was happy with the final product. After joining with the age Dataframe, I was able to create another calculated column to return the percentage of the population who has a high school diploma, some college, and college degree(all inclusive). Then, I was able to join with the income dataset, keeping only the median income and the error margin columns. 

I originally found a dataset from dataworld that was supposed to contain over 18K vegan/vegetarian restaurants across the US. I quickly realized this dataset was not vegan/vegetarian specific. Quiznos and Famous Dave’s are far from vegetarian. This same database had a vegan specific dataset with 10K rows. After filtering out duplicates (based on the address column), it dropped to 200 rows. I was discouraged to say the least, and spent many hours searching the web for useable data. I landed on happycow.com, since this was one of the few websites with full searches of vegan/vegetarian specific restaurants in the US (not just restaurants with vegan/veggie options). My excitement was quickly diminished when I realized they did not allow web scraping. Nonetheless, I decided to copy/paste a list of cities with these restaurants and a count of restaurants per city into a spreadsheet to create my own dataframe. At least this way I would know what cities house these establishments and how many are in each city. The more I thought about it, the more I knew I needed to dig a little deeper and try to find a way to bring in the actual restaurants for my analysis. 

At this point, I decided to take on the massive challenge of scraping Yelp API for vegan/vegetarian restaurants within the list of 1151 cities I pulled from Happy Cow. Thankfully, with the help of my peers and instructors, I was able to write a function with several for loops to retrieve the lists of restaurants across the country. The Yelp API only allows 5000 calls per day, so it took several days to achieve my goal of all vegan/veggie restaurants listed within my search of 1151 cities. This was important for me to accomplish because I wanted to create a user friendly interactive dashboard for anyone looking for vegan/veggie establishments in the US. I also wanted current data to show the spans of the industry. 

I created a dataframe with the counts of restaurants per city to join to my census bracket dataset. After trying inner and left joins, I realized they would not match up because my restaurant dataframe had states as abbreviations and my census data had full state names. Again, since there are so many duplicate city names, I had to join on two columns. From here, I opened in excel and quickly replaced the abbreviations with full state names so I could easily join the two. Since there are many mutual city names across the globe, I pulled in many restaurants from cities across the pond, i.e. Birmingham, Florence, etc. I removed these from my data to have an accurate count of restaurants within the US. 

Notes about Tableau:
To get around cities with the same name in different states, add a calculated column with city + state 
