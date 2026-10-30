+++
date = '2026-10-30'
draft = false
title = 'Small revolutions'
categories = ['AI']
languages = ['English']
+++
#### and/or: vibe coding the Brazilian elections

When I decided to start writing on a blog again in 2026, I did it because I truly believe good (human) communication is something no AI can do (at least so far! Maybe I should write about that too). However, what has really got me thinking lately is how non-technical people can now use AI to build things that amplify what they want to say.

This month Brazil held its elections, and among all the crazy political things going on, I noticed how many people were using LLMs to build websites to follow the results live. Obviously, what makes this possible is the fact that the Superior Electoral Court (TSE) provides live data through an API, and of course there were plenty of sloppy websites and charts. But the fact that people without much programming experience were finally "allowed" to create something tailored exactly to what they wanted was wild, and many of those projects were genuinely interesting.

Last weekend we had the second round, and I think this time the trend was trying to predict the outcome. I even built a predictor myself, and my first prediction was within 0.2% of the final result with a bit less than 20% of the votes counted. But the story of [@ro_mahl](https://x.com/ro_mahl) is what really motivated me to write this. He had already made a prediction for the first round based on the 2022 results, and it turned out to be pretty accurate. For the second round, he correctly predicted the result with only a bit more than 2% of the votes counted.

He's now giving lots of interviews to major TV channels in Brazil, and he said that, although he studied a bit of Python during his Economics BSc, he is not a programmer at all. And although he is a PhD student in Political Science at Duke University, election forecasting isn't even his research area. He just happened to be interested in the Brazilian elections and built his own predictor. And he got incredibly accurate results with only a few votes counted because of his knowledge of Political Science, not programming. If you're interested, he explains his method in more detail [here](https://projecao.2026elections.workers.dev), although it's only available in Portuguese.

Yes, we all know the dangers of so-called vibe coding and all the silver bullets the AI hype is trying to sell us, but I think this is a very good example of when these tools can be really valuable. Maybe this will age like milk, but I think from now on it'll become more and more common for non-technical people to think "maybe I can ask AI to build this for me" whenever they want a small, specific app or website, instead of googling it or searching the app stores. And as programmers, I think we should sometimes allow ourselves to use LLMs to write (non-critical) software without even looking at the code. If it works and the scope is limited and under control, let's feed the monster.