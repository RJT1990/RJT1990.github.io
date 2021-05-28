## 2027: A Dystopian AGI RPG

<p align="center">
  <img src="https://rjt1990.github.io/images/kobashi.gif" width="100%">
</p>

<br />

I hacked together a dystopian AGI RPG in a week for my 30th birthday party. It involved spoof documentaries, a social experiment with real money, scavenger hunt sidequests, and a Telegram bot as the game interface.

The game had 8-12 players and engagement was very high: players engaged every 15-30 minutes, including weekends. This blog post details how the game worked, how it played out, and my learnings from building this product.

## Plot

The setting was 2027 where a company called Kobashi Systems "solves" AGI. The rise of AGI creates social problems, however, and society self-organizes arounds two classes: those who train models (**engineers**) and those who provide data for models (**labellers**). The implicit assumption here is that machine learning remains heavily supervised. This is obviously incorrect given [progress in self-supervised learning](https://twitter.com/an_open_mind/status/1396057486940114945?s=20), but this assumption enabled a clean class divide between engineers and labellers. This was good for the story I wanted to write! So suspend your disbelief, ML researchers 🙂.

To immerse players in game world, I made a spoof documentary about how events unfolded. I took clips from other documentaries and spliced them together to make it look like interviewees were talking about events in the future. I also found an [amazing voiceover narrator on Fiverr](https://www.fiverr.com/provotalent/narrate-your-documentary-with-my-american-male-voice), and took some footage from Pexels, Shutterstock and some other sources. You can view the documentary here: 

<br />

<p align="center">
  <a href="https://www.youtube.com/watch?v=h3Fg04f-wE8"><img src="https://rjt1990.github.io/images/youtube.png" width="100%"></a>
  <br>
  <a href="https://www.youtube.com/watch?v=h3Fg04f-wE8">chapter one: ̷t̷h̷e̷ ̷b̷e̷g̷i̷n̷n̷i̷n̷g̷</a>
</p>

<br />

The reaction to the video was really strong from players. It was effective for several reasons:

- **Mockumentary format** - Really aided immersion. Friends thought I might have deepfaked it, or that I'd actually interviewed people like Jordan Peterson!
- **Timely narrative** - Post-pandemic uncertainty means people are especially curious about the future in 2021. This made people more willing to imagine the "new world" as a potential future (and immerse themselves in it).
- **Choice of music** - Phillip Glass and Hans Zimmer worked well to tap into emotions. The synth tracks from Perturbator and The Encounter also worked to sell the cyberpunk vibe.
- **Turning Friends into Heroes** - Having video clips of friends in the documentary alongside the big story made them feel special.  

Also special thanks to [Matt Clifford](https://twitter.com/matthewclifford) who agreed to my (unreasonable!) request to provide a clip talking about Kobashi Systems, as if it were a company from the [Entrepreneur First](https://www.joinef.com) programme!

The key themes I wanted to get across were how technology can shape social relations and how ownership of technology creates power. I also introduced elements of mystery, e.g. the founder Hiroshi Kobashi being missing, and an underground group known as the "Seekers" who are fighting against the company. At a macro level, I found rereading the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey) helpful for storyboarding. The main structural insight I exploited was this idea of transitioning from an "Old World" to the "New World". This was especially timely given the current pandemic, and the sense we are transitioning to a new regime where old rules will no longer apply.

To further aid immersion, I produced two additional videos for the story. I made a deliberately [cringeworthy hiring video for Kobashi Systems](https://youtube.com/watch?v=_TteD56RDPA). I also made a commercial for a fictional beverage Labella: an energy drink targeted at labellers to improve their productivity...

<br />

<p align="center">
  <a href="https://www.youtube.com/watch?v=VbIw6u9tW_M"><img src="https://rjt1990.github.io/images/labella.gif" width="100%"></a>
  <br>
  <a href="https://www.youtube.com/watch?v=VbIw6u9tW_M">Labels fuel the models, Labella fuels the humans</a>
  <br />
  <span style="font-size:10px"><i>Credit to <a href="https://commons.wikimedia.org/wiki/File:%22Evolution%22_and_life_in_vaporwave_flavours._(48475685782).png">Daniel Oliva Barbero</a> for the image adapted for this fictional drink</i></span>

</p>

<br />

For fun, I made Dogecoin the default currency in the game. But not actual Dogecoin...balances and transactions were stored in a SQLite DB on a local machine. Apologies to blockchain enthusiasts.

## Welcome to Kobashi

To begin the game, players are assigned a job at Kobashi Systems as either a **labeller** or an **engineer**. To immerse my friends, they completed a "company induction" (via the Telegram app) and they were sent company swag boxes -- containing t-shirts, a welcome letter, stickers, food and more.

The Kobashi induction was a spoof of Silicon Valley company inductions. The content served a dual-purpose: (a) making my friends feel like they were joining a real tech company (*immersion*), and (b) introducing people to the Telegram bot UX (*mechanics*).

<br />

<p>
  <a href="https://rjt1990.github.io/images/labels.jpeg"><img src="https://rjt1990.github.io/images/values.jpeg" width="100%"></a>
  <br>
</p>

Players really loved the swag boxes. People place high utility on physical goods. It's a lesson that should be carried forward for real startups, especially if you are building communities. Send out physical goods and swags to your contributors! I've shared pictures below of happy new Kobashi employees:

<br />

<p>
  <a href="https://rjt1990.github.io/images/nat.jpg"><img src="https://rjt1990.github.io/images/nat.jpg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/mikkelgoods.jpg"><img src="https://rjt1990.github.io/images/mikkelgoods.jpeg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/mercharrive1.jpeg"><img src="https://rjt1990.github.io/images/mercharrive1.jpg" width="100%"></a>
  <a href="https://rjt1990.github.io/images/mercharrive2.jpeg"><img src="https://rjt1990.github.io/images/mercharrive2.jpg" width="100%"></a>
</p>

<br />

I also got cyberpunk profile pictures made of the players, to further aid immersion. Some of these came out really well:

<br />

<p align="center">
  <a href="https://rjt1990.github.io/images/mario.jpg"><img src="https://rjt1990.github.io/images/mario.jpg" width="50%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/hana.jpg"><img src="https://rjt1990.github.io/images/hana.jpg" width="50%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/mikkel.jpg"><img src="https://rjt1990.github.io/images/mikkel.jpg" width="50%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/natasha.jpg"><img src="https://rjt1990.github.io/images/natasha.jpg" width="50%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/nish.jpg"><img src="https://rjt1990.github.io/images/nish.jpg" width="50%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/samw.jpg"><img src="https://rjt1990.github.io/images/samw.jpg" width="50%"></a>
</p>

<br />

## The Magic Moment

A few years ago, I was really influenced by a [talk on YouTube by Alex Schultz](https://youtu.be/URiIsrdplbo?t=719). He talks about the idea of a product's **magic moment** -- the moment when things click for the user. For example, on Facebook, the magic moment is seeing friends following how their lives progress. A core product goal is to get new users to that moment ASAP so they understand the key product value.

I needed a magic moment after the induction for my game. My friends needed to buy into the "New World" and leave the real world behind. This is a key structural moment in the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey), when the hero leaves the ordinary world behind. I needed to make my friends cross the first threshold themselves!

My device was to use video calls to the players from celebrities through the Telegram app. The player would receive an incoming call - a video - and it would be a celebrity congratulating them on their new job at Kobashi and wishing them a happy 2027. This not only achievied a holy shit moment, but it tied that experience to the game and the New World with the context of the message. It was the trigger to leave the old world behind...and the trigger to get fully engaged with the game.

The means to achieving this were Cameo and some video editing. This was the most expensive bit of the project, but my friends *loved* it, and it really got them engaged going forward - so objective achieved! You can view some of the "video calls" below, staring Lindsay Lohan, Steve Wozniak, Chris Diamantopoulos (Russ Hanneman from HBO's Silicon Valley), Tony Hawk, and Christopher Lloyd (Doc Brown from Back to the Future).

<br />

<p align="center">
  <a href="https://www.youtube.com/watch?v=hSsGNXEjdIU"><img src="https://rjt1990.github.io/images/lindsaylohan.png" width="50%"></a>
  <a href="https://www.youtube.com/watch?v=emsDE20YoHE"><img src="https://rjt1990.github.io/images/stevewozniak.png" width="50%"></a>
  <a href="https://www.youtube.com/watch?v=f2TTYJ376EQ"><img src="https://rjt1990.github.io/images/russhanneman.png" width="50%"></a>
  <a href="https://www.youtube.com/watch?v=bYiuRpHpoKo"><img src="https://rjt1990.github.io/images/tonyhawk.png" width="50%"></a>
  <a href="https://www.youtube.com/watch?v=4b9EIeGuS4A"><img src="https://rjt1990.github.io/images/docbrown.png" width="50%"></a>
</p>

<br />

## The Telegram App

With the immersion stage finished, the next stage was the core game mechanics. Players had an in-game phone where they could stay up to date with ongoings in the game:

<br />

<p align="center">
  <a href="https://rjt1990.github.io/images/phoneinterface.jpg"><img src="https://rjt1990.github.io/images/phoneinterface.jpg" width="100%"></a>
</p>

<br />

The core features were:

- ✉️ Mail: players received messages from non-playable characters.
- 👩‍💻 Work: where players could earn in-game money (see following sections)
- 🏦 Bank: players had a balance of money they earned in the game
- 🛒 Store: players could buy real-life items with in-game money (see following sections)
- 📰 News: daily news reports in 2027 to give more world context.

This bot was easy to develop thanks to excellent [Telegram libraries](https://pypi.org/project/python-telegram-bot/) for Python. 

The phone medium was very effective for immersion. Something about the messaging interface makes the game feel more real. The actual game mechanics, covered shortly, were a mixture of push and pull. The implementation was hacky, given my time constraints, but it worked reliably enough for the course of the week.


## Kobashi E-Store

I made a lightweight store where people could use their "Doge" to buy items, which were *actually sent* to their address when ordered. This again really added to the immersion and feeling that things were real -- even if the items were shitty things like energy drinks! People soon started posting their orders on the general chat, and the memes flourished:

<br />

<p>
  <a href="https://rjt1990.github.io/images/labella1.jpg"><img src="https://rjt1990.github.io/images/labella1.jpg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/labella2.jpeg"><img src="https://rjt1990.github.io/images/labella2.jpeg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/labella3.jpeg"><img src="https://rjt1990.github.io/images/labella3.jpeg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/labella4.jpeg"><img src="https://rjt1990.github.io/images/labella4.jpeg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/labella5.jpeg"><img src="https://rjt1990.github.io/images/labella5.jpeg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/labella6.jpeg"><img src="https://rjt1990.github.io/images/labella6.jpeg" width="100%"></a>
</p>

<br />


## Work Mini-Game

In order to earn money, players had to play a mini-game which was a variant of the Ultimatum and Dictator games in economics. These games are very effective for showing that people have inbuilt preferences towards equality, which was perfect for a plot that was fundamentally about inequality.

The way it worked was as followers. Labellers had to label 5 images a day - there was an actual in-game labelling app... They were not told how much they would be paid, only that their work would be "evaluated" by the engineers. Meanwhile engineers could not see the data, but were told the total bounty of the job and were told they could give whatever fraction they wanted to the labellers. The jobs had to be completed at 8pm: i.e. labellers label by 8pm, and modellers "train" new models on the data by 8pm. So the TLDR:

- Engineers are the only ones who know the total bounty of the job.
- Engineers can pay labellers whatever they want.
- Labellers can affect the total bounty either by not working (0 bounty) or labelling poorly (fraction of total bounty).

What happened in practice was as follows. Of the three initial engineers, two paid reasonably fairly (close to 50%) and one optimized for his own self-interest (paid 0-10%). But at the beginning, there was no protest, because everyone could buy *something* from the Kobashi e-store, in particular Labella energy drinks.

As the days went on, it became clearer that engineers were getting better items than labellers. Ferror Rochers ("chocomodels"), not just labella! 

The pivotal moment was when labellers shared their pay with each other in a Labellers Chat group. It was at this moment they realized one engineer in particular was screwing them over:

They responded by calling the engineers out on this in the public chat. The engineers used a number of (hilarious) excuses to justify the situation:

Eventually the labellers got so unhappy they striked for two days without pay. Engineers tried to bring labellers back to the table with fair offers, but trust was lost.

To stir the pot I did a number of things...

First, I "promoted" the engineer who was acting selfishly and made a public announcement about it to promote the ire of the labellers.

Secondly, I made the data labelling more ethically dubious. Instead of labelling dogs vs cats, or chihuahuas vs muffins, I introduced a military data job which had satellite pictures of tanks, fighter planes, etc. This led to 2/3 of the original labellers mislabelling in protest. I "promoted" the one that correctly labelled to "senior labeller" to further sew doubts about the company and its motives.

In the end the mini-game ended when the plot progressed --- tldr, the labellers deliberately mislabel and make all the company's models malfunctions. It would have been recently interesting to see if both groups could have bargained towards a settlement, but unfortunately I did not have the time to play this out.

What is clear in my mind is that introducing money, even if a small amount, really heats things up and gets incentives aligned to play the game. Further still, having the ability to order real things with the in-game money made the game a lot more engaging. In the end I spent less than 100gbp on items that players bought, but to players it felt like a lot more. This is actually a known result in behavioural economics that promising people a physical good instead of the equivalent monetary amount induces more engagement with an experiment. I am still amazed that people seemed to have so much utility for a crappy energy drink in this game!

## Scavenger Hunts

With the swag I sent to players, I used UV pens to scribble secret messages on the welcome letter and other items. I included book ciphers, card ciphers, and encrypted usb sticks. Each clue was dependent on another clue from another player, which was a really nice device for people to work together. It seemed to be a real positive moment for one of the groups when they figured out all the clues and got the answer.

Plot-wise, the answer would be used to trigger an event later in the gane. I feel this part could have been done better -- I could have planned better -- but I feel it was alright given the time constraints I was working under (do everything in a week).

## Misc Elements

I got a voice actor to play a role of a "Seeker" who phones the players and reveals certain plot information to advance the plot -- e.g. informing the labellers that engineers aren't dividing money fairly, pointing them towards bits of the game where they can activate certain things, etc. This worked fairly well -- I think it would have been better if it was a video rather than just audio, but it was a good device.

I also got a voice actor to play the role of a "Kobashi representative" to give public announcements about things, which seemed to work fairly well.

Another misc element was I had an ingame news section so I could flesh out the world story a bit more, and give more context on what was happening in the world around the players (which in turn could inform their decisions).

## Finale

---

## Conclusions

---


