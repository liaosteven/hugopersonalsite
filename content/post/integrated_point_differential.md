---
title: "a (potentially) better way to measure game closeness"
date: 2018-08-10T15:04:03+08:00
draft: true
---

What is the best way to measure how close a game is?

As a recreational sports better, this question is clearly of interest. Consider:

1. If two teams are 8-0, and one has been winning in blowouts, but the other has been winning in close games, perhaps the 'blowout'-winning team is the better squad.

2. If team A is playing team B for the second time this year, perhaps it would be interesting to know how close things were the first time around.

3. Knowing how 'close' a game was is useful for determining if we want to watch a game - i.e. I'm bored and I have time to watch one game, how do I determine which game to watch?

So the obvious answer is, check the score. But the score is not necessarily indicative of how close a game is. If a team jumps out to a 31-0 halftime lead, and proceeds to win 31-24, this game was never close, even though the final margin was just 7 points. See Panthers Seahawks 2015 playoffs.

On the contrast, if in the middle of the third quarter the score is 24-21, and the team with 21 ends up winning 48-27, the game was a lot closer than the final score indicates (garbage time touchdowns). See Patriots Cowboys 2007 regular season.

So, perhaps there's a better way to measure game closeness than point differential.

### Integrated Point Differential (IPD)

I sought to create a better metric for evaluating how ‘close’ a game is. I’ve called my metric “integrated point differential,” or ‘ipd’ for short. To calculate **ipd for a given team in a given game, we take the integral of the team’s point differential throughout the game with respect to time**, where point differential is defined by ([team score] - [opponent score]).

To get an idea of the intuition behind the metric, consider the following game between the Patriots and Dolphins.

| Patriots 	| Dolphins 	| Time Transpired (Seconds) 	| Quarter 	|
|:--------:	|:--------:	|:-------------------------:	|:-------:	|
|     0    	|     0    	|             0             	|    1    	|
|     3    	|     0    	|            300            	|    1    	|
|     3    	|     7    	|            780            	|    1    	|
|     3    	|    10    	|            1580           	|    2    	|
|     6    	|    10    	|            2210           	|    3    	|
|    13    	|    10    	|            2930           	|    4    	|
|    20    	|    10    	|            3430           	|    4    	|

The rows in the table represents every time there was a score in the game. “Time Transpired (Seconds)” displays how much time had already transpired in the game when the score occurred (there are 60 minutes, or 3600 seconds, in a game). For instance, the first score of the game was a field goal by the patriots, 300 seconds into the game. Note 1800 seconds is halftime, and 3600 seconds is the end of the game.

Here is the plot for the point differential throughout the game.

![Patriots Point Differential](/img/ipd/patriots_dolphins.png#center)

The point differential starts at 0 when the game begins (the score is 0 to 0). It jumps to three when the Patriots score at 300 seconds in, and drops to -4 when the Dolphins score a touchdown to lead 7-3. We continue this process for the whole game.

This game was by no means a blowout for the Patriots; the Patriots were trailing for a large portion of the game and never sealed the deal until the fourth quarter. We can see that the point differential is negative for a large stretch of the game when the Patriots are behind. To calculate the Patriot’s ipd in this game, we simply take the integral of the point differential, which in this case is equal to calculating the area of the space colored blue.

The ipd metric comes out to:$$\text{ipd} = 3*480 - 4*800 - 7*630 - 4*720 + 3*500 + 10*170 = \boxed{-5850}$$Now consider an alternative outcome: 

| Patriots 	| Dolphins 	| Time Transpired (Seconds) 	| Quarter 	|
|:--------:	|:--------:	|:-------------------------:	|:-------:	|
|     0    	|     0    	|             0             	|    1    	|
|     7    	|     0    	|            300            	|    1    	|
|    14    	|     0    	|            780            	|    1    	|
|    17    	|     0    	|            1580           	|    2    	|
|    20    	|     0    	|            2210           	|    3    	|
|    20    	|     3    	|            2930           	|    4    	|
|    20    	|    10    	|            3430           	|    4    	|

Note the final score of the game is the same. Here is the point differential plot.

![Patriots Point Differential Example 2](/img/ipd/patriots_dolphins_ex2.png#center)

Once again, the point differential is 0 to begin (game is tied 0-0). The Patriots score a touchdown at 300 seconds in, and the point differential jumps to 7. The point differential is at its maximum when the Patriots lead 20-0 starting at the 2210 second mark, and ending at the 2930 second mark.

This game would have felt like much more of a blowout. The Patriots were in clear control of the game, before the Dolphins scored a few ‘garbage time’ points near the end. The ipd for this game is$$\text{ipd} = 7*480 + 14*800 + 17*630 + 20*720 + 17*500 + 10*170 = \boxed{49870}$$To summarize, we have two games with the same final score, but vastly different game flows. The ipd metric is able to capture this and reflects how the second game was a much more ‘dominant’ victory by the Patriots.

### Spread Integrated Point Differential (SIPD)

Another interesting approach we can take is adapting this metric to NFL spreads. Just as the final score is not necessarily indicative of how close a game was, it is also not necessarily indicative of how good a bet was. In other words, even if the a team covers, they may have gotten lucky or it might have been a close call. As a gambler, we aren’t interested in games where the winning side is a close call; we are interested in determining games where the spread may be set completely inaccurately, making the winning side a ‘safe bet.’

Thus, it stands to reason that one might be interested in a metric that measures how ‘safe’ a bet was. Hopefully the parallels between measuring the ‘safety of a bet’ and the ‘closeness’ of a game are clear; we proceed to apply the same idea behind the ipd to the spread, creating a metric called the spread integrated point differentail, or sipd.

SIPD works as a simple modification to the ipd calculation. Instead of integrating the point differential over time, we integrate the point differential over time translated according to the spread. For instance, if the spread is Patriots -3, and the Patriots are ahead by 14, then the point differential (14) translated according to the spread (-3) is 11. If the Patriots are ahead by 3, then the point differential translated according to the spread is 0.

For instance, let’s take the (first) game from the IPD section where the Patriots won 20-10. Suppose the spread in that game was Patriots -3. Then our graph would look like:

![Patriots Spread IPD](/img/ipd/patriots_dolphins_sipd.png#center)

The SIPD here would be $$\text{sipd} = -3*300 + 0*480 - 7*800 -10*630 - 7*720 +0*500 + 7*170 = \boxed{-16650}$$ 

The Patriots would have covered, but the sipd accurately reflects that for much of the game, it may have seemed like the Patriots would not have covered, and that the **Dolphins may have in fact been the better bet** (i.e. if the same game was played in a million alternative universes, perhaps the Dolphins would have covered more often than not).

Note that the sipd is a translation of ipd; we can calculate $$\text{sipd} = \text{ipd} + \text{spread} *360$$

### IPD and SIPD in Practice

Using Python's BeautifulSoup Module, I scraped box score data from Pro-Football-Reference and calculated the IPD and SIPD for every game from 2002 to 2016.


### Other Metrics
