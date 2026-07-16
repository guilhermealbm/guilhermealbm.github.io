+++
date = '2026-02-17'
draft = false
title = 'Compose Previews as the Source of Truth'
categories = ['Android']
languages = ['English']
+++
#### and/or: less setup, less repetition, better IDE workflow

Over the last few years, I’ve felt Android testing get a lot better, both in tooling and in how teams talk about it. Unit tests have always been the default conversation, mostly because the Java ecosystem has had that figured out. But integration tests and screenshot tests never got the same love. They were annoying to set up, slower, flaky in weird ways, and very easy to skip because the payoff didn’t always feel worth the fight.

With Compose, that changed for me. In the last couple of years I’ve been writing more tests than I ever did before, and it hasn’t felt like suffering at all. UI is just code, state is easier to model, and a lot of the old friction is simply gone. Screenshot tests especially became pretty painless once I started using [Paparazzi](https://github.com/cashapp/paparazzi). It’s also been one of the biggest “early warning systems” for me, catching UI bugs before I even open a pull request.

And honestly, Paparazzi is still the safest bet if you want something mature that can handle “real app” usage. It’s fast, predictable, and it’s been around long enough that people trust it. My one recurring annoyance is the workflow. I already have Compose previews describing the states I care about… and then I go write screenshot tests and end up recreating almost the same setup in a test class. It’s not hard, it’s just repetitive.

That’s why Android Studio’s new [Compose Screenshot Testing](https://developer.android.com/studio/preview/compose-screenshot-testing) approach got me excited. The big benefit is simple: it removes the split between “preview code” and “test code”. Your previews become the thing you test. The states live in one place, and screenshot coverage comes from that instead of a parallel test-only setup. And because it’s built into Android Studio, the IDE integration is great. It feels like a natural extension of the preview workflow, not another tool you have to adopt, wire up, and maintain.

It’s still alpha, so I wouldn’t replace a solid Paparazzi suite in production just yet. But I tried it in a side project and it just worked: setup was easy, local runs were smooth, and CI didn’t complain either. The best part was how little extra code it required, because I wasn’t duplicating what I already had in previews.

I’m really curious to see how this evolves. If it lands well and becomes stable, screenshot tests might finally become a default part of Compose projects, not a “nice to have”. It fits the way we already work: build states as previews, iterate quickly, and then turn those same previews into snapshots, no duplicated setup.
