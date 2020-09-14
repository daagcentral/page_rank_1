# Pagerank Project: SOLUTION

## Task 1: the power method

**Part 1:**
```
% python3 pagerank.py --data=small.csv.gz --verbose 
DEBUG:root:computing indices
DEBUG:root:computing values
INFO:root:rank=0 pagerank=2.1634e+00 url=4
INFO:root:rank=1 pagerank=1.6664e+00 url=6
INFO:root:rank=2 pagerank=1.2402e+00 url=5
INFO:root:rank=3 pagerank=4.5712e-01 url=2
INFO:root:rank=4 pagerank=3.5620e-01 url=3
INFO:root:rank=5 pagerank=3.2078e-01 url=1
```

**Part 2:**
The `pagerank.py` file has an option `--search_query`, which takes a string as a parameter.
If this argument is used, then program returns all urls that match the query string sorted according to their pagerank.
Essentially, this gives us the most important pages on the blog related to our query.

Again, you may not get the exact same results as me,
but you should get similar results to the examples I've shown below.
Verify that you do in fact get similar results.

```
% python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='corona'
INFO:root:rank=0 pagerank=4.5861e-03 url=www.lawfareblog.com/lawfare-podcast-united-nations-and-coronavirus-crisis
INFO:root:rank=1 pagerank=4.0460e-03 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
INFO:root:rank=2 pagerank=2.6116e-03 url=www.lawfareblog.com/britains-coronavirus-response
INFO:root:rank=3 pagerank=2.5390e-03 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
INFO:root:rank=4 pagerank=2.3557e-03 url=www.lawfareblog.com/israeli-emergency-regulations-location-tracking-coronavirus-carriers
INFO:root:rank=5 pagerank=2.2895e-03 url=www.lawfareblog.com/why-congress-conducting-business-usual-face-coronavirus
INFO:root:rank=6 pagerank=2.2727e-03 url=www.lawfareblog.com/livestream-house-oversight-committee-holds-hearing-government-coronavirus-response
INFO:root:rank=7 pagerank=2.2520e-03 url=www.lawfareblog.com/congressional-homeland-security-committees-seek-ways-support-state-federal-responses-coronavirus
INFO:root:rank=8 pagerank=2.1878e-03 url=www.lawfareblog.com/paper-hearing-experts-debate-digital-contact-tracing-and-coronavirus-privacy-concerns
INFO:root:rank=9 pagerank=2.0339e-03 url=www.lawfareblog.com/cyberlaw-podcast-how-israel-fighting-coronavirus

% python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='trump'
INFO:root:rank=0 pagerank=6.6243e-02 url=www.lawfareblog.com/donald-trump-and-politically-weaponized-executive-branch
INFO:root:rank=1 pagerank=6.0194e-02 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
INFO:root:rank=2 pagerank=3.4969e-02 url=www.lawfareblog.com/trump-administrations-worrying-new-policy-israeli-settlements
INFO:root:rank=3 pagerank=3.2193e-02 url=www.lawfareblog.com/document-trump-revokes-obama-executive-order-counterterrorism-strike-casualty-reporting
INFO:root:rank=4 pagerank=3.0971e-02 url=www.lawfareblog.com/dc-circuit-overrules-district-courts-due-process-ruling-qasim-v-trump
INFO:root:rank=5 pagerank=2.8460e-02 url=www.lawfareblog.com/how-trumps-approach-middle-east-ignores-past-future-and-human-condition
INFO:root:rank=6 pagerank=2.5252e-02 url=www.lawfareblog.com/why-trump-cant-buy-greenland
INFO:root:rank=7 pagerank=2.2457e-02 url=www.lawfareblog.com/oral-argument-summary-qassim-v-trump
INFO:root:rank=8 pagerank=2.1462e-02 url=www.lawfareblog.com/dc-circuit-court-denies-trump-rehearing-mazars-case
INFO:root:rank=9 pagerank=2.1103e-02 url=www.lawfareblog.com/second-circuit-rules-mazars-must-hand-over-trump-tax-returns-new-york-prosecutors

% python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='iran'
INFO:root:rank=0 pagerank=6.6131e-02 url=www.lawfareblog.com/praise-presidents-iran-tweets
INFO:root:rank=1 pagerank=2.9199e-02 url=www.lawfareblog.com/how-us-iran-tensions-could-disrupt-iraqs-fragile-peace
INFO:root:rank=2 pagerank=1.7709e-02 url=www.lawfareblog.com/cyber-command-operational-update-clarifying-june-2019-iran-operation
INFO:root:rank=3 pagerank=1.4604e-02 url=www.lawfareblog.com/aborted-iran-strike-fine-line-between-necessity-and-revenge
INFO:root:rank=4 pagerank=8.4512e-03 url=www.lawfareblog.com/iranian-hostage-crisis-and-its-effect-american-politics
INFO:root:rank=5 pagerank=8.3989e-03 url=www.lawfareblog.com/parsing-state-departments-letter-use-force-against-iran
INFO:root:rank=6 pagerank=8.2581e-03 url=www.lawfareblog.com/announcing-united-states-and-use-force-against-iran-new-lawfare-e-book
INFO:root:rank=7 pagerank=8.0561e-03 url=www.lawfareblog.com/trump-moves-cut-irans-oil-revenues-whats-his-endgame
INFO:root:rank=8 pagerank=7.1939e-03 url=www.lawfareblog.com/us-names-iranian-revolutionary-guard-terrorist-organization-and-sanctions-international-criminal
INFO:root:rank=9 pagerank=5.9405e-03 url=www.lawfareblog.com/iran-shoots-down-us-drone-domestic-and-international-legal-implications
```

