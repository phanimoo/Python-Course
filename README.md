# The Analysis
## What are the most demanded skills for the top non-Senior level data roles in the US?

To identify the most in-demand skills for popular non-Senior level data roles, I filtered out the most popular positions and determined the top 5 skills for each. This analysis highlights the key job titles and their essential skills, helping me focus on the relevant skills for my targeted role.


To view my notebook with detailed steps, click here: [2_Skills_Demand.ipynb](Python_Data_Project/3_Project/2_Skills_Demand.ipynb)

### Data Visualization

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
### Results
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

By focusing on these common and role-specific skills, individuals can better prepare for various non-senior level data job titles.