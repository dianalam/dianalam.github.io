---
layout: post
title: Investigating the Twitter Strategies of the 2016 Presidential Candidates
excerpt: It's election year and social media is playing a larger role than ever before in facilitating interaction between the 2016 presidential candidates and the general public. How are the candidates leveraging their Twitter presences at this stage in the race and how does this compare across party lines and amongst candidates? In this post I look at topics, sentiment, and various "call to action" strategies of Clinton, Cruz, Rubio, Sanders, and Trump.
---

*Looking for the interactive viz? Scroll down or [click here]({{ site.url }}/assets/tweets.html).*

A presidential election year is here again and with Super Tuesday come and gone, the primaries are in full swing. It's hard not to pull up the news without reading a story about how this year's candidates--on both parties--are changing the way they engage with each other and the general American public. Social media, and Twitter in particular, is one of the main venues through which the Republicans and Democrats are reaching out to potential voters, trying to reinforce or supplement the likability of their candidates through a more fluid communication tool.

We all know that a big part of Obama's win in 2008 was through pinpointing undecided voters through machine learning models and campaigning for their votes. This strategy will likely again play a significant role in 2016 and Twitter is one of the easiest and most accessible ways to engage directly with specific populations.

# The goal

This brings me to the question I wanted to address in my newest project--at this stage in the race, can we pinpoint the Twitter strategies of the various presidential candidates? What kind of topics are they focusing on and how are they talking about these topics? Are there specific "call to action" prompts in their tweets? How has this changed since the start of the race? I see this project as a start to a longer effort to track the role of Twitter in the election through November 2016 (more on that later in the post).

# The approach

