---
layout: page
title: Datasets
permalink: /datasets/
---

Below is a list of real-world datasets relevant to digital evidence that are useful for trying out proposed methodologies.

1. [Email communications](#email-communication)
2. [Mobile app usage](#mobile-app-usage)
3. [Device location pings](#device-location-pings)
4. [Web browsing](#web-browsing)
5. [Authentication](#authentication)
6. [Amazon product reviews](#amazon-product-reviews)
7. [Reddit comments](#reddit-comments)

### Email communications

The email-Eu-core-temporal network dataset comes from the <a href="https://snap.stanford.edu/index.html">Stanford Network Analysis Project</a> and consists of ~300,000 emails sent from October 2003 through May 2005. A row in the dataset is of the form `<sender_id, recipient_id, timestamp>` where the sender and recipient IDs identify the users who sent and received the emails, respectively, and the timestamp is the time at which the email was sent.

References:

* <a href="https://snap.stanford.edu/index.html">Stanford Network Analysis Project</a>
* <a href="https://snap.stanford.edu/data/email-Eu-core-temporal.html">email-Eu-core-temporal dataset</a>
* <a href="https://dl.acm.org/doi/abs/10.1145/3018661.3018731">Canonical paper</a>: 

> Ashwin Paranjape, Austin R. Benson, and Jure Leskovec. "Motifs in Temporal Networks." In Proceedings of the Tenth ACM International Conference on Web Search and Data Mining, 2017.

### Mobile app usage

This dataset consists of ~3.6 million app usage records for Android users from September 2017 through May 2018. An app usage record (row in the dataset) is of the form `<user_id, app_name, event_type, timestamp>` where the user ID identifies the Android user, the app name identifies the app in which the event occurred, the event type is one of Opened, Closed, User Interaction, or Broken, and the timestamp is the time at which the event occurred.

References:

* <a href="https://github.com/aliannejadi/LSApp">Dataset page</a>
* <a href="https://dl.acm.org/doi/abs/10.1145/3447678">Canonical paper</a>:

> Mohammad Aliannejadi, Hamed Zamani, Fabio Crestani, and W. Bruce Croft. 2020. Context-Aware Target Apps Selection and Recommendation for Enhancing Personal Mobile Assistants. ACM Transactions on Information Systems (TOIS).

### Device location pings

This dataset was collected via the Twitter Streaming API and consists of ~80,000 geolocated Tweets from Orange County, CA collected from September 2020 through March 2021. Each Tweet (a row in the dataset) is of the form `<user_id, latitude, longitude, timestamp>` where the user ID identifies the Twitter account, the coordinates are the location of the device from which the Tweet was sent, and the timestamp is the time at which the Tweet was posted. Note that this information is only available on public Tweets for which the user has opted in to sharing their geo-coordinates.

References:

* <a href="https://github.com/UCIDataLab/uci-digital-evidence/tree/main/twitter_data">Dataset page</a> (Note that per Twitter's API use policy only the Tweet IDs can be shared)
* <a href="https://developer.twitter.com/en/docs/twitter-api/v1/tweets/filter-realtime/overview">Twitter Streaming API</a>
* <a href="https://developer.twitter.com/en/developer-terms/agreement-and-policy">Twitter API use policy</a>

### Web browsing

This dataset comes from an observational study conducted at a large U.S. university and consists of ~90,000 records of web browsing events from 55 students. Each web browsing event (a row in the dataset) is of the form `<id, m, t>` where the ID corresponds to the student, m indicates whether or not the event was a Facebook-browser event (2 indicates a Facebook event and 1 indicates a non-Facebook event), and t denotes the timestamp.

References:

* Data available <a href="https://github.com/UCIDataLab/assocr">here</a>. (Note that the data is included in the _student_web_browsing_ folder of the data file.)
* <a href="https://doi.org/10.1111/rssa.12549">CSAFE paper using this data</a>:

>Galbraith, Christopher, Padhraic Smyth, and Hal S. Stern. "Quantifying the association between discrete event time series with applications to digital forensics." Journal of the Royal Statistical Society: Series A (Statistics in Society) 183.3 (2020): 1005-1027.

* <a href="https://doi.org/10.1145/2675133.2675271">Canonical paper for dataset</a>:

>Wang, Yiran, et al. "Coming of Age (Digitally) An Ecological View of Social Media Use among College Students." Proceedings of the 18th ACM conference on computer supported cooperative work & social computing. 2015.

### Authentication

This dataset is composed of ~850 authentication events from two users successfully authenticating into computers on the Los Alamos National Laboratory enterprise network. Each event is of the form `<t, id, cid>` where t is the timestamp of the authentication event, the ID identifies the user account, and the CID identifies the computer logged into by the user.

References:

* Data available <a href="https://github.com/UCIDataLab/assocr">here</a>. (Note that the data is included in the _lanl_ folder of the data file.)
* <a href="https://doi.org/10.1111/rssa.12549">CSAFE paper using this data</a>:

>Galbraith, Christopher, Padhraic Smyth, and Hal S. Stern. "Quantifying the association between discrete event time series with applications to digital forensics." Journal of the Royal Statistical Society: Series A (Statistics in Society) 183.3 (2020): 1005-1027.

* Canonical reference for this dataset:

>Kent, Alexander D. "User-computer authentication associations in time." Los Alamos National Laboratory (2014).

### Amazon product reviews

This dataset is composed of 10,000 product reviews from 2000 Amazon accounts between 1996 and 2014. The dataset is organized into authorship verification cases, in which each case has texts from a known account and one text from an unknown account. The goal is to determine if the text from the unknown account came from the same account as the known-account texts. The text of a review reviews a product in one of 17 product categories, and documents by the same user were taken across different categories so that each verification case is of mixed topic.

References:
* Data available <a href="https://www.dropbox.com/sh/qelav1ap0uwo82q/AABb5f5FrfTjn3tUKB9cOhZia/English?dl=0&subfolder_nav_tracking=1">here</a>
* Associated publications:

> Halvani, Oren, Lukas Graner, and Roey Regev. "TAVeer: an interpretable topic-agnostic authorship verification method." Proceedings of the 15th International Conference on Availability, Reliability and Security. 2020.  <a href="https://doi.org/10.1145/3407023.3409194">https://doi.org/10.1145/3407023.3409194</a>

> Halvani, Oren, Lukas Graner, and Roey Regev. "A step towards interpretable authorship verification." arXiv preprint arXiv:2006.12418 (2020).<a href="https://doi.org/10.48550/arXiv.2006.12418">https://doi.org/10.48550/arXiv.2006.12418</a>

This dataset is derived from the Amazon product data corpus, which is available at: <a href="https://nijianmo.github.io/amazon/index.html">https://nijianmo.github.io/amazon/index.html</a> and is discussed in the associated publication found below.

> Ni, Jianmo, Jiacheng Li, and Julian McAuley. "Justifying recommendations using distantly-labeled reviews and fined-grained aspects." Empirical Methods in Natural Language Processing (EMNLP), 2019.


### Reddit comments

This dataset is composed of 4000 Reddit comments from 1000 users between 2010 to 2016. The dataset is organized into authorship verification cases, in which each case has texts from a known account and one text from an unknown account. The goal is to determine if the text from the unknown account came from the same account as the known-account texts. The comments which comprise the known-account texts were taken from disjoint subreddits such that each case is of mixed topic.

References:
* Data available <a href="https://www.doi.org/10.17632/hppkn5kbg8.1">here</a>
* Associated publications:

> Halvani, Oren (2016), “Reddit Cross-Topic Authorship Verification Corpus”, Mendeley Data, V1, doi: 10.17632/hppkn5kbg8.1

> Halvani, Oren, Lukas Graner, and Roey Regev. "TAVeer: an interpretable topic-agnostic authorship verification method." Proceedings of the 15th International Conference on Availability, Reliability and Security. 2020.  <a href="https://doi.org/10.1145/3407023.3409194">https://doi.org/10.1145/3407023.3409194</a>

> Halvani, Oren, Lukas Graner, and Roey Regev. "A step towards interpretable authorship verification." arXiv preprint arXiv:2006.12418 (2020).<a href="https://doi.org/10.48550/arXiv.2006.12418">https://doi.org/10.48550/arXiv.2006.12418</a>



