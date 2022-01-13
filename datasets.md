---
layout: page
title: Datasets
permalink: /datasets/
---

Below is a list of real-world datasets relevant to digital evidence that are useful for trying out proposed methodologies.

1. [Email communications](#email-communication)
2. [Mobile app usage](#mobile-app-usage)
3. [Device location pings](#device-location-pings)

### Email communications

The email-Eu-core-temporal network dataset comes from the <a href="https://snap.stanford.edu/index.html">Stanford Network Analysis Project</a> and consists of ~300,000 emails sent from October 2003 through May 2005. A row in the dataset is of the form `<sender_id, recipient_id, timestamp>` where the sender and recipient IDs identify the users who sent and received the emails, respectively, and the timestamp is the time at which the email was sent.

_References_:

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



