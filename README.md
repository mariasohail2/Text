
make
deal
countries
money
Something something Obamagate
12
0.183
breitbartnews
thank
via
agree
promises
congratulations
nice
obamagate
The economy's doing great...
10
0.178
economy
great
ever
record
best
history
tax
jobs
Support the military / endorsements
11
0.169
endorsement
complete
strong
amendment
military
vets
crime
congressman
New books about Trump
0
0.167
trump
president
book
donald
new
great
mike
america
Crooked Hillary NO COLLUSION
9
0.156
hunt
witch
collusion
fbi
mueller
russia
hillary
campaign
Stay at home orders / police
8
0.138
state
law
help
federal
new
york
government
california
America is awesome, also god
2
0.134
today
american
great
honor
day
america
nation
god
MAGA and key election states
7
0.133
great
america
maga
make
florida
carolina
happy
rally
Iran China North Korea
14
0.065
president
meet
korea
north
iran
china
forward
minister













In addition to this, the below graphs also visualize the average toxicity calculated per topic. 


To elaborate on these findings, the most toxic topic among all the QAnon posts deals with the Clinton sex trafficking conspiracy. This is followed by topics related to fake news, Red October (the purge of Trump’s enemies), and appealing to American patriotism to take back the county. In comparison, the most toxic Trump topics include impeachment, fake news, and Fox News, with “Sleepy Joe” Biden receiving an honorable mention.

It is interesting to note that according to Perspective API, the average toxicity of the top three Trump topics exceeded that of QAnon’s content regarding the secret Clinton sex trafficking operation. In addition to this, both sources are similarly toxic when mentioning fake news and the election, and both are also less toxic when talking about the military and foreign security threats. This could allude to similar emotional responses to fake news and bipartisanship, while being conversely very careful when saying anything about the military and national security. These are strikingly similar nationalistic tendencies, very likely stemming from QAnon followers’ idolization of Trump. Trump has also just stopped short of endorsing the group by notably retweeting and mentioned many QAnon-affiliated Twitter accounts in his tweets, so for future analysis it would be interesting to include the retweets, time-permitting.  

Entity Extraction

The Spacy package was used for Named Entity Recognition. Out of the 5802 posts extracted from QAnon, 14,333 total entities were extracted. Giving an entity/post value of 2.47. The frequency of each entity was calculated for all QAnon posts. Similarly, the entity distributions were also extracted for Trump tweets. For the 24,060 tweets extracted, 60,371 entities were recognized. This gave an entity/post value of 2.50. 

Findings

Our entity extraction analysis on the QANON dataset showed ORG, PERSON, GPE and CARDINAL as more frequently classified entities. ORG is defined as companies, agencies or institutions, GPE is defined as cities or states and CARDINAL is numerals. This distribution of entities for QAnon posts can be seen below.

Similarly, to the QAnon posts, PERSON, ORG and GPE were the most frequently classified entities for Trump tweets. This similarity shows that these two post origins put the same emphasis on people, organizations and known locations. In the case of Trump tweets, however, people and organizations had more comparable mentions compared to QAnon, where the difference was more pronounced. This distribution of entities for Trump tweets can be seen below.


To elaborate on this analysis, we looked at the top 20 most common entities for both post origins. Some commonalities were observed, such as FBI, Democrat, Republican and China. This can be seen in the image below. 




 Trump					QAnon


We also amalgamated a list of the top 20 most frequently mentioned Person, Organization (ORG) and Geographical Entity (GPE). The findings for QAnon are evidenced below.

PERSON	ORG			GPE




Similarly, the same analysis for Trump’s tweets were performed, and the findings are evidenced below.

PERSON		ORG			GPE


Most interestingly, we saw that certain people like Clinton, Biden and Mueller were mentioned most frequently for both. Another noteworthy observation is that Conspiracy and Godspeed were classified as People. Although it is clear that these may be misclassified, it might shed light to the type of context these words were used in; for example, potentially in a more formal sense compared to everyday objects. Examples of how the SPACY package classified the are shown in the image below.

