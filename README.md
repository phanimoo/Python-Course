# The Analysis
## 1. What are the most demanded skills for the top non-Senior level data roles in the US?

To identify the most in-demand skills for popular non-Senior level data-related roles, I filtered out the most popular positions and determined the top 5 skills for each. This analysis highlights the key job titles and their essential skills, helping me focus on the relevant skills for my targeted role.


To view my notebook with detailed steps, click here: [2_Skills_Demand.ipynb](Python_Data_Project/3_Project/2_Skills_Demand.ipynb)

### Data Visualization and Results

```python
fig, ax = plt.subplots(len(job_titles), 1, figsize=(15, 20))
sns.set_theme(style='ticks')
for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5).copy()
    sns.barplot(x='skill_perc', y='job_skills', data=df_plot, ax=ax[i], hue='job_skills', palette='viridis')
    ax[i].set_title(job_title)
    ax[i].set_xlabel(' ')
    ax[i].set_ylabel(' ')
    ax[i].set_xlim(0, 75)

    for n, value in enumerate(df_plot['skill_perc']):
        ax[i].text(value + 1, n, f'{value:.0f}%', va='center')

    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

plt.suptitle('Likelihood of Top Skills for Non-Senior Data Job Titles', fontsize=20, ha='center')
plt.tight_layout(rect=[0, 0, 1, 0.98])
plt.show()
```

![Visualization of Likelihood of Top Skills for Data Roles](Python_Data_Project/Images/data_skills_percent.png)
*Bar graphs showing the percentages of top 5 skills for the top most common data roles in the US*

### Insights

1. **SQL**:
   - **High Demand Across All Roles**: SQL is a critical skill for all positions, with the highest demand in Data Engineer (68%) and Data Analyst (51%). Even roles like Business Analyst (48%) and Cloud Engineer (32%) show a significant need.
   - **Key Insight**: Mastery of SQL is essential for any data-related role, highlighting its importance across various functions.

2. **Python**:
   - **Critical for Technical Roles**: Python is especially crucial for Data Scientist (72%), Machine Learning Engineer (70%), and Data Engineer (65%). It's also important for Data Analyst (27%) and Cloud Engineer (30%).
   - **Key Insight**: Python is a foundational programming language for technical roles, particularly those involving advanced analytics and engineering.

3. **Excel**:
   - **Essential for Business-Focused Roles**: Excel is a top skill for Business Analyst (42%) and Data Analyst (41%). It also appears in Cloud Engineer (19%).
   - **Key Insight**: Proficiency in Excel is particularly valuable for roles that require data manipulation and reporting.

4. **Tableau**:
   - **Important for Visualization**: Tableau is a key skill for Business Analyst (30%), Data Analyst (28%), and Data Scientist (24%).
   - **Key Insight**: Tableau is a sought-after tool for data visualization, necessary for roles that require presenting data insights.

5. **AWS**:
   - **Vital for Cloud and Engineering Roles**: AWS is highly relevant for Cloud Engineer (25%), Data Engineer (43%), and Machine Learning Engineer (31%).
   - **Key Insight**: AWS expertise is critical for roles involving cloud services and infrastructure.

6. **Other Notable Skills**:
   - **Power BI**: Important for Business Analyst (21%).
   - **R**: Relevant for Data Scientist (44%).
   - **SAS**: Useful for Data Analyst (19%) and Data Scientist (24%).
   - **Azure**: Significant for Cloud Engineer (15%) and Data Engineer (32%).
   - **Spark**: Important for Data Engineer (32%).
   - **Java**: Necessary for Software Engineer (21%).
   - **TensorFlow and PyTorch**: Key for Machine Learning Engineer (29% and 28%, respectively).

### Summary
- **Core Skills**: SQL and Python are the most universally demanded skills across multiple roles.
- **Role-Specific Skills**:
  - **Business and Analytical Roles**: Emphasize Excel and Tableau.
  - **Technical and Engineering Roles**: Focus on AWS, Azure, Spark, and specific programming frameworks like TensorFlow and PyTorch.
- **Visualization Tools**: Tableau is essential for roles that require data presentation.

