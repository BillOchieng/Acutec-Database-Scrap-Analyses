# Final Project

# Jacob B., Bill, Arina

## Report

Please answer the below questions using clear and meaningful language. No one-liners, please.

* Give an overview of the project (explanation of data, selected research questions and motivation for their selection)

This project focuses on analyzing a manufacturing dataset to improve production processes and reduce waste. The dataset contains extensive information about job operations, nonconformance incidents, workcenters, materials, and jobs. We aimed to answer several research questions to enhance operational efficiency and product quality. The motivation behind these questions was to reduce waste, improve product quality, and increase operational efficiency by identifying problem areas, optimizing processes, and focusing on the most common issues affecting production.

* Give an explanation of the database schema

The database schema consists of several interconnected tables, including 'joboperation,' 'nonconformance,' 'workcenter,' 'material,' and more. These tables store critical information about job operations, materials used, workcenters involved, nonconformance incidents, and various attributes associated with them. Relationships between tables, such as foreign keys, enable the linking of data points for analysis. For instance, the 'joboperation' table is linked to 'nonconformance' and 'workcenter' tables, allowing us to track job operations, identify issues, and pinpoint which workcenters are involved in faulty productions.

* Explain the overview of the constructed queries

We created a series of SQL queries to address the research questions effectively. These queries involved joining multiple tables, filtering data based on criteria, and calculating relevant statistics. For example, to answer Research Question 4a, we joined the 'joboperation' and 'nonconformance' tables to identify the workcenters involved in faulty productions.

* What conclusions from the executed queries did you find (including and visual graphs of your results)?

Based upon our queries, we can see that overall there is a huge need for addressing the __RED__ part issues within the company. __Research Question 2__ casts a light on the total costs of the orders that included a __RED__ part. Totaling over 221 million, this set the tone for the other findings. The __first research question__, showed the departments and individuals responsible for the most __RED__ parts. This information is invaluable to the company because it highlights the source of the issue being studied. This information will allow for the company to begin to address and evaluate the performance of these departments. This could lead to hiring more skill labor, training the labor to meet the standard, or overall upgrades to the department to deter. The __Third Research Question__ highlights the most frequent __RED__ part codes that occur in the manufacturing process. This too allows for the company to pinpoint errors that could give way to improved infrastructure or training. The final two research questions shed light on the time issues that occur along with other minute constraints that give more specific insights into other factors surrouding the __RED__ part dilemma. Overall, each of the queries are important for understanding where __RED__ parts origninate, the direct and indirect costs involved, and overall micro-level data for the company to have a starting position to fix the scrap level issues.

For the plot we decided to use 4c to show the trend.
The line plot illustrates the relationship between estimated setup hours for job operations and the frequency of 'RED' nonconformance incidents. Notably, job operations with an estimated setup time of around 0.25 hours exhibit a relatively high frequency of 'RED' incidents, while other setup time estimates have significantly lower incident frequencies.

This observation suggests that job operations with approximately 0.25 hours of setup time may be more susceptible to quality issues, leading to a higher incidence of 'RED' incidents. Possible explanations for this trend could include specific factors or processes associated with the 0.25-hour setup time that contribute to the higher incidence of nonconformance incidents.

(Did you remember to place your name at the top of this document?)