I collected all the tweets of the five top-scoring presidential candidates (Democrats: Clinton and Sanders, GOP: Cruz, Rubio, and Trump -- sorry Carson and Kasich!) via the [Twitter REST API](https://dev.twitter.com/rest/public). Unfortunately the API only lets you capture the 3,200 most recent tweets by screen name, so I was only able to get tweets going about four to ten months back per candidate. I collected tweets twice over a two week period and wound up with about 16,000 tweets in total.

Twitter text, which is capped at 140 words and rife with slang, hashtags, and user mentions, is notoriously difficult for natural language processing. However, the field is well-researched/practiced, with many others having success using topic modeling/LDA, and I was able to gather a few tips and tricks to assist in making the language more interpretable.

First, I stripped hyperlinks and limited my analysis to tweets with more than 75 characters to throw out tweets that likely weren't sentences or that only had hashtags. I used a mix of unigrams, bigrams, and trigrams to maximize the interpretability of my features, and used a tf-idf vectorizer to better isolate key words. I also tried to aggregate the tweets by hashtag to form more sizable documents, but ultimately found that looking at the tweets on a per tweet basis was more interpretable, as there are some hashtags (such as #Trump2016) that may be included in nearly all of a candidates tweets, regardless of topic.

In the end, I found that these methods were sufficient in returning pretty interpretable results; I think I benefited greatly from looking at clean tweets--candidates' profiles are closely monitored and curated by their PR divisions, so I didn't have to sort through a lot of the Twitter muck that would be in general tweets.

I used LDA and a great library called [pyLDAvis](https://pyldavis.readthedocs.org/en/latest/) to conduct topic modeling and found that using five topics returned the best results. I also used a great package called [vaderSentiment](https://github.com/cjhutto/vaderSentiment) to perform sentiment analysis on the tweets. With more time, I would have liked to develop my own sentiment analysis model, but vader is designed specifically for social media text and I found that it performed pretty well, so I stuck with it. I also investigated the mood of each tweet--for example, if a tweet is indicative and expressing fact, or imperative and expressing "call to action" by looking at grammar/verb form using [pattern](https://pypi.python.org/pypi/Pattern).

# So what are the candidates talking about?

When I started this project, I was curious about whether or not we could see a trend away from what one would think are the traditional uses of Twitter--some self advertisement and reminders to vote, dotted with some reminders about policy platforms. In short, I would say that the topics that arose are still very familiar, but the differences between the parties and amongst candidates themselves is quite interesting in terms of who is more "traditional" and who is more varied in their Twitter content.

The tweets broke down into five main topics:

**Primaries:** No surprise here. Lots of talk about upcoming primaries, reminders to vote/caucus, and commentary on the candidate's win or loss.

**Media/self-promotion:** Again, no surprise. Media keywords were high in this category, with reminders to watch various segments/interviews on CNN, Fox, etc. This category is also where all the debate reminders fell in.

**Left-leaning policies, such as health care, education, womens' rights:** Here is where things become more interesting! Although this and the general policy topic below were quite close together, I thought it was fascinating how the LDA was able to split these two apart. This topic was focused primarily on what one might describe as more liberal or left-leaning policies -- i.e. more liberal candidates are likely to focus their policy platforms on these issues. This included health care, education, LGBT and women's rights, among other topics. As we'll see below, this category was really dominated by Clinton and Sanders.

**Economic and foreign policy:** This was the more general policy topic, which included approaches to ISIS and immigration as well as Wall Street. This was also where Sanders' "political revolution" coinage appeared.

**Retweets/1-on-1s/other:** I had a hard time naming this topic, because this is where the uniqueness of each candidate really came through (aside from the comparison of their engagement in the other four topics). Mostly this category featured a lot of retweets by candidates of positive things people have said about them--a tool for 1-on-1 engagement with their followers. For Clinton and Sanders, this category contained a lot of their Spanish language tweets, aimed at Latino voters. For Clinton, who we'll see had the greatest diversity of tweets across topics, this category contained even more policy topics, including tweets about gun control and the Second Amendment.

You can explore the topics in the interactive pyLDAvis below. The left hand side is an overview of the topics and their relative distance from one another (projected onto 2D plane using Jensen Shannon Divergence). Click on a topic and on the right you'll see the top terms in their topic by their probabilities. Adjusting the relevance slider on the upper right is akin to applying a tf-idf weighting to the terms--a lambda of one ranks them solely by their probability while a lambda of zero ranks them by their "lift," or the ratio of the probability of that term belonging in that topic compared to any of the other topics (i.e. the uniqueness of that term to the topic). A lambda of 0.5 - 0.6 is suggested. [Click here]({{ site.url }}/assets/tweets-pylda.html) to view this in full screen (sorry, not too mobile-friendly).

<iframe src="{{ site.url }}/assets/tweets-pylda.html" width="800" height="800" frameBorder="0"></iframe>

# Comparison between candidates

As I mentioned above, I found the comparison between candidates to be most fascinating. Some insights:

**Tweet volume:** Just by looking at tweet volume, we can see which candidates consider Twitter more important than others. As of the end of February 2016, Cruz was leading in terms of tweet volume, with almost 1,000 tweets logged in February alone. Sanders followed closely behind with about 800 tweets in February. Clinton and Trump had about 500 - 600 tweets, and Rubio severely lagged behind with only about 350 tweets. Rubio's Twitter presence was nearly nonexistent before April 2015.

All candidates, with the exception of Trump, have been ramping up their Twitter usage leading up to Super Tuesday. In keeping with the general surprise that Trump's campaign has incited, his Twitter presence actually peaked in October 2015, but has steadily decreased since then.

**Topic breakdown:** Across party lines--the Democratic candidates have a greater variety of tweets, notably with more tweets about econ/foreign policy and health/edu/women's rights than the GOP. For Cruz and Rubio, the majority of their tweets are focused on the primaries, which echoes their respective positions of trying to play catch up to Trump in the race for the GOP nomination. Trump's tweets, unsurprisingly, are primarily focused on media and self-promotion. Here we can see what's playing out in each party--the GOP is engaged in an internal battle, with Trump riding his lead and Cruz and Rubio focusing their energies on the primaries. None of the GOP candidates seem to be campaigning based on their policy positions, whereas Clinton and Sanders are running completely different campaigns, focusing on the differences in their policy platforms to gain voters.

**Sentiment:** Overall, candidate tweets had fairly neutral sentiment scores, which makes sense given the highly curated nature of their Twitter profiles. The retweets/other and primaries topics had the most positive sentiment ratings, which makes sense given the content. Another trend that stood out was sentiment around economic and foreign policy--on average over time, Clinton and Sanders had more positive sentiments when discussing this topic, while the GOP had more negative sentiment. This again, makes a lot of sense given the respective parties' stances on immigration (closing the borders vs. inclusivity) and the GOP backlash against the economic policies of the current administration. Finally, we can see that in February 2016, Trump's media/self-promotion tweets have a far lower sentiment than the other candidates, reflecting his strategy of tweeting negative statements about other candidates and politicians.

**Imperativeness/call to action:** Trump really stood out in this category, with over 50 percent of his tweets containing some sort of call to action or command to his followers. Not a surprise given what we've seen of his campaign strategy. I was surprised, however, that Cruz and Rubio aren't stepping this up, particularly in the primaries category.

You can explore the topics by candidate, mood, and sentiment over time in the interactive below. Or if you'd rather view it full screen, [click here]({{ site.url }}/assets/tweets.html). (Sorry, this definitely isn't mobile-friendly!).

<iframe src="{{ site.url }}/assets/tweets.html" width="810" height="900" frameBorder="0"></iframe>

## Future work

I'd like to continue tracking the ebbs and flows in Twitter as the race progresses, particularly behavior surrounding key events, such as preceding and following candidate drop outs, the nomination, and ultimately the election in November. With the full gamut of data, I think this could be a fascinating study of Twitter behavior over the lifecycle of a campaign.

Another application that I initially wanted to pursue but could not because of Twitter's API limitations is to investigate the general public's sentiment and response to a candidate's tweets, both on average and by location. This could really inform the impacts of specific social media campaign strategies. For now, this idea might be difficult to implement since Twitter data collection is quite cumbersome in large quantities, specifically when looking for geotagged information, but could be very valuable. I'll keep thinking on an approach to get around it.

Finally--as I mentioned above, I didn't get a chance to develop my own sentiment analysis algorithm tailored to these tweets. While the model was able to capture Trump's comparatively less positive sentiment, it still ranked his tweets as generally neutral. I'm guessing the model wasn't able to capture a lot of the sarcasm and negative insinuations of his comments. It would be an interesting exercise to try and build a tool that is able to capture this.

Questions or thoughts? Drop me a line at [lam.diana.hc@gmail.com](mailto:lam.diana.hc@gmail.com). Would love to hear from you!