By mastering these common and role-specific skills, individuals can enhance their job security and versatility in the job market. The overlap of critical skills like SQL and Python across multiple roles ensures that professionals remain competitive and adaptable, while proficiency in specialized tools like Excel, Tableau, and AWS can provide an edge in specific positions. This comprehensive skill set not only prepares individuals for a variety of data job titles but also offers greater stability and growth opportunities in their careers.

---

## 2. How are in-demand skills trending for Top 3 Data-Related Jobs?

To identify trends in data-specific roles, I analyzed the top three in-demand positions and pinpointed the top five skills for each. I then plotted the monthly percentage of job listings requiring these skills. This analysis highlights the consistency of these top skills across the industry, underscoring their importance for robust career stability and adaptability in various roles.

To view my notebook with detailed steps, click here: [3_Skills_Trend.ipynb](Python_Data_Project/3_Project/3_Skills_Trend.ipynb)

### Data Visualization and Results
```python
df_plot = df_DA_US_perc.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_style('ticks')
plt.title('Probability of Data Skills Over Time in the US (Data Analyst, Data Scientist, Data Engineer)')
plt.xlabel('2023')
plt.ylabel('Probability of Job Skill (%)')

# Fixing the legend
plt.legend(loc='center left', bbox_to_anchor=(1, 0.5))

# Adding percentage to y-axis
from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
```

![Visualization of Probability of Skills Trending Over Time in 2023](Python_Data_Project/Images/skills_trend_percent.png)
*Line graph showing overall the probability of each of the top skills appearing in job posts on month-to-month basis*

### Insights

1. **SQL Dominance**:
   - **Consistent High Demand**: SQL remains the most demanded skill throughout the year, maintaining a probability around 55%.
   - **Key Insight**: SQL is a stable and essential skill for data roles such as Data Analyst, Data Scientist, and Data Engineer.

2. **Python Popularity**:
   - **Sustained High Demand**: Python consistently shows a high probability, around 50%, indicating its crucial role across these positions.
   - **Key Insight**: Python is indispensable for technical data roles, emphasizing the need for proficiency in this language.

3. **R Steady Presence**:
   - **Moderate Demand**: The probability of R skills fluctuates around 25%, with a slight peak in late summer.
   - **Key Insight**: While not as dominant as SQL or Python, R remains a valuable skill, especially for roles focusing on statistical analysis.

4. **Tableau Demand Fluctuations**:
   - **Slight Variation**: Tableau's probability remains close to 20% but shows minor fluctuations throughout the year.
   - **Key Insight**: Tableau is important for data visualization roles, though its demand is relatively stable with some variation.

5. **Excel Consistency**:
   - **Low but Steady Demand**: Excel's probability stays consistently around 20%, indicating its steady presence in data roles.
   - **Key Insight**: Excel continues to be a fundamental skill, particularly for data manipulation and reporting tasks.

### Summary
- **Core Skills**: SQL and Python are consistently in high demand, reinforcing their importance across various data roles.
- **Supplementary Skills**: R, Tableau, and Excel, while not as dominant, remain valuable and contribute to a well-rounded skill set.
- **Stability and Fluctuation**: The demand for these skills shows overall stability with minor fluctuations, suggesting steady job security for professionals proficient in these areas.

This chart highlights the importance of focusing on SQL and Python for robust career stability, while also acquiring skills in R, Tableau, and Excel to enhance job prospects and adaptability.

