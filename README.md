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

## Sentiment Analysis

To analyze the sentiment on the scraped tweets, VADER Sentiment Analysis was used, VADER stands for: Valence Aware Dictionary and sEntiment Reasoner.


VADER is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media, and works well on texts from other domains.
>Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.


## Intent of purchase Analysis


In other to perform this analysis, 500 tweets were labeled by the collaborators:

**0** – No relation in terms in purchase intent

-Eg: 
>_@MUFC_Tom18 Itâ€™s easy this one. The Glazers have zero interest in winning the league, theyâ€™re happy with top 4. Why? Because the prize money isnâ€™t a big enough difference to justify the extra investment. As long as they get CL football they hit the marker with Adidas. Thatâ€™s it, the truth._

**1** – Some possibility related to purchase

-Eg. 
>_@KB24X5 @lakeshow_wess Adidas NBA gear was/is much better than Nike IMO. For me the Nike apparel are more fitted, like for I have to go one size up on all the jerseys and shorts. As to adidas I can go true to size without worrying if itâ€™s going to be tight or not._

**2** – Very related to a purchase intent

-Eg. 
>_@playingarts @leonardoworx @Adobe @WIRED @billboard @adidas This is my personal favorite. So glad I could afford one before these take off!_


Since the tweet data was limited to only 7 days of scraping, the corpus is bias to this time frame. To improve the model prediction strength, control points were imputed to the training set:

>['i want adidas','probably i will buy adidas','will not buy adidas']
>
_Setting the classification to 2, 1 & 0 respectively._

### Modelling

For the intent of purchase, a [Sequential](https://www.tensorflow.org/guide/keras/sequential_model) model with [TensorFlow](https://www.tensorflow.org/) was used to make the classification.


To prevent overfitting, [Dropout](https://www.tensorflow.org/tutorials/keras/overfit_and_underfit) was applied to a layer, consists of randomly "dropping out" (i.e. set to zero) a number of output features of the layer during training. Let's say a given layer would normally have returned a vector [0.2, 0.5, 1.3, 0.8, 1.1] for a given input sample during training; after applying dropout, this vector will have a few zero entries distributed at random, e.g. [0, 0.5, 1.3, 0, 1.1].


For the training, the data was balanced, by reducing the majority of the labels 0, to avoid preference on the model by this class.

![2021-09-06 22_08_41-Window](https://user-images.githubusercontent.com/74114604/132273479-4526da47-460f-4c8d-b3d7-b24798624545.png)


For the intent of purchase, a [Sequential] (https://www.tensorflow.org/guide/keras/sequential_model) [TensorFlow] (https://www.tensorflow.org/) model was used to make the classification.


For the input layer, the [nnlm-en-dim128]( https://tfhub.dev/google/nnlm-en-dim128/2) text embedder was used.




![2021-09-06 21_48_55-Window](https://user-images.githubusercontent.com/74114604/132273159-9a553978-ab6f-460b-a2e7-83be3b572a07.png)


![2021-09-06 21_49_04-Window](https://user-images.githubusercontent.com/74114604/132273162-02077ffd-7d0a-439c-a85e-779b7445461a.png)





