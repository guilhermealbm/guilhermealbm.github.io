+++
date = '2026-03-11'
draft = false
title = 'Reviving my old Kindle'
categories = ['Projects']
languages = ['English']
+++
#### and/or: A small project that reminded me how I learned to build things

I bought this Kindle back in 2016. It worked perfectly for years, until I got a newer one and the old device slowly became useless. I even tried giving each of them a different role, using the old one on public transport and the new one at home, but in practice I always ended up reaching for the new one.

At some point, I came across this [Reddit post](https://www.reddit.com/r/homeassistant/comments/1perwtk/home_assistant_dashboard_on_jailbroken_kindle/) showing how an old Kindle could be repurposed as a small dashboard. That idea stayed in the back of my mind. Later on, my wife and I kept running into a very specific problem at home: figuring out when the next bus was coming. We wanted to avoid standing outside in the Berlin cold for too long, but also did not want to miss it and wait for the next one. At some point I connected those two things and thought: alright, maybe this old Kindle can be useful again.

{{< figure src="/img/posts/reviving-my-old-kindle/kindle-battery.jpeg" alt="Kindle without battery" caption="My good old partner was really being neglected." width="50%" >}}

What I did not expect was how much the whole process would remind me of when I first started programming, around 2015. Back then, a lot of learning came from randomly picking technical problems and trying to make them work. I installed different Linux distributions on my computer, broke them, installed others, and learned something every time. I flashed CyanogenMod on my phone, messed around with Raspberry Pi projects, and spent a lot of time doing things that were not especially practical, but taught me a lot anyway.

Today, things are different. Technology moved on, development workflows changed, and there are now a lot more tools that make everything easier, including AI. But that is only part of it. I changed too. I got older, I have a job, and my relationship with programming is more structured than it used to be. Most of the time that is a good thing. Still, I really like going back to this kind of experimentation when I can, learning something oddly specific, solving a niche problem, and getting a little lost in the process.

So I jailbroke the Kindle, installed a few hacks, and made it periodically fetch a lock screen image from a URL. I also built a small AWS Lambda function that pulls Berlin weather and nearby public transport times, then generates an image with that information. Along the way I learned a bit more about how Kindles work internally, how jailbreaking differs across models, how to use Pillow for image generation, and also had the classic experience of trying to adapt weird shell scripts based on forum comments from years ago.

The end result is simple, but I am really happy with it. There are definitely easier ways to build something like this today, and probably better hardware for it too, but that was never really the point. The real fun was reusing an abandoned device, learning something new, and ending up with a small thing that is genuinely useful in everyday life.

{{< figure src="/img/posts/reviving-my-old-kindle/kindle-dashboard.jpeg" alt="Kindle with new dashboard" caption="I hope I haven't doxxed myself with a bus schedule." width="50%" >}}

In the end, reviving my old Kindle also brought back something I still care a lot about: that old habit of learning by messing around and building small things for no particularly good reason.
