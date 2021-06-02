
## Udacity Data Visualization Nanodegree Capstone Project

![Photo by [Kat Jayne](https://www.pexels.com/@katlovessteve?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from [Pexels](https://www.pexels.com/photo/adult-alone-black-and-white-blur-568021/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)](https://cdn-images-1.medium.com/max/2560/1*2g_2pXeq8rfXCimSCKrmxQ.jpeg)

This post is the capstone project of Udacity Data Visualization Nanodegree. Its main goal is to describe how I’ve improved an existing data visualization from [Makeover Monday](https://www.makeovermonday.co.uk/) using everything that I’ve learned throughout the course.

The process of working on the project consisted of a series of tasks which I used as subheadings of the post.

## Step 1: Scope the Project and Gather Data

For a start, I checked datasets used for Makeover Monday data challenges in 2020. Since I’m deeply interested in a movement for women’s rights, gender equality, and justice, my attention was immediately caught by the week 10 data challenge. It’s based on the [data .world’s](https://data.world/) dataset and visualization [Violence Against Women & Girls — perceptions in African, Asian, and South American countries](https://data.world/makeovermonday/2020w10). The original data visualization is [here](https://public.tableau.com/profile/operation.fistula6589#!/vizhome/Internationaldayfortheeliminationofviolenceagainstwomen/Violenceagainstwomen); the dataset with all background information and data dictionary can be downloaded [here](https://data.world/makeovermonday/2020w10).

## Step 2: Explore and Assess the Data

The main variable (called *Value*) in the original dataset is the percentage of people who agree that a husband is justified in hitting or beating his wife under six specific circumstances:

* if she burns the food;

* if she argues with him;

* if she goes out without telling him;

* if she neglects the children;

* if she refuses to have sex with him;

* for at least one specific reason.

The values of the main variable are represented for 70 countries in Africa, Asia, Europe, and The Caribbean region. These values are grouped by respondent’s gender (female or male) and 15 demographics segments:

* marital status (married or living together, never married, widowed/divorced/separated);

* education level (no education, primary, secondary, higher);

* employment status (employed for cash, employed for kind, unemployed);

* residence type (rural, urban)

* age (15–24; 25–34; 35–49).

So we have 12600 combinations of all these parameters. Each of them is the dataset record that can be interpreted as follows: *47,6% of men with primary education in Azerbaijan agree that a husband is justified in hitting or beating his wife if she neglects the children…*

![](https://cdn-images-1.medium.com/max/3200/0*Au_tFAXEfNf6V4n-)

…or *15,6% of women aged 35–49 in Bangladesh agree that a husband is justified in hitting or beating his wife if she goes out without telling him.*

![](https://cdn-images-1.medium.com/max/3200/0*2IxPwGy_gqEqil_f)

Each record also contains the date when the survey was conducted.

The main goal of this step is to identify any limitations and biases in data collection, processing, and insights.

The surveys underlying the dataset were conducted by [The Demographic and Health Surveys (DHS) Program](https://dhsprogram.com/), which has provided technical assistance to more than 300 demographic and health surveys in over 90 countries for more than 35 years. So they design and implement surveys on a high level of competence, working together with government institutions and NGOs and training survey field staff in each country.

After reviewing several DHS reports, I believe that they can collect data avoiding any **selection**, **response**, or **survivorship biases**:

* they work with large nationally-representative samples (usually between 5,000 and 30,000 systematically selected households);

* the questionnaires don’t contain any leading questions, and trained interviewers don’t force respondents to give socially desirable answers;

* before producing final datasets, trained data-processing personnel process collected information and construct accurate summary variables;

* trained data-processing personnel can handle **missing variables** (another type on data collection biases) and any **data processing biases** like **outliers** and **missingness** or unusual **distribution**.

As for **data insight biases**, I see the only one potential weakness: there can be other features affecting the number of people who agree that husbands are allowed to beat their wives. For example, after comparing how many people justify violence against women in each demographic segment, we concluded that *education is a key* since the lowest percentage of people who agree that a husband is justified in hitting or beating his wife are in the group **Education — Higher**.

![](https://cdn-images-1.medium.com/max/3200/0*NnpPYNr5sBWJtxfO)

But what if there is another variable that affects people’s attitudes toward violence against women and also is a reason to get or not higher education like belonging to a particular social or ethnic group or income level? In terms of data insight biases, this absent feature is called a **confounding variable**.

However, considering DHS Program specialists as high-level professionals, I’m sure that they are able to identify all of the possible confounding variables in their surveys and understand whether they might affect the results since there are several methods and techniques that researchers can use to eliminate the influence of confounding variables.

The next question is, what limitations have I found exploring and assessing the data?

First of all, there are 1413 null values in the dataset. 26 countries don’t have a percentage of people who justify violence against women (column *Value*) for some demographic segments. For example, there are no summary results for never married people in Afghanistan and Pakistan or women with higher education in Sao Tome and Principe. It means there weren’t people from these groups in the samples. There are also no summary results for the particular circumstances as *if she refuses to have sex with him* in Jordan, which means this question was absent in the questionnaire for these countries. And finally, 12 сountries don’t have any results for men, so we can conclude that in these countries only women have participated in the surveys.

What does the absence of these values mean in terms of limitations? Well, we cannot directly compare all countries by all demographic parameters, including gender. Still, we can ignore these missing data if we base our conclusions on the average of all summary results.

All the surveys underlying the dataset were conducted in different years in 2000–2018: starting with Turkmenistan in 2000 and finishing with Guinea and Mali in 2018. However, there is no real timeline in the data since only the countries where the surveys were conducted were changing over time, not the people’s survey responses. So we cannot analyze how the percentage of people justifying violence against women was changing over time, and it’s another limitation.

Since we have data only from 70 countries that don’t represent different parts of the world evenly, we cannot compare people’s attitudes to violence against women at a higher level of geographical generalization than countries, i.e. at the world regions level.

## **Step 3: Define the Type and Purpose of Data Visualization**

My next step after assessing and exploring the data and analyzing possible biases and limitations was to find out how the [original data visualization](https://public.tableau.com/profile/operation.fistula6589#!/vizhome/Internationaldayfortheeliminationofviolenceagainstwomen/Violenceagainstwomen) could be improved.

![](https://cdn-images-1.medium.com/max/3200/0*PHwX31fN23755jPb)

The author of the visualization chose Tableau and created an interactive dashboard. Its purpose is to demonstrate that education is the main key to changing people’s attitudes to violence against women based on examples of only African countries.

The dashboard consists of several text blocks and three interactive charts. Let’s look at all the blocks and charts one by one.

The top text block contains the title *Operation Fistula* and a description of the research’s main conclusion. The title is clickable and leads to the [website](https://opfistula.org/) with the same name. This title was used because the dashboard was created within the [Viz5](https://opfistula.org/visualize-gender-equality/), the data visualization project launched by non-profit organization Operation Fistula to raise awareness of gender inequality, particularly violence against women and girls.

The next block contains three columns with the text helping users get the problem, the purpose of the survey, underlying the data, and the analysis’s conclusions.

Two remaining text blocks are used to say a little bit more about the main research conclusions and provide a legend for two of the charts.

Two of the three graphs show a percentage of people approving domestic violence against women in some circumstances. One chart is a bar chart where bars represented agreement rates in percentage for each country by length, colour, and number (the longer and darker the bar, the higher the percentage). The countries are sorted by agreement rates, and there are no tools to sort them in other ways like alphabetically or by survey year. The second chart duplicates the bar chart information on the map.

The third graph is a bar chart that demonstrates the agreement rate by every question, every demographics segment and gender. Gender is represented by a colour: grey for men and purple for women. These colours are also used in the text blocks to highlight related words and statements. By default, the numbers on the chart are aggregated for all countries, but users can get the information for a particular country, selecting it on the left bar chart or the map.

I consider the dashboard quite informative and precise; however, I cannot say that it’s easy to get the main dashboard’s message from the visualization. To determine which demographic segment percentage of people who justify domestic violence is the lowest, users have to compare dozens of bars in the right bar chart switching between five different panels. However, the second important finding, that a higher proportion of women than men think that violence against them can be justified, the same bar chart demonstrates clearly enough.

Based on the dataset and considering the possible biases and limitations, I’ve chosen to create a dashboard as well and kept the main purpose of the original data visualization: to show that educated people are less likely to approve violence against women.

The other significant changes made were not to narrow my focus to only African countries and use a different approach to compare the agreement rate by demographic groups. Firstly, I discarded gender-specific segmentation since to show the difference in the women’s and men’s attitudes to domestic violence is not the purpose of my dashboard. Secondly, I decided not to combine demographic segments with descriptions of circumstances when violence can be justified to avoid over-segmentation.

So, what information users will be able to get from the new dashboard?

* List of the countries where surveys were conducted; for each country — survey year and percentage of people justified a husband’s violence against his wife; the list can be sorted by the agreement rate, country names and survey year.

* People from what demographic segment are less likely to approve domestic violence (with filtering by countries).

* Which specific circumstances respondents consider justifying domestic violence more/less (with filtering by countries).

## Step 4: Complete the Dashboard

Now it’s time to demonstrate the new dashboard and explain why it improves the original data visualization.

![](https://cdn-images-1.medium.com/max/5996/1*-ugoF9G9rSbCDDfFKMjXTA.png)

Click [here](https://public.tableau.com/views/UDACITY_DVND_Capstone_LiudmilaSemenova/ViolenceAgainstWomen?:language=en&:display_count=y&:origin=viz_share_link) to see the new dashboard on Tableau Public.

As anybody can see, the new dashboard doesn’t differ dramatically from the original one. Still, there are some things that I improved and made the visualization better.

### **The dashboard title**

I’ve kept the main title on the same block since it’s the best place to catch a user’s attention. However, I’ve replaced the title from *Operation Fistula* to *Violence Against Women*, which made the subject of the analysis more clear.

### **The dashboard subtitle**

I’ve added the subtitle *should never be justified* to bring some emotional context and adjust the user’s perception.

### **The annotation and supportive text**

I’ve combined the survey description and conclusion in one place. The conclusion now is short, highlighted, and straightforward. I’ve added the quote from the [UN website](https://www.un.org/en/events/endviolenceday/) to emphasize the emotions related to the problem of domestic violence.

### **Sorting capabilities**

On the new dashboard, the user can sort the left bar chart *Level of Agreement by Countries* in any way: by country, by year, by the percentage of people who approve domestic violence.

### **Improved clarity**

The top-right graph Level of *Agreement by Demographic Segments* now conveys the main conclusion of the dashboard very clear: one cursory look at the bar chart is enough to identify a demographic segment with the lowest percentage of people justified violence against women.

I’ve created a separate graph with survey results distributed by survey questions *Level of Agreement by Questions*. This treemap allows users to get a detailed picture of respondents’ attitudes to specific circumstances when violence against women can be justified.

The separation of the results lets the audience avoid getting trapped in details and see the whole picture.

### **Tooltips**

I’ve improved the tooltips of all the graphs, made them more informative.

### **Call to action**

The new dashboard has an important part, which lets the users convert their emotions, their outrage over domestic violence to something productive such as donating to the *UN Trust Fund to End Violence against Women* or helping children from developing countries get an education.

### **Data provider and author**

The new dashboard has information about the data source and the author.

### **Colour palette**

The graphs’ new colour palette is sequential (from light-blue to dark-blue through shadows of turquoise): the longer the bar or the bigger the area, the darker their colour and vice versa. Since bars and areas reflect the agreement rate and dark colours are perceived as more negative, the colour palette serves as an additional source of user’s insights.

### **Polishing**

Checking the dashboard functionality, I found out some inconsistency in the Timor-Leste’s results. It turned out to be the only country where people with higher education approve domestic violence more than less educated people.

![](https://cdn-images-1.medium.com/max/2988/0*J_lOnp46MBIu6oVA)

Suspecting that it can be a data processing error, I spent a lot of time trying to get raw survey data from this country, but unfortunately, I’ve failed. I even requested to download the Timor-Leste survey dataset from [The DHS Program](https://dhsprogram.com/) database but got refused. So I decided to exclude this country from the dashboard.

## Final Thoughts

In this blog post, I described the whole process of creating a new dashboard based on existing data visualization to improve it. Although the new dashboard inherited the basic concept of the original one, now it’s easier for the audience to explore the data and find their insights, not to mention that the data visualization’s main idea is much clearer.

This project allowed me to apply all my knowledge gained from the Data Visualization Nanodegree program into practice and became a terrific sum-up of my new skills.
