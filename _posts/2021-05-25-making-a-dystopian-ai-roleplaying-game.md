## 2027: A Dystopian AGI RPG

I hacked together a dystopian AGI RPG in a week for my 30th birthday party. It consisted of spoof documentaries, a social experiment with real money and prizes, scavenger hunt plots, and an interactive Telegram bot that managed the game.

It involved 8-12 people and engagement was high: players engaged every 15-30 minutes, including weekends. This post details my learnings and some of the fun involved in the week of events!

## Plot

The setting was 2027 where a company called Kobashi Systems "solves" AGI. But the post-AGI world is deeply unequal and there is a strong class divide between engineers and non-engineers. I assumed the AI of the future is heavily supervised - obviously incorrect given [progress in self-supervised learning](https://twitter.com/an_open_mind/status/1396057486940114945?s=20) - but it made for a clean class division between engineers and labellers. So I took some creative liberties to write a good story! Suspend your disbelief, ML researchers 🙂.

To immerse players in the new world, I video edited a spoof documentary on how events unfolded. I took clips from other documentaries and spliced them together to make it look like interviewees were talking about events in the future. I also found an [amazing voiceover narrator on Fiverr](https://www.fiverr.com/provotalent/narrate-your-documentary-with-my-american-male-voice), and took some footage from Pexels, Shutterstock and some other sources. You can view the documentary here: 

<br />

<p align="center">
  <a href="https://www.youtube.com/watch?v=h3Fg04f-wE8"><img src="https://rjt1990.github.io/images/youtube.png" width="100%"></a>
  <br>
  <a href="https://www.youtube.com/watch?v=h3Fg04f-wE8">chapter one: ̷t̷h̷e̷ ̷b̷e̷g̷i̷n̷n̷i̷n̷g̷</a>
</p>

<br />

The reaction to the video was really strong. What worked well was:

- **Mockumentary format** - This is really effective for immersion. Friends thought I might have deepfaked it, or that I'd actually interviewed people like Jordan Peterson!
- **Timely narrative** - Post-pandemic uncertainty, and curiosity about where things might go. This made people more willing to jump into the "new world" because there was a realism and relevance to it.
- **Good musical score** - Phillip Glass and Hans Zimmer worked really well for tapping into emotions. The synth tracks from Perturbator and The Encounter also worked well to sell the cyberpunk vibe. It all blended together really nicely.
- **Friends felt like heroes** - putting clips of friends in the video made them feel part of a big story (and made them feel special).

Also special thanks to [Matt Clifford](https://twitter.com/matthewclifford) who agreed to my (unreasonable!) request to provide a clip talking about Kobashi Systems, as if it were a company from the [Entrepreneur First](https://www.joinef.com) programme!

The key themes I wanted to get across were how technology can shape social relations and how ownership of technology creates power. I also introduced elements of mystery, e.g. the founder Hiroshi Kobashi being missing, and an underground group known as the "Seekers" who are fighting against the company. At a macro level, I found rereading the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey) helpful for storyboarding. The main structural insight I exploited was this idea of transitioning from an "Old World" to the "New World".

I also produced two additional videos to immerse people in my world. I made a deliberately [cringeworthy hiring video for Kobashi Systems](https://youtube.com/watch?v=_TteD56RDPA). More crazily, I made a commercial for a fictional energy drink Labella, which is an energy drink targeted at labellers to improve their productivity...

<br />

<p align="center">
  <a href="https://www.youtube.com/watch?v=VbIw6u9tW_M"><img src="https://rjt1990.github.io/images/labella.gif" width="100%"></a>
  <br>
  <a href="https://www.youtube.com/watch?v=VbIw6u9tW_M">Labels fuel the models, Labella fuels the humans</a>
  <i>Credit to <a href="https://commons.wikimedia.org/wiki/File:%22Evolution%22_and_life_in_vaporwave_flavours._(48475685782).png">Daniel Oliva Barbero</a> for the image adapted for this fictional drink</i>

</p>

<br />

For fun, I also made Dogecoin the default currency in the game. But not actual Dogecoin...just balances stored in a SQLite DB on a local machine. Apologies to blockchain enthusiasts for this sacrilege.

## Company Induction

To begin the game, players are assigned a job at Kobashi Systems as either a labeller or an engineer. To immerse my friends in the world, I sent them through a "company induction" (via Telegram app) and sent them boxes with company swag -- containing letters, t-shirts, food, and more.

Sending people real stuff seemed to work well and added to the immersion that they were actually joining a company. I've shared some pictures below:

<br />

<p>
  <a href="https://rjt1990.github.io/images/nat.jpg"><img src="https://rjt1990.github.io/images/nat.jpg" width="100%"></a>
  <br>
  <a href="https://rjt1990.github.io/images/mikkelgoods.jpeg"><img src="https://rjt1990.github.io/images/mikkelgoods.jpeg" width="100%"></a>
</p>

<br />


I also got customized cyberpunk based pictures made of the players, to again make them feel more immersed in the new world.

## The Telegram App

<br />

<p align="center">
  <a href="https://rjt1990.github.io/images/phoneinterface.jpg"><img src="https://rjt1990.github.io/images/phoneinterface.jpg" width="100%"></a>
</p>

<br />
I made a Telegram bot of an ingame "phone" where players could receive messages, calls, check the news, check their bank balance, and more. You can see this below:

This worked really well as a place where people could check-in and see what was happening in the game. What especially worked well was the messaging system, and pushing messages to players. 

After the company induction, the first thing the player received is a video phone call from a famous person congratulating on their new job at Kobashi and wishing them a happy 2027. This was probably the priciest part of the game, but it worked really well as a "holy shit" moment. You can view a few of these below:

---


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


