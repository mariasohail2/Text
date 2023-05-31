Project Background

QAnon was first seen in October 2017, when an anonymous user put a series of posts on the message board 4chan signed off as "Q". This user claimed to have a "Q Clearance" level of US security clearance (Wendling, 2021).  Eventually, these messages gained notoriety, and became known as "Q drops" or "breadcrumbs", and were often written in cryptic language peppered with slogans, pledges, and pro-Trump themes (Wendling, 2021). Present day, these messages have evolved into a wide-ranging theory that claims that President Trump is waging a secret war against elite Satan-worshipping pedophiles, who are powerful names in government, business and media (Wendling, 2021). While this initially started off as a fringe movement, it has recently gained much momentum. This is evidenced with a December poll by NPR and Ipsos that showcases 17 percent of Americans believing the core falsehood of QAnon. Recently, this movement has also been attributed to spreading falsehood around the Covid-19 pandemic, the Black Lives Matter movement, and the 2020 American presidential election. 

In order to understand this phenomenon in greater detail, our project will analyze “breadcrumbs” left by Q, as well as tweets from Donald Trump in the same respective time window. In order to do this, our team will employ four types of analyses. These include :
Toxicity Analysis
Document similarity 
Sentiment analysis
Latent Dirichlet Allocation (LDA)
Entity Extraction

Data Sources and Pre-Processing

For this project, we had two primary data needs, posts from the QAnon leader, and tweets from Donald Trump. Their retrieval, and applied pre-processing are discussed below:

QAnon Posts

In order to retrieve QAnon posts, https://QAnon.pub/ was leveraged. This website has all of Q’s posts aggregated from 8kun, which is the successor of 4chan and 8chan, where QAnon posts initially appeared. In order to scrape data from this website, Selenium was used. Our team initially faced problems with the automatic scroll down feature of Selenium, as it was unresponsive towards this particular website. However, this was quickly solved by holding the “End” key for the remainder of the scraping period. Once we had our base dataset, any posts with the format “>>1234567” were extracted. This format signifies the involvement of  images, and to honor the text based scope of this project, we did not see these posts as fitting. In addition to this, our team wanted to ensure consistency of posts. In order to do this, some posts were removed manually; for example, any post containing only a single word was dropped. With all pre-processing complete, our team had a dataset of roughly 6000 QAnon posts.


Trump Tweets

Trump tweets were retrieved from https://www.thetrumparchive.com/. This data was already available in .CSV format. Therefore, scraping was not needed. For the purpose of this project, Trump data was limited to the same time period as all available QAnon posts: October 2017 to December 2020. In addition to this, retweets were eliminated from the subset to account for the computationally expensive nature of this project. With all pre-processing complete our team had a dataset of roughly 14,000 tweets from Donald Trump.

Text Analysis

For the purpose of this project, our team initially conducted a toxicity level analysis, and leveraged document similarity, sentiment analysis, Latent Dirichlet Allocation (LDA), and entity extraction for subsequent analysis. Respective methodology, details regarding APIs or algorithms used, and our findings through our analysis can be found below.

Toxicity Levels

In order to perform an analysis on Toxicity Levels between QAnon posts and tweets from Donald Trump, our team leveraged the Perspective API, and visualized observed trends from our findings. 

Perspective API Background

This is a free API accessible through Google Cloud Platform that uses Machine Learning to identify “toxic” comments, with the goal of enabling and hosting better online conversations through content moderation. The model itself scores a comment based on the following six parameters: 
Severe toxicity
Insult
Profanity
Identity attack
Threat
Sexually explicit

API Methodology

The Perspective API limits requests to one per second, and locks out users temporarily if this quota is exceeded. To accommodate this setting, our team constructed a loop that sends requests with 1.5 second intervals. This process took roughly 8 hours to be completed due to the amount of posts and comments involved. Our end result was a toxicity score for each QAnon post and Trump tweet, ranging between 0 and 1.




Findings and Visual Trends

In order to showcase results found in the toxicity level analysis,  average toxicity levels were calculated for each month from late 2017 to end of 2020. These findings are visualized in the graphs below. In addition to this, individual graphs for each year can be found in Appendix 1.0. Comparative graphs for each year between Trump and QAnon toxicity levels were also created. These can be found in Appendix 2.0. It is important to note that 2017 only has posts starting in October. This is due to the timeframe of when “Q” posts initially started to appear. In addition to this, there are no posts from “Q” between August and November 2019. This is due to three shootings taking place where shooters used the preceding 8chan to spread hateful manifestos (Bellingcat, 2021). As a result, no posts appeared during this time, until a transition to 8kun was facilitated in November (Bellingcat, 2021). 



