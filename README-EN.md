### Project Background

        With the rapid advancement of internet and communication technologies, the development and sharing of learning resources have taken on new dimensions. Online courses, live-streamed classes, and various e-learning platforms and applications have become increasingly prevalent. The COVID-19 pandemic has further highlighted the importance of online platforms as key venues for showcasing the achievements of "Internet Plus Education." Consequently, leveraging user and learning data from these platforms to provide precise course recommendations has emerged as a critical focus in online education. Based on available data, this project aims to devise comprehensive online course recommendation strategies to better serve platform users.

### Data Sources

        The data utilized in this project is sourced from publicly available datasets.

### Data Description

        There are three data tables: users.csv (user information table), study_information.csv (learning details table), and login.csv (login details table), as outlined in Tables 1, 2, and 3 respectively.

        Table 1: users.csv Field Description

| Field Name             | Description                 |
|:----------------------:|:---------------------------:|
| user_id                | User ID                     |
| registration_time      | Registration Time           |
| recently_logged        | Most Recent Visit Time      |
| learn_time             | Learning Duration (minutes) |
| number_of_classes_join | Number of Classes Joined    |
| number_of_classes_out  | Number of Classes Exited    |
| school                 | User's Affiliated School    |

        Table 2: study_information.csv Field Description

| Field Name       | Description            |
|:----------------:|:----------------------:|
| user_id          | User ID                |
| course_id        | Course ID              |
| course_join_time | Course Enrollment Time |
| learn_process    | Learning Progress      |
| price            | Course Price           |

 Table 3: login.csv Field Description 

| Field Name  | Description    |
|:-----------:|:--------------:|
| user_id     | User ID        |
| login_time  | Login Time     |
| login_place | Login Location |

# 

### Analysis  Approach

       **I. Data Preprocessing**

1. Understand the meaning of each field and perform necessary handling of missing values, duplicate values, etc.

2. Address the "--" values in the recently_logged field of the user information table.

**II. Platform User Activity Analysis**

1. Create heat maps of platform login frequencies across provinces and cities to analyze user distribution.

2. Plot bar charts of user login frequencies during workdays and non-workdays to identify peak activity periods.

3. Calculate the platform's user churn rate:
   
   Tend​ represents the end of the data observation window, and T<sub> i​ </sub>is the most recent visit time for user i. σ<sub> i​</sub>=T<sub> end</sub>​−T<sub> i</sub>​.  If σ<sub> i​</sub> exceeds 90 days, user i is considered a churned user.

4. Analyze platform user activity to provide recommendations for the online management of the education platform.

**III. Online Course Recommendation**

1. Based on user learning records, count the number of participants for each course, calculate course popularity, list the top 10 most popular courses, and plot a corresponding bar chart:
   
   The popularity of the i-th course, γ<sub>i</sub>​, is calculated as 
   
   $          \gamma_i = \frac{Q_i - Q_{\min}}{Q_{\max} - Q_{\min}}$
   
   where Q<sub>i</sub>​ is the number of participants for the i-th course, and Q<sub>max</sub> and Q<sub>min</sub>​ are the maximum and minimum number of participants across all courses, respectively.

2. Construct a user-course relationship table (binary matrix) based on users' course selections. Use an item-based collaborative filtering algorithm to calculate course similarities. Combine this with records of users' selected courses to recommend 3 courses for the top 5 users with the highest learning progress.