### Data Visualization and Results cont'd
```python
fig, axes = plt.subplots(nrows=len(job_titles), figsize=(7, 15))

for i, title in enumerate(job_titles):
	ax = axes[i]
	
	# Filter the DataFrame for the current job title and country
	df_filtered = df_concat[(df_concat['job_title_short'] == title) & (df_concat['job_country'] == 'United States')].copy()
	
	# Extract the month number from the job posted date
	df_filtered['job_posted_month_no'] = df_filtered['job_posted_date'].dt.month
	
    # Create a pivot table of exploded job skills
	df_filtered = df_filtered.explode('job_skills')
	df_pivot = df_filtered.pivot_table(index='job_posted_month_no', columns='job_skills', aggfunc='size', fill_value=0)
	
	# Calculate the total counts for each skill then sort them by the totals
	df_pivot.loc['Total'] = df_pivot.sum()
	df_pivot = df_pivot[df_pivot.loc['Total'].sort_values(ascending=False).index]
	df_pivot = df_pivot.drop('Total')
	
	# Calculate the total counts for each month
	df_totals = df_filtered.groupby('job_posted_month_no').size()
	
	# Calculate the percentage for each skill
	df_perc = df_pivot.div(df_totals / 100, axis=0)
	df_perc = df_perc.reset_index()
	
    # Format months
	df_perc['job_posted_month_no'] = df_perc['job_posted_month_no'].apply(lambda x: pd.to_datetime(str(x), format='%m').strftime('%b'))
	
    # Get the top 5 skills
	df_perc = df_perc.set_index('job_posted_month_no')
	df_plot = df_perc.iloc[:, :5]

	sns.lineplot(data=df_plot, dashes=False, palette='tab10', ax=ax)
	sns.set_style('ticks')
	ax.set_title(f'Probability of Data Skills Over Time in the US ({title})')
	ax.set_xlabel('2023')
	ax.set_ylabel('Probability of Job Skill (%)')
	ax.set_ylim(0, 16)
	ax.legend(loc='center left', bbox_to_anchor=(1, 0.5))
	ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.tight_layout()
plt.show()
```

