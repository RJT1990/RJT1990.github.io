## Making a Dystopian AI Roleplaying Game

I wanted to do something fun for my 30th birthday - last September - so I hacked together a dystopian AI roleplaying in a week. It involved "fake" documentaries detailing events up to 2027, an in-game social experiment with real money and prizes, scavenger hunt style mechanics, and a Telegram bot app where people could participate in and get updates on the game.

It involved around 8-12 people and the engagement was super high; people seemed to engage every 15-30 minutes, including weekends. This post outlines my learnings and some of the fun details on how it worked.

## Plot

The plot setting was a world five years in the future (2027) where a company called Kobashi Systems "solves" AI -- but in the process creates a deeply unequal society between engineers and non-engineers. I assumed that the future of AI is supervised learning - which is obviously incorrect given progress in self-supervised learning - but it made for a really clean class division between engineers and labellers. So I took some creative liberties to make a good story.

To immerse players in the world I video edited a fake 10 minute documentary on how events unfolded. I took clips from other documentaries and spliced them together to make it look like interviewees were talking about events in the future. I also paid a good documentary voiceover actor on Fiverr, and took some footage from Pexels, Shutterstock and some other sources. You can view the documentary here: 

https://www.youtube.com/watch?v=FJ_RYQ61qQk 

The reaction to the video from friends was really strong. I think this worked because:

- The fake documentary format works really well.
- The choice of musical score was good - Phillip Glass, Hans Zimmer, et al.
- Narrative was timely - post-pandemic, people wondering what would happen next.
- Involving my friends in the video made them part of a big story.

The key themes I wanted to get across were how technology can shape social relations and how ownership of technology creates power. I also introduced elements of mystery, e.g. the founder Hiroshi Kobashi being missing, and an underground group known as the "Seekers" who are fighting against the company.

I also produced two additional videos to immerse people in the world. I made a deliberately cringeworthy (and creepy) hiring video for Kobashi Systems. As well as a commercial for a fictional energy drink Labella, which is an energy drink targeted at labellers to improve their productivity...

For fun, I also made Dogecoin the default currency in the game.

## Company Induction

To begin the game, players are assigned a job at Kobashi Systems as either a labeller or an engineer. To immerse my friends in the world, I sent them through a "company induction" (via Telegram app) and sent them boxes with company swag -- containing letters, t-shirts, food, and more.

Sending people real stuff seemed to work well and added to the immersion that they were actually joining a company. I've shared some pictures below:

<br />

<p>
  <img src="https://rjt1990.github.io/images/nat.jpg" width=250>
  <img src="https://rjt1990.github.io/images/mikkelgoods.jpeg" width=250>
</p>

<br />


I also got customized cyberpunk based pictures made of the players, to again make them feel more immersed in the new world.

## The Telegram App

I made a Telegram bot of an ingame "phone" where players could receive messages, calls, check the news, check their bank balance, and more. You can see this below:

This worked really well as a place where people could check-in and see what was happening in the game. What especially worked well was the messaging system, and pushing messages to players. 

After the company induction, the first thing the player received is a video phone call from a famous person congratulating on their new job at Kobashi and wishing them a happy 2027. This was probably the priciest part of the game, but it worked really well as a "holy shit" moment. You can view a few of these below:

---


## Kobashi E-Store

I made a lightweight store where people could use their "Doge" to buy items, which were *actually sent* to their address when ordered. This again really added to the immersion and feeling that things were real -- even if the items were shitty things like energy drinks! People soon started posting their orders on the general chat, and the memes flourished:

---

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