More interestingly, these graphs communicate reactions to socio-political factors. For example, the year 2018 has the highest peaks between both QAnon posts and Trump tweets. In fact, in 2018 Robert Muller launched an independent investigation into Russia’s involvement within the Trump campaign (CNN, 2018). Many people were tried and convicted during this investigation including Paul Manafort, and George Papadopoulous (CNN, 2018). Therefore, the high toxicity levels evidenced in these graphs are very likely in reaction to this investigation. In addition to this, toxicity levels between Trump and QAnon posts can often be seen to mimic each other, with QAnon having more amplified results compared to Trump toxicity levels. These can be witnessed in 2018 and 2019, visualized in graphs below.


In some instances, the reverse was also witnessed. For example, in 2020 toxicity levels between Trump and QAnon can be seen to be having an inverse relationship. Interestingly, during this timeframe the severity of the Covid-19 pandemic was initially being realized. The decrease in toxicity from Trump can perhaps be explained from the tough diplomatic position he had to attend to, while he also subtly denied the pandemic, and also used incendiary language such as “China Virus”, and gas lighted the World Health Organization. We hypothesize that this can explain the decrease of toxicity levels from Trump. Similarly, the absence of this restriction and the politicization of mask wearing can explain the rise in toxicity from QAnon posts. Perhaps, most interestingly, the toxicity levels come back to mimicking each other towards the end of the year, in a decreasing fashion.



Document Similarity

The observed synchronization of toxicity levels between QAnon posts and Trump tweets lead us to explore the similarity between them. In order to conduct this analysis, four approaches were undertaken. Lastly, some interesting findings were discussed as well.

Filtering top 1000 toxic posts and tweets based on toxicity score

The 1000 most toxic posts and tweets were merged into one excel sheet, where text mining techniques were applied to clean the data. These included: removing stop words, lowercasing all text, removing any special characters, digits, and numbers not relevant to the string, and lastly removing trailing and leading spaces in the text. The data was then tokenized and lemmatized, and a bag of words was built by vectoring the texts. These cleaned posts and tweets were also merged together and the vocabulary of feature words was created. This was then split into two documents where one document contained QAnon posts and the other document contained Trump tweets. Cosine similarities were then calculated and documents with greater than 0.45 similarity were selected for further analysis (the similarity matrix can be observed in Appendix 3.0). Lastly, we extracted the indices shown in Appendix 3.0 for those similar documents and manually extracted the posts and tweets from the original data. Sample similar documents picked up from the original data can be observed below.



Similarity between posts and tweets during the initial Covid-19 pandemic news

Due to the interesting findings during the visualization phase of the toxicity level analysis, our team ventured into checking the  similarities between the posts and tweets in the date range between March 2020 to May 2020. As a result, our team took the top posts and tweets filtered for this particular date range from the original scraped data. This left us with 960 posts. In addition to this, a similar process to the one applied before was again applied in this section. Post processing, documents where the similarity threshold was greater than 0.40 were subsetted for an analysis. Indices and the similarity matrix can be evidenced in Appendix 4.0. Sample similar documents are displayed below.



Similarities between top posts and tweets during the first Trump impeachment

We also conducted a particular analysis to gain more insight into the similarities during the first Trump impeachment period. As a result, we filtered data from November 2019 to March 2020 between the QAnon posts and Trump tweets. Similarly to before, we applied the data pre-processing procedure. We then calculated document similarities, and subsetted the data to documents with similarity greater than 0.3. Lastly, we extracted the indices, and manually extracted those posts and tweets from the greater dataset. This left us with 600 posts and tweets. Indices and the similarity matrix can be observed in Appendix 5.0. Sample QAnon Posts and Trump tweets with a similarity greater than 0.30 from this timeframe can be seen below.



Similarities between top posts and tweets during the first Trump Impeachment with the maximum toxic scores

Lastly, we did an analysis similar to the one before, however this time accounting for the highest toxicity scores and the time period of Trump’s impeachment (from November 2019 to March 2020). These posts and tweets were then preprocessed, and similarity levels were calculated. Indices and the similarity matrix can be observed in Appendix 6.0. We then chose documents with a similarity of greater than 0.40 for further analysis. Sample posts can be viewed below. More examples are visible in Appendix 7.0.



Most Similar Documents Examples

Some overall notable examples from our analysis include.

Documents signaling “more things to come”.








Documents depicting nationalistic undertones and talking about election interference.


Documents talking about the withholding of information from the public


Documents shedding light on the Trump impeachment and negative sentiments towards Democrats


Cosine similarity also generated some random and not quite similar documents which were quite funny to observe



Sentiment Analysis

