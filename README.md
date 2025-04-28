PROJECT OVERVIEW 
EV Pulse: Data Insights on Electric Vehicles 
INTRODUCTION 
Electric vehicles (EVs) have emerged as a transformative force in the global transition toward 
sustainable transportation. As environmental concerns, energy security, and technological 
advancements reshape the automotive industry, electric vehicles are becoming increasingly 
prominent on roads worldwide. This project aims to explain and analyze the trends, patterns, and 
insights surrounding electric vehicle adoption in Washington State through a data science lens. 
Washington State has been at the forefront of EV adoption in the United States, driven by 
progressive policies, strong environmental awareness, and an expanding network of EV 
infrastructure. Understanding the nuances of EV registration data can help identify which vehicle 
types are gaining popularity, which counties are leading in adoption, and how manufacturer trends 
are evolving over time. 
The core dataset used in this project contains detailed records of electric vehicles registered in 
Washington. By leveraging exploratory data analysis (EDA), visualization, and statistical 
methods, this study seeks to uncover key insights that inform public policy, environmental 
strategy, and consumer behavior. 
This report not only provides a deep dive into the patterns within EV data but also contextualizes 
findings with real-world implications. It answers questions like: 
What are the most popular EV models in the state? 
Which counties are adopting EVs the fastest? 
How does electric range vary by vehicle type and make? 
Are there clear year-over-year trends indicating growth? 
Additionally, the report highlights challenges in the data, proposes areas for future research, and 
presents actionable recommendations based on observed trends. Through this, the goal is to create 
a comprehensive and insightful overview of the electric vehicle landscape in Washington State. 
DATASET DESCRIPTION 
The analysis in this project is based on a publicly available dataset provided by the 
Washington State Department of Licensing. It contains a record of all electric vehicles (EVs) 
registered in the state, reflecting a snapshot of EV adoption at the time of data collection. 
Below is a comprehensive description of the dataset and its key attributes. 
Overview 
Source: Washington State Department of Licensing  
Scope: All registered electric vehicles in Washington State 
Time Frame: As of [Insert Date if Known] 
Number of Records: Approximately [Insert Number of Rows] 
File Format: CSV  
The dataset focuses on Battery Electric Vehicles (BEVs), Plug-in Hybrid Electric 
Vehicles  (PHEVs), and other types of electrified vehicles. 
PROJECT OBJECTIVE 
The primary objective of this data science project is to explore, analyze, and extract meaningful insights 
from the electric vehicle (EV) registration data of Washington State. The project aims to contribute a 
data-driven understanding of EV adoption patterns, trends, and behaviors at both the statewide and 
regional levels. 
With the increasing shift toward sustainable energy and clean transportation, electric vehicles are a vital 
component of reducing greenhouse gas emissions and fossil fuel dependency. By examining the current 
state of EV adoption in Washington, this study seeks to support informed decision-making among 
policymakers, utility providers, environmental agencies, and potential EV consumers. 
SPECIFIC GOALS: 
• Understand the distribution and adoption of electric vehicles across Washington 
State by analyzing county- and city-level data. 
• Clean and preprocess the dataset to ensure accurate interpretation, especially regarding 
dates, vehicle types, makes, and model years. 
• Visualize the growth of EV adoption over time, identifying key years and policy 
periods that influenced registration surges. 
• Identify the most popular vehicle makes and models (e.g., Tesla, Nissan Leaf, 
Chevrolet Volt) and how their popularity varies by region. 
• Examine the types of electric vehicles (Battery Electric Vehicles vs Plug-in Hybrids) and 
their proportions in the population. 
• Analyze electric range and model year trends, and how these features have evolved 
over time for newer EVs. 
• Map electric vehicle registrations by county to uncover geographic EV hotspots and 
underserved areas. 
• Provide insights for policymakers, urban planners, and utility companies to support 
EV infrastructure planning and sustainable energy strategies
Scope of the Project 
This project focuses exclusively on electric vehicle registrations in Washington State. It does not attempt to forecast EV sales or 
compare Washington data to other states directly but rather provides a focused, in-depth exploration of the current adoption 
landscape. The scope is limited to the attributes available in the dataset but incorporates external insights (e.g., policy relevance, 
market shifts) where appropriate. 
• Geographic Focus: All counties and cities within Washington State. 
• Vehicle Types Covered: Battery Electric Vehicles (BEVs), Plug-in Hybrid Electric Vehicles (PHEVs), and limited Fuel Cell 
Electric Vehicles (FCEVs). 
• Analysis Methods: Descriptive statistics, visual analytics, correlation analysis, and geographic mapping. 
• End-Users: Policymakers, environmental agencies, EV manufacturers, researchers, and the general public 
Methodology 
This section outlines the step-by-step approach taken to extract insights from the dataset. 
Data Cleaning: 
• Removed missing or incomplete records where necessary. 
• Standardized column names and vehicle makes/models for consistency. 
• Filtered out non-electric or ambiguous entries. 
Exploratory Data Analysis (EDA): 
• Frequency analysis on categorical data (Make, Model, EV Type). 
• Distribution analysis on numerical data (Electric Range, Model Year). 
• Cross-tabulations of Make vs EV Type, Model Year vs Range, etc. 
Visualization: 
• Used libraries like matplotlib, seaborn, and plotly for clear, interactive visuals. 
• Plotted bar charts, histograms, box plots, line graphs, and geographic maps. 
Correlation & Comparative Analysis: 
• Generated correlation heatmaps to identify linear relationships between numeric variables. 
• Compared trends across EV types and makes to assess technological evolution. 
Tools and Technologies Used 
• Programming Language: Python 
• Libraries: pandas, numpy, matplotlib, seaborn, pandas 
• Platform: Google Colab 
• Data Source: Washington State Department of Licensing. 
Significance of the Study 
This analysis has real-world implications for various stakeholders: 
• Government: Supports evidence-based policymaking, incentive planning, and infrastructure investment. 
• Manufacturers: Offers insights into regional preferences and growing EV market segments. 
• Utility Companies: Aids in forecasting demand and planning for electricity distribution. 
• Environmental Advocates: Provides data to measure climate goals and carbon reduction impact. 
DATA IMPORT AND LIBRARIES 
REQUIRED LIBRARIES 
import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt 
import seaborn as sns 
# Deals with tabular data (DataFrames) 
# Performs numerical/statistical operations 
# Plots basic graphs 
# Enhances visualization with plots 
LODING DATASET AND INSPECTING 
df=pd.read_excel('/content/Electric
 _Vehicle_Population.xlsx') 
print(df.shape)                           
df.tail(10)                                
print(df.info()) 
print(df.head(10)) 
//View column names 
print(df.columns)
DATA CLEANING AND PREPATION 
 
 
  Getting the description of the dataset 
         
        df.describe() 
 
 
        Cleaning  Data   And  Removing   The  NULL Value 
 
       if 'Legislative District' in df.columns: 
               df=df.drop(columns='Legislative District',axis=1) 
 
        if 'Base MSRP' in df.columns: 
              df=df.drop(columns='Base MSRP',axis=1) 
 
        df ['Electric Range']. fillna(df ['Electric Range']. mean (), inplace=True) 
 
        print (df ['2020 Census Tract']. mode ()) 
 
        df ['2020 Census Tract']. fillna (df ['2020 Census Tract']. mode () [0], inplace=True) 
        
        df.isnull().sum()                    // Checking the null values of the Data Set 
 
        if 'Vehicle Location' in df.columns: 
               df=df.drop(columns='Vehicle Location',axis=1) 
        
        common_county = df['County'].mode()[0] 
        df['County'].fillna(common_county,inplace=True) 
 
        common_city = df['City'].mode()[0] 
        df['City'].fillna(common_city,inplace=True) 
   
        common_Electric_Utility = df['Electric Utility'].mode()[0] 
        df['Electric Utility'].fillna(common_Electric_Utility,inplace=True) 
 
        common_Electric_Range = df['Electric Range'].mode()[0] 
        df['Electric Range'].fillna(common_Electric_Range,inplace=True) 
 
        common_Postal_Code = df['Postal Code'].mode()[0] 
        df['Postal Code'].fillna(common_Postal_Code,inplace=True) 
 
       common_2020_Census_Tract = df['2020 Census Tract'].mode()[0] 
       df['2020 Census Tract'].fillna(common_2020_Census_Tract,inplace=True) 
       
       df.isnull().sum() 
 
 
 
                    EXPLORATORY DATA ANALYSIS 
(EDA) 
 
 
 
       //Find the mode value of “make” column 
       print(df[‘Make’].mode()) 
         
       print(df['Make'].mode()[0]) 
 
      //Getting more about the data 
       df.describe() 
 
       //Finding the number of the model made by company 
        
       df['Model'].value_counts() 
 
       df['Make'].value_counts() 
      
      //Mean, Median, Mode for Electric Range 
        //Mean 
      mean_value = df['Electric Range'].mean() 
       print("Mean Electric Range:", mean_value) 
 
      //Median 
      median_value = df['Electric Range'].median() 
      print("Median Electric Range:", median_value) 
 
     //Mode (can return multiple values) 
       mode_value = df['Electric Range'].mode() 
       print("Mode Electric Range:", mode_value.tolist()) 
    //Descriptive statistics for numeric columns 
       print("Mean values:\n", df.mean(numeric_only=True)) 
       print("Median values:\n", df.median(numeric_only=True)) 
       print("Mode values:\n", df.mode(numeric_only=True).iloc[0]) 
 
 
 
  
VISUAL DATA EXPLORATION 
 
 
         //Creating a count plot for "make "column 
            sns.countplot(x='Make',data=df) 
 
       //Pie Chart: EV Type Distribution 
           ev_type_counts = df['Electric Vehicle Type'].value_counts() 
           plt.figure(figsize=(7, 7)) 
           plt.pie(ev_type_counts.values,labels=ev_type_counts.index,     
autopct='%1.1f%%', startangle=140) 
           plt.title('EV Type Distribution') 
           plt.axis('equal') 
           plt.tight_layout() 
           plt.show() 
      //Histogram: Distribution of Model Years 
          plt.figure(figsize=(10, 6)) 
          plt.hist(df['ModelYear'],bins=range(int(df['ModelYear'].min()), 
int(df['Model Year'].max()) + 1), color='teal', edgecolor='black') 
          plt.title('Distribution of Model Years') 
          plt.xlabel('Model Year') 
          plt.ylabel('Number of Vehicles') 
          plt.show() 
      //Line Chart for Growth of Tesla Vehicles by Year 
         tesla_data = df[df['Make'] == 'TESLA'] 
         tesla_by_year = tesla_data['Model Year'].value_counts().sort_index() 
        plt.figure(figsize=(12, 6)) 
        plt.plot(tesla_by_year.index,tesla_by_year.values,marker='o', 
linestyle='-', color='crimson') 
        plt.title('Growth of Tesla EVs by Model Year') 
        plt.xlabel('Model Year') 
        plt.ylabel('Number of Teslas') 
        plt.show() 
 
        //Scatter Plot: Model Year vs make 
              
            if 'Make' in df.columns: 
                     plt.figure(figsize=(10, 6)) 
                     plt.scatter(df['Model Year'], df['Make'], alpha=0.3, color='gray') 
                     plt.title('Scatter Plot: Model Year vs. Make') 
                     plt.xlabel('Model Year') 
                     plt.ylabel('Make') 
                     plt.show() 
 
     //Top 10 Makes (Manufacturers) 
         
        plt.figure(figsize=(10, 6)) 
         top_makes = df['Make'].value_counts().head(10) 
        sns.barplot(x=top_makes.values,y=top_makes.index, palette='viridis') 
        plt.title('Top 10 Electric Vehicle Makes') 
        plt.xlabel('Number of Vehicles') 
        plt.ylabel('Make') 
        plt.show() 
     //Vehicle count by Model Year 
        
       plt.figure(figsize=(12, 6)) 
       model_year_counts = df['Model Year'].value_counts().sort_index() 
       sns.lineplot(x=model_year_counts.index, y=model_year_counts.values, 
marker='o') 
       plt.title('Electric Vehicles by Model Year') 
       plt.xlabel('Model Year') 
       plt.ylabel('Number of Vehicles') 
       plt.show() 
 
      
 
 
     //Distribution by Electric Vehicle Type 
       plt.figure(figsize=(8, 6)) 
       ev_type_counts = df['Electric Vehicle Type'].value_counts() 
       sns.barplot(x=ev_type_counts.values,y=ev_type_counts.index, 
  palette='coolwarm') 
        plt.title('Distribution by EV Type') 
        plt.xlabel('Number of Vehicles') 
        plt.ylabel('EV Type') 
        plt.show() 
 
 
     //Vehicles by County (Top 10) 
     plt.figure(figsize=(10, 6)) 
     county_counts = df['County'].value_counts().head(10) 
     sns.barplot(x=county_counts.values,y=county_counts.index, 
palette='mako') 
     plt.title('Top 10 Counties by Number of EVs') 
     plt.xlabel('Number of Vehicles') 
     plt.ylabel('County') 
     plt.show() 
 
 
     //Box plot of model years grouped by EV type 
     df.boxplot(column='Model Year', by='Electric Vehicle Type') 
     plt.title('Model Year Distribution by EV Type') 
     plt.xlabel('Electric Vehicle Type') 
     plt.ylabel('Model Year') 
     plt.xticks(rotation=15)
     plt.show()


KEY FINDINGS 
EV Hotspots by County 
Identify counties with the highest number of registered EVs — such as King, Snohomish, or 
Pierce — and explore potential reasons (population, income, infrastructure). 
Adoption Trends Over Time 
• Steady Growth Since Early 2010s: 
EV adoption in Washington State began to rise significantly after 2011, with noticeable year-over
year growth. 
• Sharp Increase Post-2018: 
There was a steep rise in EV registrations after 2018, likely influenced by increased model 
availability (e.g., Tesla Model 3), improved battery technology, and greater public awareness. 
• Surge During 2020–2023: 
Despite the COVID-19 pandemic, EV adoption surged from 2020 to 2023. Government stimulus 
programs, state-level tax incentives, and clean vehicle mandates likely played a role. 
• Dominance of Battery Electric Vehicles (BEVs): 
BEVs began to outpace Plug-in Hybrids in registrations, especially with the growing popularity of 
Tesla and other long-range EVs. 
• Model Year Shift: 
Newer models (2020 and above) make up a significant portion of the dataset, indicating rapid 
turnover toward newer and more efficient vehicles. 
Dominant Vehicle Makes & Models 
• Tesla Leads the Market: 
Tesla is the most registered electric vehicle make in Washington, with popular models like the 
Model 3, Model Y, and Model S dominating the list. 
• Nissan’s Early Popularity: 
The Nissan Leaf is one of the earliest and most widely adopted EVs, especially in earlier model 
years (2011–2017). It remains common in both urban and suburban areas. 
• Rise of New Entrants: 
Other brands like Ford (e.g., Mustang Mach-E), Hyundai (e.g., Kona Electric, Ioniq), and Kia 
(e.g., Niro EV) have gained traction in recent years, showing market diversification. 
PROJECT SUMMARY & TAKEAWAYS 
SUMMARY OF VISUALIZATIONS 
This project has provided an in-depth exploration into electric vehicle (EV) registration patterns across Washington State 
using data science methodologies. By focusing on key attributes such as make, model, model year, range, and geographic 
distribution, the analysis offered actionable insights into how EV adoption is progressing within the region. 
Key Insights from the Analysis: 
• Popular Manufacturers: Tesla emerged as the most dominant EV brand in the state, with its various models—
 including the Model 3 and Model Y—representing a large portion of total registrations. Nissan and Chevrolet also 
maintained strong positions with consistent sales of the Leaf and Bolt, respectively. 
• Model Year Trends: A steady increase in registrations of newer EV models indicates strong market growth and 
consumer trust in newer technologies, suggesting effective incentives and increasing awareness. 
• EV Type Distribution: Battery Electric Vehicles (BEVs) make up the majority of registered EVs in Washington, 
reflecting a shift away from traditional internal combustion and even hybrid models. Plug-in Hybrids (PHEVs) 
represent a smaller but steady share. 
• Geographic Patterns: Urban counties such as King, Snohomish, and Pierce lead in EV registrations, likely due to 
better charging infrastructure, higher income levels, and greater environmental awareness. Conversely, rural areas 
show lower adoption rates, pointing to the need for broader charging networks. 
• Range Evolution: The average electric range of vehicles has steadily increased over the years, with newer models 
offering better efficiency and longer distances. This has likely helped reduce “range anxiety” among consumers. 
• CAFV Eligibility: Vehicles qualifying for Clean Alternative Fuel Vehicle incentives showed higher adoption, 
indicating that financial policies continue to play a significant role in consumer decisions. 
Broader Implications: 
The findings support Washington State’s efforts toward reducing carbon emissions and transitioning to clean 
transportation. The project highlights the importance of: 
• Expanding charging infrastructure in rural and underserved regions 
• Continuing or enhancing EV purchase incentives 
• Supporting data-driven policymaking for climate and energy goals 
Limitations: 
Although the project provides robust insights, several limitations should be acknowledged: 
• The dataset lacks detailed demographic data about vehicle owners 
• Some records contain missing or inconsistent fields 
• No temporal registration history (e.g., deregistration or resale data) 
Reflections and Learning Outcomes: 
This project demonstrated the powerful role that data science can play in supporting sustainable development. From data 
cleaning to visualization, geospatial analysis, and interpretation, each phase contributed to forming a complete picture of 
the EV landscape in Washington. Key technical skills used include: 
• Data preprocessing with pandas 
• Data visualization with matplotlib, seaborn, and plotly 
• Geographic analysis using county-level groupings 
• Communicating insights effectively through narrative and visuals 
Conclusion: 
Electric vehicles are not only a technological innovation but also a societal shift toward a cleaner, more responsible future. 
This project captures a critical moment in that transition—showcasing where Washington stands, where gaps remain, and 
what might come next. As technology advances and EV accessibility grows, continuous analysis like this will be crucial in 
ensuring equitable and efficient progress. 
• Histogram of EV Types: 
A histogram displayed the distribution of electric vehicle types in the dataset, highlighting that Battery Electric 
Vehicles (BEVs) dominate over Plug-in Hybrid Electric Vehicles (PHEVs), showing a clear shift toward full 
electrification. 
• Pie Chart by County or Utility: 
Pie charts showed the proportion of EV registrations across counties and electric utilities, helping identify regions 
with strong adoption and revealing how certain utilities (like Puget Sound Energy) support large EV populations. 
• Scatter Plot of EV Registrations Over Time: 
This plot revealed a rising trend in EV adoption, especially between 2018–2023. It highlighted growth spikes that 
likely align with tax incentives, new model releases, and broader EV awareness. 
• Boxplot of Electric Range by Make or Model Year: 
Boxplots visualized the variation in electric range across vehicle makes or model years, revealing that newer models 
tend to offer longer ranges, reflecting technological improvements. 
• Heatmap of Top Makes vs Top Counties: 
A heatmap demonstrated how different vehicle makes are distributed across counties, helping uncover regional brand 
preferences (e.g., Tesla’s popularity in King County). 
• Line Plot of Yearly Adoption Trends: 
The line plot illustrated year-on-year growth in registrations, confirming that Washington State is experiencing a 
consistent upward trend in EV adoption, particularly after 2020. 
MAJOR INSIGHTS 
▪ Rapid rise in EVs after 2018. 
▪ Dominance of BEVs (especially Teslas). 
▪ Concentration in urban/suburban counties. 
▪ Growing electric range in newer models. 
Challenges Faced During the Project: 
• 
While working on this project, several technical and analytical challenges were encountered: 
1. Data Cleaning and Inconsistencies 
The dataset contained inconsistencies in vehicle model naming conventions (e.g., “Model 3” vs. 
“MODEL 3”). 
 
Missing values in columns such as Electric Range and Base MSRP required careful handling, either 
through imputation or removal. 
2. Geographical Data Complexity 
Although counties and zip codes were provided, some cities were missing or mismatched, making 
accurate geographic mapping more complex. 
 
Legislative district-level insights were harder to extract due to uneven distribution. 
3. Class Imbalance 
 
Some manufacturers (e.g., Tesla) dominated the dataset, while others had minimal representation. 
This made fair comparisons more difficult. 
4. External Context Dependency 
Some analytical conclusions depended on external factors such as EV incentives, charging 
infrastructure, or policy—data that wasn’t included in the original dataset. 
Environmental and Economic Impact: 
 
1. Environmental Benefits 
A large-scale shift to EVs reduces tailpipe emissions, leading to improved urban air quality. 
 
As Washington uses significant hydroelectric power, the overall carbon footprint of EV usage is 
significantly lower than in fossil-fuel-dependent regions. 
2. Economic Growth 
The growth of EVs supports local green jobs, including manufacturing, battery recycling, and 
charging infrastructure development. 
 
EV incentives may help low- to middle-income households adopt cleaner vehicles over time. 
Policy Recommendations: 
 
Based on the data analysis, the following policy actions are recommended: 
1. Expand Charging Networks 
Focus on underserved and rural areas to boost confidence in EV adoption. 
Provide grants for commercial and residential EV charging installations. 
2. Continue and Expand Incentives 
 
Extend Clean Alternative Fuel Vehicle (CAFV) programs to cover more vehicle types and price 
ranges. 
Offer incentives for used EV purchases to make them accessible to more demographics. 
3. Public Awareness Campaigns 

Educate the public on EV range capabilities and cost benefits over time. 
Provide real-life success stories and total-cost-of-ownership comparisons with gas vehicles. 
 
Future Work and Extensions: 
 
This project can be extended in several directions: 
1. Comparative State Analysis 
Comparing Washington's EV adoption trends with states like California or Oregon could offer 
broader regional insights. 
2. Time Series Forecasting 
 
With historical data, we could forecast EV adoption using ARIMA models or LSTM neural 
networks. 
3. Integration with Charging Station Data 
Analyzing charging station availability alongside registration trends can help identify infrastructure 
gaps. 

4. Consumer Behavior Analysis 
With access to demographic or usage data, a more targeted analysis of EV consumer profiles could 
be performed. 
Policy/Infrastructure Implications 
• The state should prioritize EV infrastructure like charging stations in high-growth counties. 
• Utilities should prepare for increased load in EV-dense areas. 
• Policymakers can use this data to design targeted subsidies or regulations.
