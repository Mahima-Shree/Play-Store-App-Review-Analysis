# Play Store App Review Analysis

**INTRODUCTION**

Application distribution platform, for example, Play Store gets overwhelmed with millions of new applications being launched on the platform regularly. Lots of designers and developers work on it to make an app successful on the Play Store. In this highly competitive world, it is an immense challenge for a developer to know whether they are focusing on the right path to make their app successful on the platform. To launch themselves successfully and create an identity for themselves in this oversaturated market, they need to ensure that majority of the essential factors are incorporated while designing and developing an app that would play an important role in customer's decision-making process. However, the lack of a clear understanding of the inner working and dynamic of popular app markets impacts both the developers and users.

**OBJECTIVE**

The main objective of this exploratory data analysis project is to understand customer demands better and thus help developers to popularize their product on the Play Store. One day on the evening of 8th August 2021, AlmaBetter plans to debut into the Android application by developing a mobile application on the play store platoform. They approaced us "Data Diggers" to help with building their technical know how about building a good android application. They wanted us to study current trends and insights of Play Store. We were given with two datasets i.e., Play Store & User Reviews. Before jumping into the data's provided, let me first explain you about the EDA analysis.

**PROBLEM STATEMENTS**

1.What are the top categories on Play Store?
2.Are majority of the apps Paid or Free?
3.How importance is the rating of the application?
4.Which categories from the audience should the app be based on?
5.Which category has the most no. of installations?
6.How does the count of apps varies by Genres?
7.How does the last update has an effect on the rating?
8.How are ratings affected when the app is a paid one?
9.How are reviews and ratings co-related?
10.Lets us discuss the sentiment subjectivity.
11.Is subjectivity and polarity proportional to each other?
12.What is the percentage of review sentiments?
13.How is sentiment polarity varying for paid and free apps?
14.What is Exploratory Data Analysis?

Exploratory data analysis (EDA) is used by data scientists to analyze and investigate data sets for patterns, and anomalies (outliers), and form hypotheses based on our understanding of the dataset and summarize their main characteristics, often employing data visualization methods. It is an important step in any Data Analysis or Data Science project. It helps determine how best to manipulate data sources to get the answers you need. EDA involves generating summary statistics for numerical data in the dataset and creating various graphical representations to understand the data better and make it more attractive and appealing.

The following are the various steps involved in the EDA process:

1.Problem Statement - We shall brainstorm and understand the given data set. We shall study the attributes present in it and try to do a philosophical analysis about their meaning and importance for this problem.
2.Hypothesis - Upon studying the attributes present in the data base, we shall develop some basic hypothesis on which we can work and play with the data to look for the varied results which we can get out of it.
3.Univariate Analysis - It is the simplest form of analyzing the data. In this we would initially pick up a single attribute and study it in and out. It doesn't deal with any sort of co-relation and it's major purpose is to describe. It takes data, summarizes that data and finds patterns in the data.
4.Bivariate Analysis - This analysis is related to cause and the relationship between the two attributes. We will try to understand the dependency of attributes on each other.
5.Multivariate Analysis - This is done when more than two variables have to be analyzed simultaneously.
6.Data Cleaning - We shall clean the dataset and handle the missing data, outliers and categorical variables.
7.Testing Hypothesis - We shall check if our data meets the assumptions required by most of the multivariate techniques.

DATA EXPLORATION, CLEANING AND INSIGHTS

play_store dataframe has 10841 rows and 13 columns. The 13 columns are identified as below:

1.App - It tells us about the name of the application.
2.Category - It tells us about the category to which an application belongs.
3.Rating - It tells us about the ratings given by the users for a specific application.
4.Reviews - It tells us about the total number of users who have given a review for the application.
5.Size - It tells us about the size being occupied the application on the mobile phone.
6.Installs - It tells us about the total number of installs/downloads for an application.
7.Type - It tells us whether the application is free or a paid one.
8.Price - It tells us about the price of the application.
9.Content_Rating - It tells us about the target audience for the application.
10.Genres - It tells us about the various other categories to which an application can belong.
11.Last_Updated - It tells us about the when the application was updated.
12.Current_Ver - It tells us about the current version of the application.
13.Android_Ver - It tells us about the android version which can support the application on its platform.

user_reviews dataframe has 64295 rows and 5 columns. The 5 columns are identified as follows:

1.App - It tells us about the name of the application.
2.Translated_Review - It tells us about what the users feedback is about the application.
3.Sentiment - It tells us about a view or opinion of the user w.r.t. the application.
4.Sentiment_Polarity - Sentiment polarity for an element defines the orientation of the expressed sentiment, i.e., it determines if the text expresses the positive, negative or neutral sentiment of the user about the application.
5.Sentiment_Subjectivity - It refers to the text that contains text which is usually expressed by a human having typical moods, emotions, and feelings. Mostly it is a public opinion and not a factual information.

Data Cleaning - Univariate & Bivariate Analysis

The number of null values in User-review dataframe are:

1.Translated_Review has 26868 null values which contributes 41.79% of the data.
2.Sentiment has 26863 null values which contributes 41.78% of the data.
3.Sentiment_Polarity has 26863 null values which contributes 41.78% of the data.
4.Sentiment_Subjectivity has 26863 null values which contributes 41.78% of the data.

Note1: 49% of NaN found in 4 features of user-review dataset hence we have removed all the NaN values from the user_review data frame.

The number of null values in play_store dataframe are:

1.Rating has 1474 null values which contributes 13.60% of the data.
2.Type has 1 null value which contributes 0.01% of the data.
3.Content_Rating has 1 null value which contributes 0.01% of the data.
4.Current_Ver has 8 null values which contributes 0.07% of the data.
5.Android_Ver has 3 null values which contributes 0.03% of the data.

OUR HYPOTHESIS:

Hypothesis_1:

We cannot simply drop these NaN values of Rating Column. So in order to get sentiment or translated review info for the apps from the user_review DF so that we can fill these NaN values based a logic based derivation. Thus, we need to merge these two DF's so that we get Common Apps between between them and can compare.

Hypothesis_1 conclusion:

We don't have infomation of sentiment of the Apps to fill the NaN values for the remaining apps from the merged DF.

Hypothesis_2:

Let us check whether do we have rating of Apps within the PlayStore DF.

Hypothesis_2 conclusion:

we found that even with this hypothesis we dont get information needed to fill NaN of the Rating.

Note2: Since both Hypothesis did not get us the information about Filling NaN values of Rating. We shall proceed with dropping these from the play_store DF.

**Data Cleaning – Univariate Analysis** (Play Store Data Set)

Findings • Reviews column was converted to a numeric type. • Size column had ‘M’, ‘k’ & ‘Varies with device’ which were all converted to a numeric variable. • Installs column has ‘+’ & ‘,’ characters present in it, which were removed, and then the column was converted to a numeric type. • Type column has only two strings i.e., Free & Paid which were relevant and retained as it is. • Price column had ‘$’ symbol present, which was removed and then the column was converted to a numeric type. • Content_Rating column has relevant variables present in it and thus were retained as it is. • Genres column also had relevant variables present in it and thus were retained as it is. • Last_Updated column has the dates in string format, these were converted to datetime format. • Current_Ver column refers to the latest version of the app and it had all relevant data in it, so it was retained. 8 null values were present, which were removed.

Data Cleaning – Univariate Analysis (User Reviews Data Set) Findings • 42% of the Translated_Review, Sentiment, Sentiment_Polarity & Sentiment_Subjectivity has null values and we had dropped all of these values, as they were of no value to the analysis.

**Data Cleaning – Bivariate Analysis**

Findings • We studied the heatmaps of both the data sets to ensure that we are not ignoring any important and relevant data and it’s dependency on the each other which would help us in our exploratory analysis.

Data Cleaning – Duplicates

Findings • Now that we have done our important analysis i.e., Univariate and Bivariate analysis. We shall now check for the duplicates present in the given play store data set and remove them. • A total of 1049 duplicates was found to be present in the play store data set. • We thus, then decided to drop these, as all the values in each column were repetitive in nature.

**EDA INSIGHTS AND CONCLUSION:**

• In this project of analyzing play store applications, we have worked on several parameters which would help AlmaBetter to do well in launching their apps on the play store. • In the initial phase, we focused more on the problem statements and data cleaning, in order to ensure that we give them the best results out of our analysis. • AlmaBetter needs to focus more on : • Developing apps related to the least categories as they are not explored much. Like events and beauty. • Most of the apps are Free, so focusing on free app is more important. • Focusing more on content available for Everyone will increase the chances of getting the highest installs. • They need to focus on updating their apps regularly, so that it will attract more users. • They need to keep in mind that the sentiments of the user keep varying as they keep using the app, so they should focus more on users needs and features.
