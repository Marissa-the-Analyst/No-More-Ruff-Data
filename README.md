# No-More-Ruff-Data
I transformed a synthetic, warehouse-scale dataset of 2,080 pet products into a clean, analysis-ready resource. Using advanced filtering, logical formulas, and text cleaning, I normalized inconsistent attributes—like grain-free status and weights bridging the gap between messy web-scraped data and actionable supply chain insights.

## Before
<img width="1056" height="622" alt="image" src="https://github.com/user-attachments/assets/68764c7b-752e-4f98-85bf-8feb5b326dcc" />

## After
<img width="1495" height="503" alt="image" src="https://github.com/user-attachments/assets/47b819a2-7229-4b5f-87ae-8785b209117c" />

# Finished Product 
-	A clean dataset, suitable for answering queries and questions.

# Programs Used
- Excel

# Goals
-	A clean dataset suitable for downstream analysis

# Data Source
I got this dataset from Kaggle! Here is the link [Premium Dog Outlets](https://www.kaggle.com/datasets/scoeyd/premium-dog-outlets). The data is synthetic but from my personal experience in a warehouse environment, I found its vastness and general layout to be very familiar!

# Cleaning Process
Cleaning. I’m working on this giant dataset with 2080 products. I used a formula to help identify duplicates: <br>
=IF((B2=B3)*(D2=D3), "look", "") <br>

It flagged 2 duplicates. One was the 1st product that had the exact same name, price, weight etc etc. I removed that one. Then there was one at 745. This one had 2 different flavors so we were able to ignore that.
<br>

I replaced â€‘ in all of the cells with a space using find and replace. Apparently they are hyphens pre-scrape so Ill do that from now on. <br>

In a moment of ambition or blind sidedness, I used a filter query to manually pull all the instances of null weight and dog food category:
<br>
=FILTER(Product[[ProductID]:[COGS]],(Product[Weight]="NULL")*(Product[Category]="Dog Food")) <br>

Let it be noted the same effect can be achieved easier using auto filters.
<br>

Anyways I'm noticing a few things. There are instances where NULL represents N/A and there are instances where NULL is just missing data. <br>

I changed all of the weight ones that were 0 or NULL to blanks to preserve the integrity of the integer column and make downstream analysis easier. <br>

Another trick is highlighting duplicates and filtering by color <br>

Changed flavor from NULL to N/A when not in reference to dog food <br>

Recoded all of grain from 0’s and 1’s to yes, no, N/A
-	Used text contains to filter the product names w/ grain free and updated the grain

Updated material to be N/A when not in reference to applicable products
<br>

Hid extra rows after attempting to clear them.
<br>

# Existing Data Issues Post Clean
The necessity of so many descriptions, categories, and subcategories is questionable. As a backend for a website, it makes sense. As a supply chain environment, maybe if the subcategories were categorized as storing locations with each subcategory needing different handling requirements. Think dog food, canned dog food could likely be palletized and shipped as full pallets. Dry dog food could be as well, but it's more difficult. Depending on demand, dry dog food might need to be picked and handled differently, which would necessitate different storing requirements. Not to mention damaged Dog food needs to be near a cleanup station as to prevent pests/rot. 
<br>

There are a lot of missing values. Primarily across those extraneous subcategories. 

# Opportunities & Potential Business Questions
-	Which products give us the biggest margin?
-	Hill’s Science Diet just recalled all of their Salmon Flavored items; can you get me a list of ProductIds so I can reach out to the stores?
-	Valentines is coming up, give me a list of seasonal items associated that we can ship off in a display.  