![Visulization of Each Role's Highest In-Demand Skills Listed Over Time](Python_Data_Project/Images/skills_trend_extended.png)
*Seperate line graphs of each of the top Data Jobs showing the probabilities of the top 5 skills appearing in job posts month by month*

### Insights

#### Data Analyst
- **Core Skills**:
  - **SQL**: Consistently the most demanded skill, around 14%, essential for data querying and management.
  - **Excel**: Steady demand, around 12%, crucial for data manipulation and analysis.
  - **Python**: Stable demand around 8%, important for data analysis and automation.

- **Supplementary Skills**:
  - **Tableau**: Around 7%, vital for data visualization and reporting.
  - **SAS**: Around 6%, used for statistical analysis and data manipulation.

#### Data Scientist
- **Core Skills**:
  - **Python**: Most demanded skill, around 14%, essential for data analysis, machine learning, and statistical modeling.
  - **SQL**: Steady demand, around 12%, important for data querying and manipulation.
  - **R**: Around 8%, critical for statistical analysis and data visualization.

- **Supplementary Skills**:
  - **SAS**: Around 5%, used for advanced statistical analysis.
  - **Tableau**: Around 5%, valuable for data visualization.

#### Data Engineer
- **Core Skills**:
  - **SQL**: Consistently the most demanded skill, around 10%, essential for database management and ETL processes.
  - **Python**: Steady demand, around 8%, important for scripting and automation.
  - **AWS**: Consistent demand around 6%, crucial for cloud-based data solutions.

- **Supplementary Skills**:
  - **Azure**: Around 5%, used for cloud services and data solutions.
  - **Spark**: Around 4%, important for big data processing.

### Key Analysis
#### Shared Skills Across Roles
- **SQL**: Dominates across all three roles, essential for data querying, management, and manipulation.
- **Python**: High demand in all roles, crucial for programming, data analysis, and automation.

#### Role-Specific Highlights
- **Data Analysts**: Excel and Tableau are particularly important for data manipulation and visualization.
- **Data Scientists**: R and SAS are significant for statistical analysis and advanced data modeling.
- **Data Engineers**: AWS, Azure, and Spark are key for cloud computing and big data processing.

### Summary
Focusing on mastering SQL and Python provides a robust foundation for career stability and adaptability across Data Analyst, Data Scientist, and Data Engineer roles. Additionally, gaining proficiency in role-specific skills enhances job prospects and versatility in the dynamic field of data science and engineering.

## 3. How well do jobs and skills pay for data roles?

To identify the highest-paying roles and skills, I focused on jobs in the United States and analyzed their median salaries. Initially, I examined the salary distributions for common data jobs, such as Data Scientist, Data Engineer, and Data Analyst, to understand which positions offer the highest pay.

To view my notebook for more details, click here:
[4_Salary_Analysis](Python_Data_Project/3_Project/4_Salary_Analysis.ipynb)

### Data Visualization and Results

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', hue='job_title_short', palette='Set1', order=job_order)
sns.set_style('ticks')
plt.title('Distribution of Average Yearly Salary for Data Jobs in US')
plt.xlabel('Average Yearly Salary (USD)')
plt.ylabel(' ')
plt.xlim(0, 300000)
plt.gca().xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'{int(x/1000)}k$'))
plt.show()
```
![Visualization of Median Salaries for Top 6 Data Roles in the US](Python_Data_Project/Images/salary_analysis.png)
*Boxplots visualizing the median salaries for each of the Top 6 highest in-demand data roles in the US*

### Insights

The chart presents the distribution of average yearly salaries for various data jobs in the US, including both senior and non-senior roles.

#### Key Observations:

1. **Senior Data Scientist**:
   - **Salary Range**: The highest among all roles, with most salaries falling between approximately $125k and $190k.
   - **Outliers**: Some salaries exceed $250k, indicating lucrative opportunities for highly experienced professionals.

2. **Senior Data Engineer**:
   - **Salary Range**: Second highest, with most salaries ranging from around $120k to $180k.
   - **Outliers**: A few salaries go beyond $200k, suggesting high earning potential in specialized positions.

3. **Data Scientist**:
   - **Salary Range**: Generally between $90k and $150k.
   - **Outliers**: Some salaries reach up to $200k, reflecting the value of advanced analytical skills and expertise.

4. **Data Engineer**:
   - **Salary Range**: Similar to Data Scientists, typically between $90k and $140k.
   - **Outliers**: Some salaries approach $200k, indicating demand for skills in data infrastructure and engineering.

5. **Senior Data Analyst**:
   - **Salary Range**: Between $80k and $130k.
   - **Outliers**: A few salaries surpass $150k, highlighting opportunities for experienced analysts in leadership roles.

6. **Data Analyst**:
   - **Salary Range**: The lowest among the roles, generally between $50k and $90k.
   - **Outliers**: Some salaries exceed $100k, showing potential for growth and specialization.

### Key Analysis:

1. **Career Growth and Salary Progression**:
   - There is a clear progression in salary from non-senior to senior roles across all job titles. 
   - Investing in skill development and gaining experience can lead to significant salary increases.

2. **Demand for Specialized Skills**:
   - The presence of high outliers, especially in senior roles, indicates a strong demand for specialized skills and extensive experience.
   - Continuous learning and skill enhancement in tools like SQL, Python, and cloud technologies can improve job prospects and salary potential.

3. **Role Comparison**:
   - Senior roles (Senior Data Scientist, Senior Data Engineer) command higher salaries compared to their non-senior counterparts.
   - Among non-senior roles, Data Scientists and Data Engineers tend to earn more than Data Analysts, reflecting the complexity and technical requirements of these positions.

4. **Advancing from Data Analyst to Data Engineer or Data Scientist**:
   - Data Analysts looking to significantly increase their earning potential might benefit from transitioning to Data Engineer or Data Scientist roles rather than advancing to Senior Data Analyst.
   - The salary range for Data Engineers and Data Scientists is higher, with greater upward mobility into senior positions.
   - Acquiring additional skills in programming, machine learning, and data engineering can facilitate this transition and lead to more lucrative career opportunities.

5. **Market Value of Data Roles**:
   - The data highlights the lucrative nature of data-related careers, particularly as one advances to senior positions.
   - Staying updated with industry trends and in-demand skills is crucial for career advancement and maximizing earning potential.

### Summary

Understanding the salary distribution and the factors influencing it can guide professionals in making informed career decisions. For Data Analysts, focusing on acquiring key skills and gaining experience in data science or data engineering can significantly enhance career stability and progression. This strategic move can lead to higher salaries and more robust career opportunities in the competitive field of data science and engineering.

### Data Visualizaitiona and Results cont'd:
```python
fig, ax = plt.subplots(2, 1)  

sns.set_theme(style='ticks')

# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_data_top_pay, x='median', y=df_data_top_pay.index, hue='median', ax=ax[0], palette='dark:b_r')
ax[0].legend().remove()
# original code:
# df_data_top_pay[::-1].plot(kind='barh', y='median', ax=ax[0], legend=False) 
ax[0].set_title('Top 10 Highest Paid Skills for Entry Level Data Roles')
ax[0].set_ylabel('')
ax[0].set_xlabel('')
ax[0].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))