**Part 3:**
```
$ python3 pagerank.py --data=./lawfareblog.csv.gz --filter_ratio=0.2
INFO:root:rank=0 pagerank=3.4696e-01 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
INFO:root:rank=1 pagerank=2.9521e-01 url=www.lawfareblog.com/livestream-nov-21-impeachment-hearings-0
INFO:root:rank=2 pagerank=2.9040e-01 url=www.lawfareblog.com/opening-statement-david-holmes
INFO:root:rank=3 pagerank=1.5179e-01 url=www.lawfareblog.com/lawfare-podcast-ben-nimmo-whack-mole-game-disinformation
INFO:root:rank=4 pagerank=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1963
INFO:root:rank=5 pagerank=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1964
INFO:root:rank=6 pagerank=1.5071e-01 url=www.lawfareblog.com/lawfare-podcast-week-was-impeachment
INFO:root:rank=7 pagerank=1.4957e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1962
INFO:root:rank=8 pagerank=1.4367e-01 url=www.lawfareblog.com/cyberlaw-podcast-mistrusting-google
INFO:root:rank=9 pagerank=1.4240e-01 url=www.lawfareblog.com/lawfare-podcast-bonus-edition-gordon-sondland-vs-committee-no-bull
```

**Part 4:**
```
% python3 pagerank.py --data=./lawfareblog.csv.gz --verbose
DEBUG:root:computing indices
DEBUG:root:computing values
INFO:root:rank=0 pagerank=8.4156e+00 url=www.lawfareblog.com/litigation-documents-related-appointment-matthew-whitaker-acting-attorney-general
INFO:root:rank=1 pagerank=8.4156e+00 url=www.lawfareblog.com/lawfare-job-board
INFO:root:rank=2 pagerank=8.4156e+00 url=www.lawfareblog.com/documents-related-mueller-investigation
INFO:root:rank=3 pagerank=8.4156e+00 url=www.lawfareblog.com/litigation-documents-resources-related-travel-ban
INFO:root:rank=4 pagerank=8.4156e+00 url=www.lawfareblog.com/subscribe-lawfare
INFO:root:rank=5 pagerank=8.4156e+00 url=www.lawfareblog.com/masthead
INFO:root:rank=6 pagerank=8.4156e+00 url=www.lawfareblog.com/topics
INFO:root:rank=7 pagerank=8.4156e+00 url=www.lawfareblog.com/our-comments-policy
INFO:root:rank=8 pagerank=8.4156e+00 url=www.lawfareblog.com/upcoming-events
INFO:root:rank=9 pagerank=8.4156e+00 url=www.lawfareblog.com/about-lawfare-brief-history-term-and-site

% python3 pagerank.py --data=./lawfareblog.csv.gz --verbose --alpha=0.99999
DEBUG:root:computing indices
DEBUG:root:computing values
INFO:root:rank=0 pagerank=1.0624e+01 url=www.lawfareblog.com/snowden-revelations
INFO:root:rank=1 pagerank=1.0624e+01 url=www.lawfareblog.com/lawfare-job-board
INFO:root:rank=2 pagerank=1.0624e+01 url=www.lawfareblog.com/masthead
INFO:root:rank=3 pagerank=1.0624e+01 url=www.lawfareblog.com/litigation-documents-resources-related-travel-ban
INFO:root:rank=4 pagerank=1.0624e+01 url=www.lawfareblog.com/subscribe-lawfare
INFO:root:rank=5 pagerank=1.0624e+01 url=www.lawfareblog.com/litigation-documents-related-appointment-matthew-whitaker-acting-attorney-general
INFO:root:rank=6 pagerank=1.0624e+01 url=www.lawfareblog.com/documents-related-mueller-investigation
INFO:root:rank=7 pagerank=1.0624e+01 url=www.lawfareblog.com/our-comments-policy
INFO:root:rank=8 pagerank=1.0624e+01 url=www.lawfareblog.com/upcoming-events
INFO:root:rank=9 pagerank=1.0624e+01 url=www.lawfareblog.com/topics

% python3 pagerank.py --data=./lawfareblog.csv.gz --verbose --filter_ratio=0.2
DEBUG:root:computing indices
DEBUG:root:computing values
INFO:root:rank=0 pagerank=4.6091e+00 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
INFO:root:rank=1 pagerank=2.9867e+00 url=www.lawfareblog.com/livestream-nov-21-impeachment-hearings-0
INFO:root:rank=2 pagerank=2.9669e+00 url=www.lawfareblog.com/opening-statement-david-holmes
INFO:root:rank=3 pagerank=2.0173e+00 url=www.lawfareblog.com/senate-examines-threats-homeland
INFO:root:rank=4 pagerank=1.8769e+00 url=www.lawfareblog.com/what-make-first-day-impeachment-hearings
INFO:root:rank=5 pagerank=1.8762e+00 url=www.lawfareblog.com/livestream-house-armed-services-committee-hearing-f-35-program
INFO:root:rank=6 pagerank=1.8693e+00 url=www.lawfareblog.com/whats-house-resolution-impeachment
INFO:root:rank=7 pagerank=1.7655e+00 url=www.lawfareblog.com/congress-us-policy-toward-syria-and-turkey-overview-recent-hearings
INFO:root:rank=8 pagerank=1.6807e+00 url=www.lawfareblog.com/summary-david-holmess-deposition-testimony
INFO:root:rank=9 pagerank=9.8346e-01 url=www.lawfareblog.com/events

% python3 pagerank.py --data=./lawfareblog.csv.gz --verbose --filter_ratio=0.2 --alpha=0.99999
DEBUG:root:computing indices
DEBUG:root:computing values
INFO:root:rank=0 pagerank=5.2385e+01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
INFO:root:rank=1 pagerank=5.2385e+01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
INFO:root:rank=2 pagerank=7.9438e+00 url=www.lawfareblog.com/cost-using-zero-days
INFO:root:rank=3 pagerank=2.3700e+00 url=www.lawfareblog.com/lawfare-podcast-former-congressman-brian-baird-and-daniel-schuman-how-congress-can-continue-function
INFO:root:rank=4 pagerank=1.5529e+00 url=www.lawfareblog.com/events
INFO:root:rank=5 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-increased-us-focus-indo-pacific
INFO:root:rank=6 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-drill-maybe-drill
INFO:root:rank=7 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-disjointed-operations-south-china-sea
INFO:root:rank=8 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-us-china-divide-shangri-la
INFO:root:rank=9 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-sinking-feeling-philippine-china-relations
```



