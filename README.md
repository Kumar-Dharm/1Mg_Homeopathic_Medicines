# 1Mg_Homeopathic_Medicines  
![1Mg_logo](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/36bcd26b-ee28-49a2-af8c-82a7d8bb9537)

In the "1Mg Homeopathic Medicine" project, the goal is to leverage web scraping, data preprocessing, analysis, 
and visualization techniques to assist a client who intends to open a homeopathic medicine store. 
The project involves extracting data from the Tata 1mg website, transforming it into a usable format, 
and creating an interactive dashboard to provide insights for the client's business decision-making.

## Folder Structure
| Files | Description |
|-------| ------------|
| **Excel_work** | "Excel_Work" is a folder housing Excel datasets and all Excel-related tasks and activities. |
| **PowerBI_work** | "PowerBI_Work" folder encompasses datasets for Power BI and all tasks and activities performed within Power BI, including the creation of dashboards. |
| **Web_scraping** |  "Web_Scraping" folder comprises an IPython Notebook (IPYNB) file for web scraping purposes. |
| **README.md** | "README.md" serves as the project's informational documentation. |

## Table of Contents
- [Introduction](#introduction)
- [Objectives](#objectives)
- [Project Plan](#project-plan)
- [Web Scraping](#web-scraping)
- [Data Cleaning](#data-cleaning)
- [Preprocessing and Exploration](#preprocessing-and-exploration)
- [Analysis and Insights](#analysis-and-insights)
- [Business Solution](#business_solution)
- [Dashboard](#dashboard)
- [Challenges](#challenges)
- [Learning](#learning)
- [Conclusion](#conclusion)

## Introduction
- Introducing the '1Mg Homeopathic Medicine Store Analysis' project, which harnesses data from Tata 1mg, India's leading digital healthcare platform.  
- The project's core objective is to aid clients in the establishment of prosperous homeopathic medicine stores.  
- By extracting valuable insights from 1mg's comprehensive offerings, including E-pharmacy, Diagnostics, and Health content, the project equips clients to make informed, data-driven decisions.  
- Ultimately, this initiative empowers individuals with the essential information needed to succeed in the homeopathic medicine retail sector.

## Objectives

**Objectives:**  
  * Conduct comprehensive market research based on data.  
  * Identify the specific target audience for the homeopathic medicine store.  
  * Estimate the total cost required to establish and operate the store effectively.  
  * Estimate the total revenue considering a 10% profit margin.  
  * Develop interactive dashboards to address customer queries effectively.  

**Problem Statements:**  
  * Determine the preferred brand of homeopathic medicines to stock.  
  * Identify the optimal product assortment to initiate with.  
  * Analyze the most common diseases treated by homeopathic medicines.  
  * Estimate the capital investment needed for setting up the store.  

## Project Plan

**Project completion pathway:**  
  1. **Web Scraping:** Extract relevant data from Tata 1mg website for homeopathic medicines.
  2. **Data Cleaning:** Ensure data integrity by removing duplicates, handling missing values, and correcting inconsistencies.
  3. **Exploratory Data Analysis:** Uncover insights and patterns in the data through visualizations and summary statistics.
  4. **Insights Extraction:** Apply skills and tools to derive meaningful insights and trends from the data.
  5. **Business Analysis:** Translate statistical findings into actionable business insights for decision-making.
  6. **Dashboard:** Create an interactive visualization tool to present key findings and allow user exploration.

## Web Scraping  
<pre><code>
**Getting the link of all the products**
box_link=[]
for i in range(0,100):
    var={"user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36"}
    url ="https://www.1mg.com/categories/homeopathy/homeopathy-medicines-106?filter=true&pageNumber="+str(i)
    response=requests.get(url, headers=var)
    soup=BeautifulSoup(response.text, "lxml")
 
    for i in soup.find_all("a"):
        com_link="https://www.1mg.com"+ str(i.get("href"))
        box_link.append(com_link)
#print(box_link)
print(len(box_link))
</code></pre>

## Data Cleaning  
**Uncleaned Data**  
![1Mg_Uncleaned_data_snip](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/348d246a-67dd-436d-ad18-b4c8d1edb8d7)  

## Preprocessing and Exploration

**Null and Noise Handling:**  
- Conducted a thorough assessment to identify and address null values in the dataset. Also, implemented noise reduction techniques to ensure data accuracy.

**Data Type Consistency:**  
- Ensured uniform data types across the dataset. This consistency aids in smooth processing and analysis. 

`MID(I2, FIND("Key Benefits:", I2)+13, FIND("Dosage:", I2) - FIND("Key Benefits:", I2))`  

`SUBSTITUTE(MID(I6, FIND("Key Ingredients", I6) + 16, FIND(".", I6, FIND("Key Ingredients", I6)) - FIND("Key Ingredients", I6)), "Indications:", "")` 

**Table Size and Shape Evaluation:**  
- Assessed the size and shape of each table to comprehend its structure. This step is crucial for understanding the data's composition.

* By executing these preprocessing steps, the dataset was refined, cleaned, and made ready for further analysis, establishing a solid foundation for accurate insights.

**Cleaned Data**
![1Mg_Cleaned_data_snip](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/bc82b36b-e634-45e9-ac8b-fa3c8a422d54)  

**Important Features**  
| Numerical Variables | Categorical Variables |
| ------------- | ------------- |
| MRPs | Product Names |
| Selling Price | Brands |
| Ratings | Key Ingredients |
| Number of Ratings | Key Benefits Area |
| Revenue | Reviews |

## Analysis and Insights  
<pre><code>
**Questions:**  
  1. Number of medicine available of different benefit area.  
  2. Price range of medicine for each benefit area.  
  3. Brand specialization(Key Benefits) of each area.  
  4. Average price, min price , max price and number of products for each brand.  
  5. Average number of rating for each brand in their specialization products where the number of rating is not NULL.  
  6. Maximum number of times ingredient used in each benefit area.  
  7. Average cost for ingredients.  
  8. Most used ingredient.  
  9. Which brand has most greater than 4 point review medicine?  
</code></pre>

**Insights**  
![Insights](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/3ae7958d-a83c-412a-aa2d-a2ddf8f89bcf)

**Brands Price Variation**  
![Brands_price_variation](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/296b0264-3911-4c9b-9067-ba4615dc2ae5)  
- Adel Pekana Germany, Dr. Reckeweg & Co, and Bjain Pharmaceuticals Pvt Ltd stand out as the top three brands exhibiting the most significant price fluctuations within the homeopathic market.  
- These three brands also hold top positions in terms of customer reviews and ratings, underscoring their prominence and appeal in the market.  
- Notably, the price variance metrics, including minimum, maximum, average prices, and product count, demonstrate substantial disparities for these brands. 

* This underscores the dynamic nature of their pricing strategies and market presence.

**Products Price Variation**  
![Min_Max_Price](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/5afe4d63-433c-4d72-af1b-a9eb7c6d637c)  
- When examining product price variations, it becomes evident that conditions such as Erectile Dysfunction, Constipation, Anxiety, and Depression exhibit the most pronounced disparities in terms of minimum and maximum product prices within the market.  
- Following closely behind, we find conditions including Diabetes, Weakness, Mouth Ulcers, Urinary Complaints, Thyroid Problems, and Bone Joints and Muscle Pain displaying notable price variations.  
* This underscores the intricate pricing dynamics prevalent in these therapeutic categories.

## Business_solution
![Business_solution](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/1cebe5c9-6271-4f82-b3eb-540ef5733c48)

* The project aims to provide the client with valuable insights to make informed decisions about opening a homeopathic medicine store.
* By analyzing the data and offering an interactive dashboard, the project assists the client in understanding market trends, estimating costs, and optimizing their inventory.
* Ultimately, the project contributes to the success and profitability of the client's business venture.

# Dashboard
![1Mg_PowerBI_Dashboard](https://github.com/Kumar-Dharm/Image_Gallery/assets/132021299/8ad90b01-f67f-442e-8b9f-20f27436b957)

## Challenges
- Web Scrapping:
Need to explore one of the new python library. 
We get banned from scrapping products data more than 50 at a time.
- Data Cleaning:
Key benefits and key ingredients of the medicines were in paragraph. 
No of products purchased by customers was not available.
- Team collaboration:
As it was first project and we are not physically available at a place so collaborating with all the members was bit challenging.
- Time constraints:
As it was construct week project and we need to complete within the given time frame.  

## Learning
- **Web Scraping Proficiency:** Acquired skills in web scraping to efficiently gather data from online sources.
- **Data Cleaning Expertise:** Developed the ability to clean and preprocess raw data, ensuring its quality and consistency.
- **Insight Generation Skills:** Gained experience in using analytical tools and methods to extract meaningful insights from data.
- **Problem-Solving Skills:** Applied data-driven insights to formulate practical business solutions.
- **Dashboard Development:** Developed proficiency in creating interactive dashboards for data visualization and user engagement.
- **Client Communication:** Enhanced the ability to effectively communicate and address client queries and needs using data-driven solutions.

## Conclusion  
* **Smart Choices:** We assumed customers who bought items also rated them. Our top-rated brands, 23 in all, score above 4.
* **Key Benefits:** From our study, we found 35 important benefits that our products provide, covering a wide range of needs.
* **Great Variety:** Our offerings include a whopping 1628 different products, ensuring options for everyone.
* **Smart Picks:** We're suggesting starting with 300 diverse products, focusing on the top 10 brands and 30 key benefits.
* **Financial Picture:** To kickstart the Homeopathic store, we estimate a setup cost of 900,000 units. We're aiming for a revenue of 990,000 units, with a 10% profit margin of 90,000units.
* **Strategic Move:** The 80-20 principle shows that 80% of our earnings come from just 20% of our products/brands.

This knowledge guides us in creating a strong Homeopathic medicine store that's attentive to customer desires and positioned for success.

|---------------------------------------------------------------------------------------------------------------------------|
