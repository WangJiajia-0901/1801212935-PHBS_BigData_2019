# How can be the popular upper in Bilibili?
## 1  Introduction 
We are in the information overloading age. Entertainment applications and e-commerce platforms provide users with a large number of products at all times, each user in the vast amount of information and even redundant information between the need to spend a lot of time to find their own goods, efficiency compared to the previous network is not developed, not only did not improve but reduced a lot, This is the information overload problem that prevails in the WEB 2.0 era. In order to solve this problem, many platforms have established personalized recommendation systems based on big data. Precision recommendations greatly improve user and product matching efficiency. **This is a matching solution from the user's view, and I want to rethink this issue from the perspective of content producers.** When will content producers release products can earn more attentions? <br>
To narrow this question down, I focus the self-media and take the Bilibili as the example. I want to find the right video releasing time for the Bilibili's uppers. Knowing that, the uppers can become popular quite soon. <br>
## 2  Big Data Problem Restatement and Properties
### 2.1 Problem Restatement
For upper, the best time release is the time period that gets the most attention. In order to describe the most attention-watching time, you can judge from the following indicators.  <br>

Indicators | Details
-|- 
Total online users of Bilibili | The more online users, the more people may watch this video 
Total online playback of Bilibili | More playback means the higher the viewing of new videos 
Time and number of times paused throughout the viewing process | More pauses mean that users are less attentive to viewing
Whether the user has long "silent viewing" | If the user does not do video clicks or other actions for a long time, the user can be considered to be using the video as a background and focusing on something else
Number of times a bombshell was written | The more bombshell means that users are more enthusastics in participating
Number of likes | The more likes, the more people focus on
Number of dislikes | The more dislikes, the more people have negative reaction
Number of comments | The more comments, the more people focus on
Content of bombshell | If the users leave the positive bombshell
Content of comments | If the users leave the postive comments

To get the preliminary feelings of how big the data will be, I crawled the number of plays and the number of people online on the Bilibili home page.<br>
![onlineusers](https://github.com/WangJiajia-0901/Big-Data-Analysis/blob/master/onlineusage.png)
![onlineusage](https://github.com/WangJiajia-0901/Big-Data-Analysis/blob/master/onlineusers.png)
From the figure we can conclude that online viewership varies widely from time to time, which means that release timing is quite an issue. <br>
### 2.3 3V properties
**The three V properties are quite obvious.** <br>
**Firstly, it is the volume.** According to the 2018 financial report of Bilibili, the average monthly active user reached a new high of 92.8 million in the fourth quarter of 2018, with 79.5 million mobile monthly live users, up 29% and 37% year-on-year, respectively. The average monthly number of paying subscribers rose 298 percent to 4.4 million in the past 12 months. Each user's movie-viewing behavior forms part of the data being analyzed. So the data is obviously massive.<br>
**Secondly, it is the variety.**  The user's watching behavior data is various. There is a variety of viewing data sources, users' viewing behavior is diverse, and all the actions of the user on this platform can become data. As the indicators mentioned before, the total online users, total online playback, time and number of times paused throughtout the viewing process, whether is "silent viewing", times of bombshell was writen, number of likes and dislikes and comments, the contents of bombshell and comments and so on. This data is mostly unstructured and a few are structured. For example, the texts of comments and bombshell are unstructured, but the total online users and play volumes are structured data.<br>
**Thirdly, it is velocity.** This comes from two aspects, the first is that the user's movie viewing behavior is real-time updated and dynamic, and the second is that the viewing behavior of different users constitutes the dynamic viewing state of the whole platform. <br>

## Workflow and Solution
### Reptile data and stored in a database
All the data need to be crawled and I have succuessfully crawled the online usage. I need to crawl all the indicators mentioned before. To better manage the data, directly store the data in the database.
### Establish model
First, use NLP to capture and analyze the sentiment of the users who are viewing this video by analyzing the text.<br>
Second, use random forest to establish the regression model between the above indicators and the certain video's playing volume.<br>
### Output Best Play Time
Different types of videos (game, food, makeup) will have different results, so for different segments of the video to get different best video release time.<br>
## Database expectations
I think MongoDB is proper for this problem with the following reasons.<br>
Suitable for real-time data processing of the website. It is ideal for real-time insertion, updates and queries, and has the replication and high scalability required for real-time data storage for websites. <br>
Due to its high performance, it is suitable as a cache layer for the information infrastructure. After the system restarts, the persistent cache layer built by it avoids overloading the underlying data source. <br>