## Task 2: the personalization vector

**Part 1:**
```
% python3 pagerank.py --data=./lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona'
INFO:root:rank=0 pagerank=8.8870e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
INFO:root:rank=1 pagerank=8.8867e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
INFO:root:rank=2 pagerank=1.8256e-01 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
INFO:root:rank=3 pagerank=1.4907e-01 url=www.lawfareblog.com/brexit-not-immune-coronavirus
INFO:root:rank=4 pagerank=1.4907e-01 url=www.lawfareblog.com/rational-security-my-corona-edition
INFO:root:rank=5 pagerank=1.0729e-01 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
INFO:root:rank=6 pagerank=1.0199e-01 url=www.lawfareblog.com/britains-coronavirus-response
INFO:root:rank=7 pagerank=1.0199e-01 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
INFO:root:rank=8 pagerank=9.4298e-02 url=www.lawfareblog.com/lawfare-podcast-mom-and-dad-talk-clinical-trials-pandemic
INFO:root:rank=9 pagerank=8.7207e-02 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
```

using `--search_query` option:
```
% python3 pagerank.py --data=./lawfareblog.csv.gz --filter_ratio=0.2 --search_query='corona'
INFO:root:rank=0 pagerank=1.2502e-01 url=www.lawfareblog.com/congress-needs-coronavirus-failsafe-its-too-late
INFO:root:rank=1 pagerank=6.0747e-02 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
INFO:root:rank=2 pagerank=5.4774e-02 url=www.lawfareblog.com/britains-coronavirus-response
INFO:root:rank=3 pagerank=5.4397e-02 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
INFO:root:rank=4 pagerank=5.1758e-02 url=www.lawfareblog.com/livestream-house-oversight-committee-holds-hearing-government-coronavirus-response
INFO:root:rank=5 pagerank=5.1446e-02 url=www.lawfareblog.com/paper-hearing-experts-debate-digital-contact-tracing-and-coronavirus-privacy-concerns
INFO:root:rank=6 pagerank=4.7120e-02 url=www.lawfareblog.com/why-congress-conducting-business-usual-face-coronavirus
INFO:root:rank=7 pagerank=2.7820e-02 url=www.lawfareblog.com/israeli-emergency-regulations-location-tracking-coronavirus-carriers
INFO:root:rank=8 pagerank=2.7438e-02 url=www.lawfareblog.com/lawfare-podcast-united-nations-and-coronavirus-crisis
INFO:root:rank=9 pagerank=2.0545e-02 url=www.lawfareblog.com/congressional-homeland-security-committees-seek-ways-support-state-federal-responses-coronavirus
```