After finding the similarities between Trump tweets and QAnon posts, we also calculated the polarity scores for these similar documents using the Valence Aware Dictionary for sentiment reasoning method, in order to identify the positive and negative comments or tweets and understand what shapes their political views.





Sentiment Analysis of QAnon Documents Similar to Trump Tweets

There were four documents which had maximum similarities and for which we analyzed sentiments as well.

The first document illustrates that both Trump and QAnon depict positive sentiment as can be observed from the compound score and they both are referring to future events in terms of “more things to come”.
The second  document illustrates negative sentiment for both the QAnon and Trump tweets as they talk about election interference.
In the third document QAnon depicted negative sentiment where Trump’s tweets depicted positive sentiment where they are talking about withholding the information from the public.
In the last one, both depicted negative sentiment towards democrats and directed to Trump’s impeachment.

These observations are interesting, as although  the two post origins are referring to similar notions, they may be referenced in a similar or different tone.

These are exemplified below:

Funny Similarities and Sentiments

During our analysis, we stumbled upon some similarities that we found humorous. In one instance, Trump is talking about Pope John Paul II with a positive sentiment, and QAnon posts says “The war is real. He fights for you”. This was interpreted with a negative sentiment due to rhetoric such as “war” and “fight”. Similarly, in the second example, Trump expresses negative thoughts towards General motors, and QAnon also describes a negative sentiment. However the object is unknown in this case but it seemed as if QAnon expressed sentiments towards GM. 



LDA

For this project, LDA was undertaken with the goal of isolating topics from each source. We did this with aspirations of deriving an average toxicity score per topic. In order to perform this analysis, the following steps were taken:

Tokenization
Lemmatization
Stop words removal
Re-tokenization
Count Vectorization
Deleting any existing integers 

Through this process, 15 topics were extracted from each source, with 3000 iterations for the LDA algorithm. We made the decision to include URLs, as these could contain valuable information. We then extracted the top 30 words per topic, removing any resulting URL elements and stop words. Topics were then examined manually, which resulted in a “final set” of words that best represented each topic. A script was then run to extract any posts that contained three or more words associated with a topic. The toxicity scores for these posts were averaged, resulting in a “topic toxicity score”. 









Findings

The results of our analysis can be evidenced per source. Samples of the topics extracted from the QAnon dataset and their associated scores can be observed below.

Topic
Topic Number
Average Toxicity
Reduced Topic Words
clinton and sex trafficking
2
0.286
republican
child
democratic
sex
sexual
democrat
guilty
traffic
rise up patriots
12
0.247
god
stand
fight
patriots
people
together
evil
united
fake news controlling the narrative
3
0.240
control
news
people
fake
media
narrative
attack
potus
Iran and Saddam Hussein funding
7
0.232
potus
us
relevant
control
iran
money
hussein
fund
Red October
8
0.231
people
right
world
know
power
public
change
red
Comey, Epstein, news stations
1
0.204
treason
believe
comey
epstein
coincidences
cnn
barlow
snowden
watch for messages (in the news, etc)
13
0.189
think
know
potus
news
coincidence
future
anons
watch
Virus and the election
11
0.187
vote
election
china
biden
covid
voter
death
virus
Surveillance organizations / foreign security threats
5
0.170
fisa
fbi
russia
intel
sec
uk
nsa
hussein
war, government, and violence
0
0.168
government
control
person
freedom
military
antifa
violence
warfare
foxnews, conspiracies
14
0.164
news
trump
politics
QAnon
foxnews
conspiracy
story
nytimes
Comey's firing
4
0.162
fired
fbi
director
clinton
justice
comey
attorney
counsel
Mueller investigation
6
0.149
mueller
sessions
house
fbi
huber
potus
doj
evidence
Twitter and youtube URLs.
10
0.120
twitter
status
youtube
realdonaldtrump
hillaryclinton
mobile
patriot
saracarterdc
China controlling the central bank/fb/google
9
0.113
bank
central
china
fb
google
access
target
national







Similarly, a sample of the topics extracted from the Trump’s tweets dataset and their associated scores can be observed below.

Topic
Topic Number
Average Toxicity
Reduced Topic Words
The do-nothing democrats, impeachment
4
0.399
democrats
nothing
impeachment
president
call
nancy
never
pelosi
Fox News is awesome
6
0.388
house
white
foxnews
interview
congratulations
conference
secretary
foxandfriends
The wicked fake news
1
0.330
fake
news
media
report
cnn
bad
know
story
Sleepy Joe and the election
5
0.216
biden
joe
vote
win
election
sleepy
state
ballot
Build the wall / supreme court
13
0.192
border
wall
security
court
immigration
crime
work
mexico
Other countries screwing over US
3
0.187
china
trade
pay
dollars
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