# Top 10 Most In-Demand Skills for Data Analystsr')
sns.barplot(data=df_data_top_count, x='median', y=df_data_top_count.index, hue='median', ax=ax[1], palette='light:b')
ax[1].legend().remove()
# original code:
# df_data_top_count[::-1].plot(kind='barh', y='median', ax=ax[1], legend=False)
ax[1].set_title('Top 10 Most In-Demand Skills for Entry Level Data Roles')
ax[1].set_ylabel('')
ax[1].set_xlabel('Median Salary (USD)')
ax[1].set_xlim(ax[0].get_xlim())  # Set the same x-axis limits as the first plot
ax[1].xaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'${int(x/1000)}K'))

plt.tight_layout()
plt.show()
```

![Visualization of Skills with the Highest Median Salaries And Highest Demand](Python_Data_Project/Images/skills_demand_salary.png)
*Bar charts showing the top highest paid technical skills (top) as well as the top most requested skills in job postings (bottom) in the US across Data Analysts, Data Scientists and Data Engineers*

### Insights

#### Key Observations:

**Top 10 Highest Paid Skills for Entry-Level Data Roles:**

1. **MongoDB**: Highest median salary, approaching $200K.
2. **Unreal Engine**: Strong demand, with salaries around $175K.
3. **Ruby on Rails**: High median salary, indicating robust demand for web development skills.
4. **Solidity**: Reflects the lucrative blockchain technology market.
5. **Elixir**: High earnings potential, especially in back-end development.
6. **Hugging Face**: Significant salary, highlighting demand for natural language processing expertise.
7. **dplyr**: Indicates valuable data manipulation skills within the R programming language.
8. **Objective-C**: Still relevant and high-paying in mobile app development.
9. **Theano**: Reflects demand for expertise in deep learning frameworks.
10. **Atlassian**: High salary potential, suggesting value in project management and software development tools.

**Top 10 Most In-Demand Skills for Entry-Level Data Roles:**

1. **Apache Spark**: Highly sought after for big data processing.
2. **AWS (Amazon Web Services)**: Crucial for cloud computing and infrastructure.
3. **Python**: Essential for a wide range of data tasks and highly demanded.
4. **Azure**: Reflects the importance of Microsoft’s cloud platform.
5. **R**: Valuable for statistical analysis and data science.
6. **SQL**: Fundamental skill for data management and manipulation.
7. **Tableau**: Important for data visualization and business intelligence.
8. **SAS**: Indicates demand in industries relying on advanced analytics.
9. **Power BI**: Popular for business analytics and data visualization.
10. **Excel**: Still relevant and widely used for data analysis.

### Key Analysis:

1. **Salary vs. Demand**:
   - While some skills like MongoDB and Unreal Engine offer the highest median salaries, they are not listed among the most in-demand skills.
   - Skills like Python, AWS, and SQL, which appear on the most in-demand list, also offer competitive salaries, reflecting their broad utility across various roles.

2. **Strategic Skill Development**:
   - **High-Paying Skills**: Focusing on acquiring high-paying skills like MongoDB, Unreal Engine, and Ruby on Rails can significantly boost earning potential.
   - **In-Demand Skills**: Acquiring in-demand skills like Python, AWS, and Spark ensures robust job opportunities and career stability.

3. **Skill Overlap and Career Advancement**:
   - **For Data Analysts**: Enhancing skills in SQL, Tableau, and Excel, which are already relevant, can ease the transition to Data Engineer or Data Scientist roles.
   - **For Career Growth**: Learning high-paying skills like MongoDB and Solidity can open up advanced opportunities and lead to higher salaries.

4. **Industry Trends**:
   - The data indicates a growing demand for cloud computing skills (AWS, Azure), big data processing (Spark), and machine learning frameworks (Hugging Face, Theano).
   - Skills in traditional statistical tools (R, SAS) and data visualization (Tableau, Power BI) remain critical for data-driven decision-making roles.

### Summary:

For entry-level data professionals, a strategic blend of in-demand and high-paying skills can pave the way for robust career growth and lucrative opportunities. Balancing foundational skills like Python, SQL, and Excel with specialized expertise in areas like cloud computing, big data, and blockchain technology can provide a competitive edge in the dynamic job market. This approach not only ensures job security but also offers the potential for substantial salary advancements as professionals transition into more advanced data roles.