```
Author: Luca Matteo Spoljarevic
Contact: git@spoljarevic.info
My new website: https://spoljarevic.sh
Socials: https://socials.spoljarevic.sh
Projects: https://projects.spoljarevic.sh
Date created: 2026-02-27
Last changed: 2026-02-27
```

# Greetings everyone!
## Short introduction ##
So you're back at my blog? I see.
Well... too bad! Now you're gonna hear me yapping about one of my favorite music artists.
Her artist name is **Ronan Fae**, but due to simplicity I will just call her Ronja here, since that's how I got to know here.

We'll first talk about the technical part. So what I did for her IT and then I spend some time writing more about her (call it free promotion if you like).

I just want to make sure that we are on the same level here.
I am **not** getting paid to promote her, neither do I get any money from what I do for her.
The opposit is the case, for the two domains I bought for her over time, I invested my own money.

And I have no interest in getting some from her in the future. I simply do this because I like her and this is my way to support her and saying thank you for your music.

## What I did for Ronan Fae ##
### Cloudflare and Domains ###
#### Domains that are booked ####
Ronja recently had a namechange.
Originally I bought the domain ronjasmusic.com.
When I offered my service and she accepted, I asked her (in human language), what tld (top-level domain) she wants.

When she said a simple .com domain, I immediately looked for ronjamusic.com, since Ronja Music was her Artist name at that time.

Sadly it was already gone, so I looked for alternatives. And quickly I found ronjasmusic.com.
Asked her if that's fine with her and afer approval, I booked the domain.

When she told me about the name change, I immediately looked for a new domain.

Ronan Fae was her new name and I was quite happy to see that ronanfae.com was still available.

After fully migrating my domains from various providers to Cloudflare, I will not take the old domain with me.
This will take a few months tho due to some of them being locked right now. Meaning I can't bring them to a new provider.

After that, ronjasmusic.com will be free again and ronanfae.com will remain to build an identity for Ronja in the future

#### Websites and redirects ####
Before you ask, I am no web-developer.
I understand the basics and did code websites a bit as a hobby a few years ago, but I'm rusty.

I didn't want to vibe code something for her, I tought this won't meet the standards I want to set for her.
But I wanted to have a great socials site for her and her fans.

