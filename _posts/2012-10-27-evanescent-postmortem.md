---
layout: post
title: Evanescent Post-Mortem
---

I started making video games when I was twelve, starting off with Game Maker 6 and drag and drop, before graduating to GML, and then later onto Flash Actionscript 3. Immediately after moving to Flash, I took the nonsensical option and decided to make a big Flash game right away, which ended up taking up a whole year due to my roller-coaster development path and trial-and-error coding. The big project of mine grew from my fooling around with Flash into a serious endeavor, and eventually became my first truly polished and completed game.

That game is Evanescent, which is [open sourced on Github](https://github.com/dmliao/evanescent), though the source code is an absolute terror.

![](/img/blog/evanescent-postmortem/Evanescent.jpg)

All in all, since I did complete the game, I consider it a success. I had released it expecting nothing more than a few game plays from a few friends, and the satisfaction of having released a game. While it has not seen immense success on the game portals I put it on, I’m overall happy with how things have gone down.

Still, there’s always room for reflection and improvement, and looking back now, Evanescent was a game that had been developed crookedly, with me trying to learn Flash as I went along. Here is some of my insight on having made this game:

# The Plan

The entire goal of this project was to make a Flash game that would 

1. Have a plot
2. Last more than an hour of gameplay in total. 

From having made too many failed Game Maker games, I realized that I had to plan out what I wanted to do with Evanescent.

The first thing I did was choose an art direction, and make the main player’s sprite. Good looking sprites is a very big motivating factor for me, so having a high-quality sprite early on in development was a priority, just to make sure that I’d want to keep working on it. (This aspect might not apply with everyone, however, just how I work.) It was only after I’d designed the player and HUD that I began to figure out the game mechanics and coding.

Feature creep was going to be a problem, and I knew it; I locked in a set of features very early on in development, and set aside four weapons, HP, boss and enemy types before coding.

![](/img/blog/evanescent-postmortem/week1.jpg)

_Week 1 of developing Evanescent – player and HUD graphics were final, and the movement, weapons, and world-shifting system had been programmed in_

Writing the story also didn’t take much time, and I ended up having a pretty good outline of the game within a month of development – pretty good, considering I was juggling game dev and school.

I began to program enemies, first using programmer art (like that black box in the screenshot above), before moving on to creating some graphics. The entire world-shifting dynamic was a gameplay aspect that I’d really wanted to incorporate into Evanescent, and was pleasantly surprised by how easy it was to program. (I added a boolean variable field to every object and enemy, and set it to true for the colored world and false for the black and white world.)

Very quickly, it seemed like I’d completed a majority of the game. I had enemies, implementations, the whole engine…it was just a matter of putting it all together.

# What took so long, then?

“The last 20% of the game takes 80% of the time” – I’m not sure where I stole that from, but that is unfortunately a very true statement, as I learned the hard way. I’d had an engine, but I still had to design all of the enemies, still had to make the individual levels, and all the menus and transitions. And developing all of that took a long time.

I didn’t have a graphical level editor, so enemy placements were hard-coded in. And so each enemy and level had to be tested, tested, and tested again. Making sure that the timings were right, that no enemies just ran into each other, that no segments of the levels were impossible to beat.

If there’s anything capable of turning me off video games forever, it’d be the sheer amount of testing that’s needed in developing any game. At first, it was exciting to be able to play something I’d built myself, but as time went on, I got tired of seeing the same screens, same enemies over and over again, just tweaking their positions, or timings, or fixing bugs to get everything to work right.

## Lesson #1: Games break a lot in development, and they won’t always look pretty either.

![](/img/blog/evanescent-postmortem/dragon.jpg)

_Trying to get the dragon enemy’s body parts to look right probably took at least an hour or two_

As the game grew bigger, problems also cropped up in my coding, as I’d never really learned proper coding and organizing practice before developing Evanescent.

I had no image archive; images had been stored in the same file system as the enemy classes, and I was building quite a monstrosity of spaghetti code. And then, as I got better at programming, I saw flaws in my own work, saw how much of a mess I’d made out of Evanescent’s code, and tried to fix it.

That also took far too much time.

## Lesson #2: Things that were created several months ago will probably look different from what you make now. 

If you go back and try to fix everything, the project will never be finished.

It took a few nights, in the summer, when I was crazy after having been awake for more than 24 hours at one in the morning, to realize: “Holy crap, I’ve been making this game for several months and I haven’t finished it yet, let’s forget about everything and finish it.”

So I eventually had to leave my perfectionist tendencies aside and accept the fact that most of the engine was a spaghetti code mess, and work on finishing the levels and the cutscenes and wrapping everything in a pretty menu.

All in all, the development process took a year. I had thought it to be a summer’s worth of project, at most.

## Lesson #3: It’s too easy to underestimate the amount of time you need to make something, and to overestimate the amount of time you have to make it.

Even so, in the end, I kept my promise to myself, and finished the damned thing. After I finished it, I didn’t really know what to do with it, so I kind of kept it to myself for about another year, before finally opening the floodgates and releasing it online.

It hasn’t even been a month since I put it on game portals, but I’ve already come to realize what went right and what went wrong with Evanescent:

# The Good

I’ve gotten quite a bit of praise for the graphics and music, which I’m personally proud of. Drawing all of the environments and enemies took a while, as did the music composition, but those were aspects of the game that were very enjoyable to make, so I did not mind the time spent on those assets. I had sought to create a beautiful game, and visually, I have not heard complaints about it.

In addition, my friends all enjoyed Evanescent’s story – it made them think a little, and tied in well with the art style. The game is a little long, and the story spans the entire hour (and maybe a half) of playtime. I’d designed it to be as out-of-the-way as possible, and players can skip the story entirely by pressing enter, but it was nice knowing that some people had appreciated the writing.

Evanescent also lives up to its title: It’s a bullet-hell shooter. And it is difficult. For my friends who liked those kinds of games, it was a fun, whimsical game. For the people who just played casually…it might not be. But it had served its purpose in that sense, and for that, I was satisfied.

# The Bad

I’ve come to realize after making this game that I wasn’t exactly the best at game design. I could program, write, draw, and compose, and make every single aspect of a game, except put it together in a very neat, fun package.

The first problem was the filesize – the original game clocked in at 20 megabytes, huge for a Flash game, and after compression, it was still around 14 mb. Maybe for a game of this size, considering the 6 levels and the painted graphics, wasn’t exactly meant for the casual game platform, and so the game design had not really suited the audience. That was not something I realized until very late in development; by then, it was far too late to change platforms or simplify the game content.

Having not played too many bullet hells myself, I had also failed to realize some of the aspects that people expected of the genre: upgrades. Besides the filesize, that was the single overriding complaint of the game. It wasn’t even something I had considered, and I’m not sure why I managed to miss something so important – although I think the game stands on its own without upgrades, there will be people who disagree with me, and I can see where they’re coming from.

Enemy issues was the next big complaint. Even with all of my testing, some aspects still went undiscovered, and I didn’t catch all of the bugs – and I sometimes didn’t realize how hard the game actually was. Having tested for months before release, I’d gotten to be quite good at the game, and some players missed cues or struggled with enemies that I had thought to be quite easy to read or obvious to beat.

## Lesson #4: Always have a second opinion – for games, that’d be beta testers. They provide a more objective view to any project, and can see flaws that the creator misses entirely.

I didn’t quite get enough friends to test the thing, so some odd problems like bosses persisting at the bottom of the screen (where they couldn’t be hit) or graphics glitches had slipped out into release unnoticed.

Ultimately, however, what went wrong was the fact that I had no real audience for my game. Evanescent was too casual for hardcore players, with no life limit, no upgrades, and simplistic plot, yet too extreme for the people who barely played games, as it was still a pretty difficult bullet hell.

Lesson #5: When making a game, make sure to make it fun and appealing to a target audience. Everything else is secondary.

Evanescent was fun to some people, which I’m very happy about, but there is still a lot I could improve upon, in my game design and development, to make a better game for my next project.

# So now what?

Maybe Evanescent didn’t exactly have the smoothest development path, but it was done, and it was done exactly how I had imagined. I look at it more as a story, and maybe as art, than a game, and I certainly treated its development as such – it is as much an art game as it is a bullet hell – and perhaps that caused its focus to waver a bit.

But it's done, with all of its crudeness and quirks, and that's probably the best outcome I could've asked for.

_Note (Written in July 2016): It's interesting going back and reading this post-mortem, about how I struggled with balancing gameplay and story in a game. It's still a struggle, though I think I'm finding a better balance. A bullet-hell shooter is probably not the best medium to flesh out a deep narrative, unfortunately._