## 2027: A Dystopian AI RPG

<p align="center">
  <img src="https://rjt1990.github.io/images/kobashihf.gif" width="100%">
</p>

<br />

I hacked together a dystopian AI RPG in a week for my 30th birthday party. It involved spoof documentaries, a social experiment with real money, scavenger hunt sidequests, and a Telegram bot as the game interface.

The game had 8-12 players and engagement was very high: we all had fun! This blog post details how the game worked, how it played out, and my learnings from building this side project.

<br />

## Plot

The setting was 2027 where a company called Kobashi Systems "solves" AI. But the rise of AI creates social problems and society self-organizes arounds two classes: those who train AI models (**engineers**) and those who make data for AI models (**labellers**).

To immerse players in game world, I made a spoof documentary about how events unfolded. I took clips from other documentaries and spliced them together to make it look like interviewees were talking about events in the future. I also found an [amazing voiceover narrator on Fiverr](https://www.fiverr.com/provotalent/narrate-your-documentary-with-my-american-male-voice), and took some footage from Pexels, Shutterstock and some other sources. You can view the documentary here: 

<br />

<p align="center">
  <a target="_blank" href="https://www.youtube.com/watch?v=h3Fg04f-wE8"><img src="https://rjt1990.github.io/images/youtube.png" width="100%"></a>
  <br>
  <a target="_blank" href="https://www.youtube.com/watch?v=h3Fg04f-wE8">chapter one: ̷t̷h̷e̷ ̷b̷e̷g̷i̷n̷n̷i̷n̷g̷</a>
</p>

<br />

Player reaction to the video was really strong, for a number of reasons:

- **Mockumentary format** - This really aided immersion. Friends thought I might have deepfaked it, or that I'd actually interviewed people like Jordan Peterson!
- **Timely narrative** - People are especially curious about the future right now with the pandemic, which made it easier to step into a potential future
- **Choice of music** - Phillip Glass and Hans Zimmer tapped into emotions; the synth tracks from Perturbator and The Encounter sold the cyberpunk vibe
- **Turning friends into heroes** - Having video clips of friends in the documentary alongside the big story made them feel special  

Special thanks to [Matt Clifford](https://twitter.com/matthewclifford) who agreed to my (unreasonable!) request to provide a clip talking about Kobashi Systems, as if it were a company from the [Entrepreneur First](https://www.joinef.com) programme!

The key themes I wanted to get across were how technology can shape social relations and how ownership of technology creates power. I also introduced elements of mystery, e.g. the founder Hiroshi Kobashi being missing, and an underground group known as the "Seekers" who are fighting against the company. At a macro level, I found rereading the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey) helpful for storyboarding. The main structural insight I exploited was this idea of transitioning from an "Old World" to the "New World". This was timely given the pandemic -- and it played into the sense we are transitioning to a new world post-pandemic.

To further aid immersion, I produced two additional videos for the story. I made a deliberately cringeworthy [hiring video for Kobashi Systems](https://youtube.com/watch?v=_TteD56RDPA). I also made a [commercial for a fictional beverage La Bella](https://www.youtube.com/watch?v=VbIw6u9tW_M): an energy drink targeted at labellers to improve their productivity...

<br />

<p align="center">
  <a target="_blank" href="https://www.youtube.com/watch?v=VbIw6u9tW_M"><img src="https://rjt1990.github.io/images/labella.gif" width="100%"></a>
  <br>
  <a target="_blank" href="https://www.youtube.com/watch?v=VbIw6u9tW_M">Labels fuel the models, La Bella fuels the humans</a>
  <br />
  <span style="font-size:10px"><i>Credit to <a target="_blank" href="https://commons.wikimedia.org/wiki/File:%22Evolution%22_and_life_in_vaporwave_flavours._(48475685782).png">Daniel Oliva Barbero</a> for the image adapted for this fictional drink</i></span>

</p>

<br />

For fun, I made Dogecoin the default currency in the game. Although this wasn't actual Dogecoin...balances and transactions were stored in a SQLite DB on a local machine. Apologies to blockchain enthusiasts.

<br />

## 👋 Welcome to Kobashi

To begin the game, players were assigned a job at Kobashi Systems as either a **labeller** or an **engineer**. Their first task was to complete a "company induction" (via the Telegram app) and they were sent company swag boxes. The swag boxes contained t-shirts, a welcome letter, stickers, food and more.

The Kobashi induction was a spoof of Silicon Valley company inductions. The content served a dual-purpose: (a) making my friends feel like they were joining a real tech company (*immersion*), and (b) introducing people to the Telegram bot UX (*mechanics*).

<br />

<p>
  <a target="_blank" href="https://rjt1990.github.io/images/valuesnew.jpeg"><img src="https://rjt1990.github.io/images/valuesnew.jpeg" width="100%"></a>
  <br>
</p>

Players *loved* the swag boxes. People get high utility from physical goods that are tied to a digital product. It's a lesson that should be applied for real startups, especially if you are building communities. Send out swag to your contributors! I've shared pictures below of happy new Kobashi employees:

<br />

<p>
  <a target="_blank" href="https://rjt1990.github.io/images/nat.jpg"><img src="https://rjt1990.github.io/images/nat.jpg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/samwshirt.jpg"><img src="https://rjt1990.github.io/images/samwshirt.jpg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/mikkelgoods.jpg"><img src="https://rjt1990.github.io/images/mikkelgoods.jpeg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/mercharrive1.jpeg"><img src="https://rjt1990.github.io/images/mercharrive1.jpg" width="100%"></a>
  <a target="_blank" href="https://rjt1990.github.io/images/swagarrives.png"><img src="https://rjt1990.github.io/images/swagarrives.png" width="100%"></a>
</p>

<br />

To further aid immersion, I got cyberpunk profile pictures made of the players. Some of these profile pictures came out really well:

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/mario.jpg"><img src="https://rjt1990.github.io/images/mario.jpg" width="50%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/hana.jpg"><img src="https://rjt1990.github.io/images/hana.jpg" width="50%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/mikkel.jpg"><img src="https://rjt1990.github.io/images/mikkel.jpg" width="50%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/natasha.jpg"><img src="https://rjt1990.github.io/images/natasha.jpg" width="50%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/nish.jpg"><img src="https://rjt1990.github.io/images/nish.jpg" width="50%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/samw.jpg"><img src="https://rjt1990.github.io/images/samw.jpg" width="50%"></a>
</p>

<br />

## ✨ The Magic Moment

A few years ago, I was really influenced by a [talk on YouTube by Alex Schultz](https://youtu.be/URiIsrdplbo?t=719). He talks about the idea of a product's **magic moment** -- the moment when things click for the user. For example, on Facebook, the magic moment is seeing friends and following how their lives progress. A core product goal is to get new users to that moment ASAP so they understand the key product value.

I needed a magic moment after the induction for my game. My friends needed to buy into the "New World" and leave the real world behind. This is a key structural moment in the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey), when the hero leaves the ordinary world and crosses the threshold. I needed my friends cross the first threshold in the game!

My device was to use celebrity video calls to the players through the Telegram app. The player would receive an incoming call - a video - and it would be a celebrity congratulating them on their new job at Kobashi and wishing them a happy 2027. This not only achieved a holy shit moment, but it tied that experience to the game and the New World. It was the trigger to leave the old world behind...and to get fully engaged with the game.

The means to achieving this were Cameo and some video editing. This was the most expensive bit of the project, but my friends *loved* it, and it really got them engaged going forward - so objective achieved! You can view some of the "video calls" below, staring Lindsay Lohan, Steve Wozniak, Chris Diamantopoulos (Russ Hanneman from HBO's Silicon Valley), Tony Hawk, and Christopher Lloyd (Doc Brown from Back to the Future).

<br />

<p align="center">
  <a target="_blank" href="https://www.youtube.com/watch?v=hSsGNXEjdIU"><img src="https://rjt1990.github.io/images/lindsaylohan.png" width="50%"></a>
  <a target="_blank" href="https://www.youtube.com/watch?v=emsDE20YoHE"><img src="https://rjt1990.github.io/images/stevewozniak.png" width="50%"></a>
  <a target="_blank" href="https://www.youtube.com/watch?v=f2TTYJ376EQ"><img src="https://rjt1990.github.io/images/russhanneman.png" width="50%"></a>
  <a target="_blank" href="https://www.youtube.com/watch?v=bYiuRpHpoKo"><img src="https://rjt1990.github.io/images/tonyhawk.png" width="50%"></a>
  <a target="_blank" href="https://www.youtube.com/watch?v=4b9EIeGuS4A"><img src="https://rjt1990.github.io/images/docbrown.png" width="50%"></a>
</p>

<br />

## 📱 The Telegram App

With the immersion stage finished, the next stage was the core game mechanics. Players had an in-game phone where they could stay updated with the game and participate in daily activities:

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/phoneinterface.jpg"><img src="https://rjt1990.github.io/images/phoneinterface.jpg" width="100%"></a>
</p>

<br />

The core features were:

- 👩‍💻 Work: where you earned in-game money (see following sections)
- 🛒 Store: where you could buy real-life items with earnings (see following sections)
- ✉️ Mail: where you received messages from non-playable characters
- 🏦 Bank: where you could see your in-game balance
- 📰 News: where you could read daily news reports in 2027
- 👥 Friends: where you could view profiles of people you met in the game
 
This bot was easy to develop thanks to excellent [Telegram libraries](https://pypi.org/project/python-telegram-bot/) for Python. 

The phone medium was very effective for immersion. Something about the messaging interface made the game feel real. The game mechanics, covered shortly, were a mixture of push and pull; some actions were done on the player's own initiative, others were prompted through push notifications. As a whole, the bot implementation was hacky, given time constraints, but it worked reliably enough for the course of the game.

<br />

## 👩‍ Work


<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/ultimatumggame.jpeg"><img style="border: 0" src="https://rjt1990.github.io/images/ultimatumgame.jpeg" width="100%"></a>
  
  <span style="font-size:14px"><i>Credit to <a target="_blank" href="https://thenib.com/the-ultimatum-game-4af0e8c7e365/">Zach Weinersmith</a> for this comic series explaining the Ultimatum Game</i></span>

</p>

<br />

To recap, the core class divide in 2027 was between engineers and labellers, and there were extremely high levels of inequality. So how best could I convey this tension through the game?

I knew about the [Ultimatum](https://en.wikipedia.org/wiki/Ultimatum_game) and [Dictator](https://en.wikipedia.org/wiki/Dictator_game) games. These are economic experiments that show people have intrinsic preferences for fairness: people will reject unfair splits even it is costly to do so! This seemed like a good setup to manifest issues of inequality, so I designed a modified ultimatum game. Here is how it worked:

1. Each labeller is paired with an engineer for a daily job. Each job has a bounty, e.g. 10 Doge. Only the engineer knows the bounty.
2. Labellers label 5 images a day, for example dogs vs cats. Engineers do not observe the data or this process.
3. Once labelling is done, the engineer "trains" a model on the new data and records an accuracy. Labellers do not observe this process.
4. If labelling is perfect, the full bounty is received; if partially correct, a fraction of the bounty is received; if no labels are correct: no bounty. Labelling quality is signalled through the model accuracy that the engineer observes after "training the model".
5. The engineer allocates a fraction of the bounty to the labeller. The labeller is notified of the amount they receive once allocated - but not the amount the engineer receives!
6. The labellers are lied to by the game: they are told pay is "divided fairly according to AGI".

Step five is where rational choice theory says the engineer should take all of the bounty and pay the labeller $\epsilon > 0$. That's where things get interesting...

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/ultimatumggame2.jpeg"><img style="border: 0" src="https://rjt1990.github.io/images/ultimatumgame2.jpeg" width="100%"></a>
  
  <span style="font-size:14px"><i>Credit to <a target="_blank" href="https://thenib.com/the-ultimatum-game-4af0e8c7e365/">Zach Weinersmith</a></i></span>

</p>

<br />

Here is an example of a **labeller** doing their daily task:

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/labelprocess.gif"><img src="https://rjt1990.github.io/images/labelprocess.gif" width="60%"></a>
</p>

<br />

And here is an **engineer** "training" a new model, and deciding how to split the bounty:

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/trainingprocess.gif"><img style="border: 0" src="https://rjt1990.github.io/images/trainingprocess.gif" width="60%"></a>
</p>

<br />

[Asymmetric information](https://en.wikipedia.org/wiki/Information_asymmetry) created intriguing game elements that fired up controversy and suspicion:

- **Labellers do not observe the the total bounty**: engineers can potentially get away with paying labellers less
- **Engineeers do not observe the labelling process**: engineers do not know how long labelling takes, or the type of data being annotated (e.g. military data)
- **Labellers do not observe the training process**: labellers do not observe the engineer's training process (and the lack of effort required)

This mini-game was the heart of the game. Using the [Hero's Journey](https://en.wikipedia.org/wiki/Hero%27s_journey) structure, this is the **Road of Trials** where players become acclimatized to the New World, but also have the first challenges fighting the system...

We'll cover what actually happened shortly, but first, what was that money actually used for?

<br />

## 🛒 Kobashi E-Store

I made a lightweight store where people could use their "Doge" to buy items, which were *actually sent* to them when ordered. Here are the items that were available:

<br />

<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/estore.jpg"><img src="https://rjt1990.github.io/images/estore.jpg" width="100%"></a>
</p>

<br />

Translating this to 2021 products...

- 🥤 LaBella: Carobao Mixed Berry energy drink
- 🍫 Chocomodels: Ferrero Rocher
- 👱‍♀️ Pavlovian Conditioner: TRESemmé hair conditioner
- 🔈 Kobashi Home System: Amazon Echo Dot
- 🤖 Marvin Multipurpose Robot: probably a Roomba
 
The store was another holy shit moment for people. When they ordered items, they were actually delivered! This added to the immersion -- even if the items were cheap things like energy drinks! People soon started posting their orders on the general chat, and the memes flourished:

<br />

<p>
  <a target="_blank" href="https://rjt1990.github.io/images/labella1.jpg"><img src="https://rjt1990.github.io/images/labella1.jpg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/labella2.jpeg"><img src="https://rjt1990.github.io/images/labella2.jpeg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/labella3.jpeg"><img src="https://rjt1990.github.io/images/labella3.jpeg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/labella4.jpeg"><img src="https://rjt1990.github.io/images/labella4.jpeg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/labella5.jpeg"><img src="https://rjt1990.github.io/images/labella5.jpeg" width="100%"></a>
  <br>
  <a target="_blank" href="https://rjt1990.github.io/images/labella6.jpeg"><img src="https://rjt1990.github.io/images/labella6.jpeg" width="100%"></a>
</p>

<br />

The Store raised the stakes of the game since it made the money earned more real. If you were an engineer, the temptation to screw over labellers to get your Robot became a lot greater...

The Store also had a narrative role as a **Tempting Obstacle*** for the players. In the Hero's Journey, this is a temptation that can lead the hero to stray from the quest. As we'll see, many labellers came close to accepting the status quo because they aspired to get a Robot...

As a whole, funding this element of the game was surprisingly cheap: it cost me circa $100 to fulfil the orders, but player utility seemed much greater than the cash amount. I knew this from experimental economics: if you give a prize (e.g. an iPhone) then this gets more participation than giving the equivalent monetary amount. People value physical things!

<br />

## ✉️ Mail

While the ultimatum mini-game was ongoing, I needed a device to progress the plot. I sent players mysterious calls from the "Seekers". These calls informed players of Kobashi's questionable business activities, and primed them to take down the company. An example of one of these calls is below:

<br />
<p align="center">
  <a target="_blank" href="https://www.youtube.com/watch?v=FLqrafG3WCA"><img src="https://rjt1990.github.io/images/unknowncaller.png" width="50%"></a>
</p>

<br />

I also used mail to perform custom interventions -- stirring the pot -- based on how players were behaving.

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/hiroshi.jpeg"><img src="https://rjt1990.github.io/images/hiroshi.jpeg" width="70%"></a>
</p>

<br />

## 🧩 Puzzles

To add to the intrigue, I included hidden puzzles with the company swag that players received. The idea was that the Seekers had intercepted a Kobashi swag van and planted in ways for the players to contact them. 

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/swagcontents.jpeg"><img src="https://rjt1990.github.io/images/swagcontents.jpeg" width="100%"></a>
  <span style="font-size:12px">Example items for one player: a joker card, a UV light, an encrypted USB stick</span>
</p>

<br />

The core devices used for the puzzles were:

- 🕵️ **UV messages**: hidden on welcome letters and other items
- 🃏 **Decks of cards**: hidden messages on the side - only visible with correct card ordering
- 📖 **Book ciphers**: that reveal a hidden message once decoded
- 🔌 **Encrypted USB sticks**: once decrypted, they contained a keyword hidden in a video

The Labeller puzzle turned out to be especially engaging. Here is how it went down. The first clues were found by shining a UV light on the welcome letters and Joker cards:

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/jokeruv.jpeg"><img src="https://rjt1990.github.io/images/jokeruv.jpeg" width="100%"></a>
</p>
<br />

Each of these messages were of the form "find [x]", and the first task was to find out what these meant. Eventually the players caught onto the fact that the names were nicknames for themselves:

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/decodingnames.jpg"><img src="https://rjt1990.github.io/images/decodingnames.jpg" width="100%"></a>
</p>
<br />

So these nicknames told each player which other player they needed to solve their clues. The first player in the chain was "Hera" -> [Juno](https://www.juno.bio) -> [Hana](https://www.twitter.com/hanebdar). Hana had a book [Leviathan](https://en.wikipedia.org/wiki/Leviathan_(Hobbes_book)) that came with a note of numbers:

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/leviathanorder.jpg"><img src="https://rjt1990.github.io/images/leviathanorder.jpg" width="100%"></a>
</p>
<br />

By using the UV light on the respective page numbers of the book, this revealed a word (which corresponded to a card number):

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/kingclue.jpeg"><img src="https://rjt1990.github.io/images/kingclue.jpeg" width="100%"></a>
</p>
<br />

Decoding the numbers...

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/cardorderingtext.jpg"><img src="https://rjt1990.github.io/images/cardorderingtext.jpg" width="100%"></a>
</p>
<br />

This was then communicated to Lim -> 林 -> Hayashi -> [Mario](https://twitter.com/logicalicy):

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/ihaveaclue.jpg"><img src="https://rjt1990.github.io/images/ihaveaclue.jpg" width="100%"></a>
</p>
<br />

Mario then stacked up the cards...

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/cardordering.jpg"><img src="https://rjt1990.github.io/images/cardordering.jpg" width="100%"></a>
</p>
<br />

And shining a UV light on the side revealed a message:

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/kyoto.jpg"><img src="https://rjt1990.github.io/images/kyoto.jpg" width="100%"></a>
</p>
<br />

Kyoto! The final player Sam had an encrypted USB stick and an instruction on the welcome letter:

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/latitude.jpg"><img src="https://rjt1990.github.io/images/latitude.jpg" width="100%"></a>
</p>
<br />

Putting in the latitude of Kyoto and applying the modifier...

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/usbreveal.gif"><img src="https://rjt1990.github.io/images/usbreveal.gif" width="100%"></a>
</p>
<br />

Bingo. On the USB stick was a clip from Lost in Translation with the word "serenity" embedded in the ending. This would be a keyword used later in the plot.

This puzzle sidequest worked really well. One mistake I made was not tying the final clue to the main plot significantly enough. But players clearly got a lot of intrinsic utility from just solving the puzzles. I was careful not to make the puzzles too difficult, because the goal was to facilitate communication between players (and advance the plot) -- not an IQ test.

## ⛰️ The Story

So how did things go down?

The beginning of the game was a honeymoon period where engineers and labellers got along. Everyone was enjoying the experience of ordering items from the Kobashi E-Store. The joys of consumerism...

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/honeymoon.jpg"><img src="https://rjt1990.github.io/images/honeymoon.jpg" width="100%"></a>
</p>
<br />

Things changed when the swag arrived. I set up two separate chats for labellers and engineers. Each team had a puzzle to solve from their swag. But separate communication channels also began to divide the players...This was important because the labellers would sooner or later realize they were being screwed.

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/labeller_hi.jpg"><img src="https://rjt1990.github.io/images/labeller_hi.jpg" width="100%"></a>
</p>
<br />

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/engineer_hi.jpg"><img src="https://rjt1990.github.io/images/engineer_hi.jpg" width="100%"></a>
</p>
<br />

The first signs of suspicion came when Mikkel (an engineer) posted a photo of Ferrero Rocher on the general chat. Labellers could only afford energy drinks with their pay, so this was a little suspect...

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/ferror1.jpg"><img src="https://rjt1990.github.io/images/ferror1.jpg" width="100%"></a>
  <a target="_blank" href="https://rjt1990.github.io/images/ferror2.jpg"><img src="https://rjt1990.github.io/images/ferror2.jpg" width="100%"></a>
</p>
<br />

To escalate tensions further, I changed the training data. Previously this had been innoucous tasks like dogs vs cats and chihuahuas vs muffins. This was changed to (mocked) military data: satellite photos of planes, tanks, and so on:

<br />
<p align="center">
  <a target="_blank" href="https://i2-prod.mirror.co.uk/incoming/article6497151.ece/ALTERNATES/s1200c/Fighter-satellite-main.jpg"><img src="https://i2-prod.mirror.co.uk/incoming/article6497151.ece/ALTERNATES/s1200c/Fighter-satellite-main.jpg" width="100%"></a>
</p>
<br />

Many labellers refused to label the data given the contents. But they did not communicate the type of data to the engineers! So engineers got bad training data, and they assumed the poor labels were due to laziness or incompetence!

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/angryengineers.jpg"><img src="https://rjt1990.github.io/images/angryengineers.jpg" width="100%"></a>
</p>
<br />

Labellers in turn got punished with low payouts. Labellers then began to discuss the situation and share their compensation...and the truth became clearer. They soon realized one engineer (Mikkel) was being particularly unfair and paying them a lot less!

<br />
<p align="center">
  <a target="_blank" href="https://rjt1990.github.io/images/labeller_rev_1.jpg"><img src="https://rjt1990.github.io/images/labeller_rev_1.jpg" width="100%"></a>
  <a target="_blank" href="https://rjt1990.github.io/images/labeller_rev_2.jpg"><img src="https://rjt1990.github.io/images/labeller_rev_2.jpg" width="100%"></a>
  <a target="_blank" href="https://rjt1990.github.io/images/labeller_rev_3.jpg"><img src="https://rjt1990.github.io/images/labeller_rev_3.jpg" width="100%"></a>
</p>
<br />


....TBC (when I have time to write up)
