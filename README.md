mixpanel_hax
============  

for testing out mixpanel stuffs  

# read me  

* mixpanel **does not** recommend this approach.
* released under MIT license.  
* i make no warranty as to the fitness of this code.
* [insert other obgligatory preamble here later]  

# status  

the code works in a dev environment with manually passed URL params. next step is to set live on the web, set up corresponding test campaign, view, and project in adwords, GA, and mixpanel, respectively, and see if everything works with ad clicks containing non-utm-prefixed destination URL params as well as dynamically inserted VT params.  

# background  

i'm testing this out b/c i want to find a way to get adwords, GA, and mixpanel to play nicely togetner. what do i mean by this?  

if you've set up auto-tagging for adwords and GA you get a lot of useful data for free through gclid. but 3rd party apps can't use gclid data, so if you want your 3rd party app to track utm_source, for example, you have to find another way of passing it in the URL.  

manually tagging destination URLs with utm parameters allows 3rd party apps to "see" these data, but google don't recommend using auto-tagging *and* manually setting utm-prefixed params because it can cause things to get "wonky" in GA.  

we *could* use non-utm-prefixed params in destination URLs and register corresponding properties in mixpanel, but out of the box there's no way i know of to tell mixpanel, "hey, aw_source is the same thing as utm_source, so let's just use that in our reporting, mmkay?"  

an aside: like us you may want to automate tracking of dynamic performance-related data such as search keywords, search ad position, display URL (etc.). see goog's documentation on ValueTrack and read the test code here to see how to implement.

# solution  

to note: mixpanel advises against forking their code and self-hosting (for some good reasons) so we'll look into taking this functionality out and placing it in our code.  

to see how we're attempting this take a look at the diff between the first and third commits. the first commit is mixpanel's unmodified code and the third commit includes comments about functionality, ideas for extending the code, and a few more params that could be interesting.  

comments/suggestions welcome!