1)
2) 


In addition to this, FBI and CNN were also frequently mentioned. When looking from the lens of GPE specifically, both Trump and Qanon mentioned China, Russia and Iran. It was also evident that Trump Tweets were more likely to talk about internal states, whereas QAnon posts mentioned international countries more. This is interesting as there is evidence that the QAnon movement has begun to spread towards other countries such as the UK, as seen in the example below.


Lastly, we looked at which entities were most common among the two texts. There were 1141 common examples. Although it was telling to see the commonalities that were frequent in both texts such as FBI, Russia, China, Iran, it was also interesting to see subjects that were far more talked about in QAnon. For example, UK, SA, and MSM were subject to this phenomenon. While we hypothesize SA to signal South Africa, MSM refers to the “Main Stream Media”. These types of words can symbolize concepts that might not be as freely mentioned in Trump social media, but that are still gaining traction in the QAnon movement.

Count Decreasing on QAnon		Count Decreasing on Trump


We also examined the list of common entities intently and pulled out some interesting and somewhat concerning terms, such as Corrupt, Treason, Win and Vote. We believed words like these could be telling in terms of gaining insights on voting fraud. We counted the frequency of these words grouped by day, for both Trump Tweets and QAnon tweets. In Trump tweets, we could see a major jump in these words around December of 2019, which was a time when Representatives voted for the President to be impeached for abuse of power and obstruction of Congress. Increased numbers were also observed in December 2020, as a similar political situation was ongoing. This is visualized in the graph below.


We completed the same process for QAnon posts. Interestingly, the largest number of mentions for these types of posts were made around October of 2017, which was when the movement started. Please reference the graph below.



By merging the two datasets containing mention volume by dates, we were able to look at mentions simultaneously. There did not exist a significant correlation (-0.07) in this case. However, lack of correlation does not necessarily mean lack of causation or relationship between the two activities. There could be a delayed response between the two. Interestingly enough, as Trump’s mention of voter fraud related terms increases towards the end of 2020, QAnon posts did not see as much activity. This could point towards the fact brought up by many news articles that QAnon believers began to lose trust in the movement. Please reference the image below.


A similar analysis was performed for tweets mentioning Biden. In this case, the number of mentions per day for the two post origins were 72% correlated. This is seen in the image below, and it could further strengthen the growing evidence for Trump’s involvement and influence in QAnon activity. 



Lastly, we looked at the time series plot for mentions of Russia grouped by day. Here, a 17% correlation was observed. Judging from the shape of the plot, this could be due to a delayed reaction from QAnon users in response to Trump mentions or actions. Please reference the graph below.




Conclusion

Overall, our team enjoyed performing these many analyses. Some things that made this project truly enjoyable was the reflection of socio-political factors within the data. For example, the toxicity levels have often reflected politically tumultuous times. In addition to this, the LDA analysis also sheds light into the views held by this demographic. For example, it is notable that the military is spoken about in far less toxic fashion within QAnon circles, despite it holding negative sentiment for many people. It is also interesting to see trends such as toxicity levels being mimicked by Trump tweets and QAnon posts, often with QAnon amplifying the pattern of Trump’s. In other cases, when Trump is highly toxic, he outperforms QAnon with this metric. Overall, this has been a joyful practice, as our team has not only learned more about performing text based analytical techniques, but also been able to merge that with socio-political knowledge. Given the ever-increasing focus on unstructured data, learning how to use these analytics tools is invaluable.















Bibliography:

“The QAnon Timeline: Four Years, 5,000 Drops and Countless Failed Prophecies.” Bellingcat, 1 Feb. 2021, www.bellingcat.com/news/americas/2021/01/29/the-qanon-timeline/. 

Wendling, Mike. “QAnon: What Is It and Where Did It Come from?” BBC News, BBC, 6 Jan. 2021, www.bbc.com/news/53498434. 

“What 2018 Looked like for the Mueller Investigation.” CNN, Cable News Network, www.cnn.com/interactive/2018/politics/mueller-investigation-year-in-review/index.html. 




