![2021-09-06 16_52_45-Window](https://user-images.githubusercontent.com/74114604/132259998-0b9a8e81-97f5-4f50-9bef-b924c2b4e44c.png)


  # EIT - Adidas Sentiment & intent of purchase ML analysis

**_What are we doing?_**

Analyzing previous twitter data on tweets containing the word adidas.

**_Why are we doing this?_**

To help identify customer sentiment on the brand and purchasing intent.

**_How are we doing this?_**

Using statistical modelling to analyze tweets and predict customer sentiment on the brand, as well as their purchase intent.

**_What will we gain from this?_**

The ability to understand customers’ opinions on the brand and target them based on the group they fall in.

___

**Sentiment Analysis**

To analyze the sentiment on the scraped tweets, VADER Sentiment Analysis was used, VADER stands for: Valence Aware Dictionary and sEntiment Reasoner.


VADER is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media, and works well on texts from other domains.
>Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.


**Intent of purchase Analysis**


In other to perform this analysis, 500 tweets were labeled by the collaborators:

**0** – No relation in terms in purchase intent

-Eg: 
>@MUFC_Tom18 Itâ€™s easy this one. The Glazers have zero interest in winning the league, theyâ€™re happy with top 4. Why? Because the prize money isnâ€™t a big enough difference to justify the extra investment. As long as they get CL football they hit the marker with Adidas. Thatâ€™s it, the truth.

**1** – Some possibility related to purchase

-Eg. 
>@KB24X5 @lakeshow_wess Adidas NBA gear was/is much better than Nike IMO. For me the Nike apparel are more fitted, like for I have to go one size up on all the jerseys and shorts. As to adidas I can go true to size without worrying if itâ€™s going to be tight or not.

**2** – Very related to a purchase intent

-Eg. 
>@playingarts @leonardoworx @Adobe @WIRED @billboard @adidas This is my personal favorite. So glad I could afford one before these take off!


For the intent of purchase, a [Sequential] (https://www.tensorflow.org/guide/keras/sequential_model) [TensorFlow] (https://www.tensorflow.org/) model was used to make the classification.