At the time, I self-hosted a [Linkstack Instance](https://linkstack.org/) (Open source and in my opinion even better Linktree alternative) for myself on a dedicated Ionos Server.
And smart as I was, I simply set up a user for her, copied her old socials instance pretty much 1:1 and set up a nice theme.
Then I created an nginx config for the site and connected the domain socials.ronjasmusic.com.

And would you look at that, the website was online.

Now don't make the mistake and host anything on Ionos nor a dedicated server if you don't have a really good reason.
These are the specs I had on that server and what it cost me (prices are usage over 30 days):
```
OS: Debian Linux
Static IPv4: 5,15€
HDD Snapshot: 15,71€
SSD Premium Storage: 31€
SSD Standard Storage: 36,17€
AMD EPYC Gen 3: 99,48€
RAM (I think I had 8 GB ram?): 51,03€
HDD Storage: 9,09€
```
In total, for a server with little reccources, I paid (taxes included) 294,68€
And that was before the RAM prices went insane.

For 50-100 bucks a month, I could've gotten a dedicated server with pretty much double everything minimum somewhere else.
But at the time I simply didn't know better, so shit happens.

Anyway, after maybe half a year or a bit longer I canceled that server and since I don't want any port forwarding on my router, I decided to let the creator of Linkstack host the site.
I know that he just had a lot happening in his personal life, but at the time, a few months after I subscribed to a professional plan with him, I didn't get any replies to emails I sent.
Not on requests like changing the domain nor on really important things like the site appears to be down.
That dragged over a few more months until I decided that I'm quite unhappy with the service and therefore canceled the subscribtion.

Again, now I know the reasons of him behaving like this and can comfortably say that you should definitly let him host it for you.
Maybe give him a few more months to work on the backlog, but then definitly consider it.

Anyway, I switched to a fre instance and set up everything for me and for Ronja.
But since I couldn't connect her domain with the free instance, I decided to create a redirect from socials.ronanfae.com to linksta.cc/@ronanfae.

For that I simply went to Cloudflare and on Rule/Overview clicked on ``Create rule``. There I selected ``Redirect Rules`` and ``Redirect to a different domain``.
Now I just needed to change smallshop.example.com to socials.ronanfae.com and in the then section replaced globalstore.example.net to linksta.cc/@ronanfae.

It is important to leave the rest untouched, trust me, this is how it'll gonna work.

### Ask before doing something ####
Now that I was on the flow with domains and all that good stuff, I decided to create a Proton Account for her with my referal link and set up a domain for Proton Mail and one subdomain for Proton Pass Aliases (SimpleLogin Service).
That was pretty easy since those steps are already in my blood considering how often I did this but also since both Proton Mail and Proton Pass walk you through every single step.
When that was done, I decided to create a few Mail Addresses and inform Ronja.

When informing her, I also said that she needs to test it quickly since the free trial is only 14 days long.
You see, not only did I do stuff she didn't ask for (pretty sure that alone would be fine), but I also put her under massive time pressure.

That's not okay to do to a normal person, but I knew Ronja is struggeling with mental health, which made the whole situation even worse.

Of course I didn't just say "Here, I made this for you and now test it you have only this amount of time".
I would never talk to a person like this.

I took time explaining what everything is, why I did this, why I tought it was an important step but also reassured her that even if she doesn't have the time nor nerves to do this right now, that I can always do it again and she really doesn't need to hurry if the time was wrong.

We chatted a bit and decided to push this step to the future.

What I want to tell you with this is... please don't push others into things they didn't even wanted in the first place.
I got carried away and stressed a good person out. This could and should have been avoided in the first place.

### What I'm currently working on behind the doors ###
Work never ends, and I loaded more then enough onto myself in the past months.
So much that I can barely keep up, especially since I always find new tasks that get added to the list.

With that being said, I'm a big fan of having full control over something.
That's why I'm, currently working on a new, self-coded socials page for her.
A homepage is planned too, but is not worked on yet.

This way, I can implement whatever I want and connect a domain to it.

Reason I got the idea in the first place was, so that I'd be able to embet things like spotify or her latest Instagram posts into the website.

The code is currently in a private repository, but when I'm finished and happy with the end product, it's going public.
Not too sure about the License type I'm gonna choose, but I don't think I'm gonna use something with much restriction.

MIT License doesn't feel right, but I don't want to restrict y'all so maybe I just go with that.

## About the artist ##
``Her YouTube description:``
Hey I'm Ronan Fae. 
I'm a singersonwriter from Gemany, who likes cats and dying their hair fun colours.
I write music for the mentally unstable and the queers (for obvious reasons👽🏳️‍🌈).

I hope my music helps you a little to not feel alone with your struggles. You are loved and your feelings are valid!

I used to post a lot of covers and originals on my channel and sometimes a few other random, silly little 'vlogalike' videos.
right now my channel might be a little sleepy, but ... not dead and I WILL BE BACK (the more time I have, the more I'll be back)

btw stream my new song Faking It!
https://distrokid.com/hyperfollow/ronja/faking-it


Stay healthy, stay hydrated and don't forget to subscribe.
Sincerly, the happy potato next door!

### How I got to know here ###
Back when I still had TikTok, I just scrolled through my FYP (For you page) and saw a post of her.
Specifially, it was her sining the song **Faking it**.

Normally I'm not really into such "Mental struggle" music, but somehow her song catched me.
I looked for her spotify and listend to a few songs... They were great!

Then I decided to not only follow her there, but also on some other social media plattforms.

So yeah, even tho I really dislike TikTok, I'm really happy that I had it back then. Otherwise I might have never found her.

### What kind of music does she make ###
She mostly does music covering mental health.
I know, not a lot of words, but she covers so many aspects in this topic alone, that I just don't know how to  describe it any better.
It helped me in a dark phase and will definitly help you, even if you just feel loneley or misunderstood.

But I think even someone who's perfectly fine will find some joy in her music.

On her Discord server, she sometimes shares some snippets of work in progress songs.
Definitly check it out, link comes a bit later in this post.

### Why I like it and what my favorite song is ###
As mentioned above, I was in a very dark place a few years ago and it got really dangerous is you know what I mean.
But I'll cover this in another blog post, so stay tuned.

Tho I think that's enough explanation for you to see how it helped me.
It wasn't really that I could relate to what she sang, a bit but not complety, but way more that I felt some comfort in the music.

It gave me the feeling of being understood and accepted. Something I didn't think I'd deserve.

Whenever I had the chance to, I would listen to her music.

But one song in particular catched me and ironicly it was the first song I ever heard from her, Faking it.

I can't even describe what that song has, but it just made me feel so much better again.

**If you read this Ronja**, thank you. From the bottom of my heart. Thank you.

### How and where you can find her ###
You can find all her socials under [socials.ronanfae.com](https://socials.ronanfae.com).
There is a tiny UI bug if you open the website on mobile, but sadly I can't do anything about it since I neither host the site nor have the knowledge to fix the theme.

If you want to talk with her and her community directly, she also has a Discord Server called [Chaos Caven](https://discord.gg/MTR24FFe).

## Words from Ronja herself ##
Asked Ronja if she wants to say something, but have not recieved a reply yet.