**Part 2:**
Using both the `--search_query` and `--personalization_vector_query` option
```
% python3 pagerank.py --data=./lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona' --search_query='-corona'
INFO:root:rank=0 pagerank=8.8870e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
INFO:root:rank=1 pagerank=8.8867e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
INFO:root:rank=2 pagerank=1.8256e-01 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
INFO:root:rank=3 pagerank=1.0729e-01 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
INFO:root:rank=4 pagerank=9.4298e-02 url=www.lawfareblog.com/lawfare-podcast-mom-and-dad-talk-clinical-trials-pandemic
INFO:root:rank=5 pagerank=7.9633e-02 url=www.lawfareblog.com/fault-lines-foreign-policy-quarantined
INFO:root:rank=6 pagerank=7.5307e-02 url=www.lawfareblog.com/limits-world-health-organization
INFO:root:rank=7 pagerank=6.8115e-02 url=www.lawfareblog.com/chinatalk-dispatches-shanghai-beijing-and-hong-kong
INFO:root:rank=8 pagerank=6.4847e-02 url=www.lawfareblog.com/us-moves-dismiss-case-against-company-linked-ira-troll-farm
INFO:root:rank=9 pagerank=6.4847e-02 url=www.lawfareblog.com/livestream-house-foreign-affairs-committee-holds-hearing-crisis-idlib
```