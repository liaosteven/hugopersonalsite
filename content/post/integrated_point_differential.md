---
title: "a better way to measure game closeness"
date: 2018-08-11T15:04:03+08:00
---

**TLDR: The final score does not tell the whole story regarding how close a game was. Integrated Point Differential (IPD) improves upon Point Differential by accounting for the score throughout the game, as opposed to just the final score. Spread Integrated Point Differential (SIPD) adjusts IPD with respect to the spread, and could be a useful proxy for whether a bet was the right side (even if it didn't cover).**

What is the best way to measure how close a game is?

So the obvious answer is, check the score. But the score is not necessarily indicative of how close a game is. If a team jumps out to a 31-0 halftime lead, and proceeds to win 31-24, this game was never close, even though the final margin was just 7 points. See Panthers Seahawks 2015 playoffs.

In contrast, if in the middle of the third quarter the score is 24-21, and the team with 21 ends up winning 48-27, the game was a lot closer than the final score indicates (garbage time touchdowns). See Patriots Cowboys 2007 regular season.

So, perhaps there's a better way to measure game closeness than point differential.

### Integrated Point Differential (IPD)

I sought to create a better metric for evaluating how ‘close’ a game is. I’ve called my metric “integrated point differential,” or ‘ipd’ for short. To calculate **ipd for a given team in a given game, we take the integral of the team’s point differential throughout the game with respect to time**, where point differential is defined by ([team score] - [opponent score]).

It's simpler than it may sound. To get an idea of the intuition behind the metric, consider the following game between the Patriots and Dolphins.

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

This game would have felt like much more of a blowout. The Patriots were in clear control of the game, before the Dolphins scored a few ‘garbage time’ points near the end. The ipd for this game is$$\text{ipd} = 7*480 + 14*800 + 17*630 + 20*720 + 17*500 + 10*170 = \boxed{49870}$$To summarize, we have two games with **the same final score, but vastly different game flows**. The ipd metric is able to capture this and reflects how the second game was a much more ‘dominant’ victory by the Patriots.

### Spread Integrated Point Differential (SIPD)

Another interesting approach we can take is adapting this metric to NFL spreads. If you're not familiar with betting terminology, check out my [basic guide](/post/basic_intro_betting/).

Just as the final score is not necessarily indicative of how close a game was, it is also not necessarily indicative of how good a bet was. In other words, even if a team covers, they may have gotten lucky or it might have been a close call. As a gambler, we aren’t interested in games where the outcome could go either way; we are more interested in determining games where the spread may be set completely inaccurately, making the winning side a ‘safe bet.’

Thus, it stands to reason that one might be interested in a metric that measures how ‘safe’ a bet was. SIPD works as a simple modification to the ipd calculation. Instead of integrating the point differential over time, we integrate the point differential over time *translated according to the spread.* For instance, if the spread is Patriots -3, and the Patriots are ahead by 14, then the point differential (14) translated according to the spread (-3) is 11. If the Patriots are ahead by 3, then the point differential translated according to the spread is 0.

For instance, let’s take the (first) game from the IPD section where the Patriots won 20-10. Suppose the spread in that game was Patriots -3. Then our graph would look like:

![Patriots Spread IPD](/img/ipd/patriots_dolphins_sipd.png#center)

The SIPD here would be $$\text{sipd} = -3*300 + 0*480 - 7*800 -10*630 - 7*720 +0*500 + 7*170 = \boxed{-16650}$$ 

The Patriots would have covered, but the sipd accurately reflects that for much of the game, it may have seemed like the Patriots would not have covered, and that the **Dolphins may have in fact been the better bet** (i.e. if the same game was played in a million alternative universes, perhaps the Dolphins would have covered more often than not).

Note that the sipd is a translation of ipd; we can calculate (for non-overtime games): $$\text{sipd} = \text{ipd} + \text{spread} *3600$$

### IPD in Practice

Using Python's BeautifulSoup Module, I scraped box score data from Pro-Football-Reference and calculated the IPD and SIPD for every game from 2002 to 2016.

Point differential are calculated with respect to the home team (i.e. point differential = [home score] - [away score]). Thus, 'blowouts' by the road team will have very *negative* point differentials.

Some interesting findings:

**Five Lowest IPDs (Biggest Road Blowouts)**

|      Date     	|  Home Team 	| Away Team 	| Home Score 	| Away Score 	|    IPD   	|
|:-------------:	|:----------:	|:---------:	|:----------:	|:----------:	|:--------:	|
|  Week 7, 2010 	|   Broncos  	|  Raiders  	|     14     	|     59     	| -112,130 	|
|  Week 6, 2014 	| Buccaneers 	|   Ravens  	|     17     	|     48     	|  -101823 	|
| Week 13, 2005 	|   Eagles   	|  Seahawks 	|      0     	|     42     	|  -99351  	|
| Week 14, 2007 	|   Ravens   	|   Colts   	|     20     	|     44     	|  -94082  	|
| Week 10, 2010 	| Washington 	|   Eagles  	|     28     	|     59     	|  -93801  	|

The most interesting game here is the Colts' blowout of the Ravens, where the Colts won by "just" 24 points. The game would rank 146th in terms of 'road blowout' by point differential alone (i.e. between 2002 and 2016, there were 145 games in which the road team won by 25 or more), but ranks 4th in IPD rankings. Here, IPD captures how the Colts led 30-0 with 11:57 left to go in the *second quarter*, and 44-7 until the Ravens tacked on two garbage time touchdowns in the 4th quarter - [box score for reference](http://www.espn.com/nfl/game?gameId=271209033). In this sense, IPD better captures how badly the Colts destroyed the Ravens than point differential alone.

Meanwhile, the biggest road blowout in terms of point differential was Patriots @ Bills in Week 10, 2007, when the Patriots won 56-10. This game ranked 7th in IPD.

**Five Highest IPDs (Biggest Home Blowouts)**

|      Date     	| Home Team 	|  Away Team 	| Home Score 	| Away Score 	|   IPD  	|
|:-------------:	|:---------:	|:----------:	|:----------:	|:----------:	|:------:	|
|  Week 6, 2009 	|  Patriots 	|   Titans   	|     59     	|      0     	| 121046 	|
|  Week 3, 2014 	|  Falcons  	| Buccaneers 	|     56     	|     14     	| 118517 	|
| Week 13, 2014 	|    Rams   	|   Raiders  	|     52     	|      0     	| 113257 	|
| Week 14, 2012 	|  Seahawks 	|  Cardinals 	|     58     	|      0     	| 112586 	|
|  Week 7, 2011 	|   Saints  	|    Colts   	|     62     	|      7     	| 105891 	|

Nothing surprising here - the only 'anomaly' is the Falcons Bucs game, which ranked 17th on point differential alone (i.e. there were 16 games between 2002 and 2016 in which the home team won by 43 or more). However, IPD captures how the Falcons led 56-0 until 8:46 in the 4th, when the Buccaneers tossed two garbage time touchdowns.

### SIPD in Practice 
Things get more interesting when we look at SIPD - the games with highest absolute (i.e. apply absolute value) SIPD could be viewed, in hindsight, as the 'safest' bets - games in which the spread was wildly off, where your bet was **_least in doubt_**.

Another way I like to interpret this: NFL games involve quite a bit of luck. If you cover your bet, that doesn't mean you made the right bet - i.e. if the game was played in 10,000 alternative universes, each side might cover 5,000 times. However, obviously sportsbooks can't set perfect spreads every time - there will be games which the spread is wildly off, where perhaps if the game was played in 10,000 alternative universes, one side might cover 8,000 times. Games with extremely high absolute SIPD are games in which *we are most confident that the spreads were off*.

Obviously, we don't know the SIPD until after the game is over. However, maybe studying previous games with high absolute SIPDs can give us insight on how we can identify future games in which spreads are off.

Anyways, here are the eleven games in which absolute SIPD was highest. Point Differential is once again calculated with respect to the home team. The spread shown is also with respect to the home team (i.e. negative spread means home team was favored, positive spread means road team was favored).

**Eleven Highest Absolute SIPD**

| Rank 	|      Date     	|  Home Team 	|  Away Team 	| Spread 	| Home Score 	| Away Score 	|   SIPD  	|
|:----:	|:-------------:	|:----------:	|:----------:	|:------:	|:----------:	|:----------:	|:-------:	|
|   1  	|  Week 7, 2010 	|   Broncos  	|   Raiders  	|   -7   	|     14     	|     59     	| -137330 	|
|   2  	| Week 14, 2014 	|   Saints   	|  Panthers  	|   -9   	|     10     	|     41     	| -114464 	|
|   3  	| Week 10, 2013 	|    Colts   	|    Rams    	|   -7   	|      8     	|     38     	| -108266 	|
|   4  	|  Week 3, 2014 	|   Falcons  	| Buccaneers 	|   -6   	|     56     	|     14     	|  96917  	|
|   5  	| Week 10, 2012 	|  Dolphins  	|   Titans   	|   -7   	|      3     	|     37     	|  -96911 	|
|   6  	|  Week 1, 2015 	| Buccaneers 	|   Titans   	|   -3   	|     14     	|     42     	|  -94884 	|
|   7  	| Week 16, 2009 	|   Giants   	|  Panthers  	|  -8.5  	|      9     	|     41     	|  -94714 	|
|   8  	| Week 13, 2014 	|    Rams    	|   Raiders  	|   -6   	|     52     	|      0     	|  91657  	|
|   9  	|  Week 7, 2009 	|   Bengals  	|    Bears   	|   +2   	|     45     	|     10     	|  91039  	|
|  10  	|  Week 6, 2014 	| Buccaneers 	|   Ravens   	|   +3   	|     17     	|     48     	|  -91023 	|
| 11   	| Week 13, 2010 	| Chargers   	| Raiders    	| -13    	| 13         	| 28         	| -90249  	|

The reason I include 11 games - and not 10 - was because I think the 11th-ranked game is interesting. Unlike the other games, the point differential was 15 points - nothing to write home about.

However, the SIPD indicates that betting on the Raiders here would have been an extremely safe bet. And the game flow verifies this: the Chargers were favored by 13, but the Raiders led 14-0 in the first quarter, 21-3 at the half, and 21-6 at the end of the third quarter. At that point, the Chargers would have needed to outscore the Raiders by at least 28 to cover. If you bet on the Raiders, your money was never in doubt.

### Summary

* IPD improves over point differential in representing your internal sense of how close a game was. For games where you say "the game was closer than the score indicates," this will be reflected by a lower (absolute) IPD.
* IPD is useful in finding good games to watch. The team with a negative IPD won? Likely a comeback. The 2017 Super Bowl between the Patriots and Falcons had a -40859 IPD for the Patriots (note the IPD accurately reflects how for much of the game, things didn't feel close). Games with extremely low (absolute) IPDs and high scores are likely back-and-forth battles with several lead changes.
* SIPD is useful tool for betters, as a metric that sheds light on how 'off' a spread was. The higher the SIPD, the more covering was never in doubt.
* With the understanding that the game of football involves a lot of luck, SIPD may also be a useful metric for determining if you 'made the right bet.' For instance, you might lose a bet on a backdoor cover, but a positive SIPD might be a good proxy for whether you had the right side (i.e. in 10,000 universes you would have covered in more than half).
* Although all examples were in reference to football here, IPD and SIPD can easily be extended to other sports as well. 