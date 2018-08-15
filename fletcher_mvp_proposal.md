## Project Proposal

The minimum viable product that I'm hoping to present on would be a artist identifier and topic modeling project that is able to distinguish between different hip-hop artists. My initial idea was to try and do artist identification by training my model on Donald Glover's stand-up comedy transcripts and attempt to see if my model could traverse the change in medium from stand-up comedy to hip-hop lyrics and identify his alter ego, Childish Gambino out of multiple artists. Instead, my plan is to "simply" do a artist identification model between multiple artists (staying within the same medium), because I didn't think that I could generate a large enough corpus from Donald Glover's limited stand-up comedy transcripts on the internet. After training my model and generating my MVP, I'm still going to try and perform this "hip-hop to stand-up" identifier and hopefully I can get some meaningful results.

### Dataset

I'm working on getting data from Genius to get lyrics from different hip-hop/rap artists, specifically Childish Gambino (Donald Glover's alter ego), Kendrick Lamar, J. Cole, and Kanye West, at the minimum. I initially tried to get the lyrics through Genius's API, but they only allow song/artist information to be pulled, and not lyrics. As a "like-to-have" I'm also planning on scraping some of Donald Glover's stand up comedy transcripts and quotes/interviews.

### Domain

The domain has to deal mostly with linguistics with respect to natural language processing, and determining whether or not Donald Glover's linguistic style can be distinguished from other similar artists. Furthermore, I would be hoping to see if his linguistic style translates across his stand up comedy material and his hip-hop lyrics.

Hip-hop music is one of my favorite genres to listen to, and I've chosen artists who all have relatively similar styles, with respect to musical style and subject matter. All of the artists have used their music to speak on traditional hip-hop subjects such as race, socio-economic inequality, rap culture/partying, and other overt political messages.


### Known unknowns

There are a couple of major known unknowns that I'm worried about running into, but I feel as though some could still give me insight even with the "failure" of a model to fulfill its intended purpose. My major unknown is whether or not I'm going to be able to scrape/obtain enough lyrics from just these 4 artists to build a robust enough model to train on. My second unknown is whether or not these 4 artists write all of their music solely on their own. If any of them have co-writers or ghostwriters for some of their songs, it might bias my model and make it harder to train on an artists specific style. My "nice-to-have" unknown is whether or not NLP will still be able to determine that Donald Glover and Childish Gambino are the same author, despite the big change in styles between stand-up comedy and rap.
