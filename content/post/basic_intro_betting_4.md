---
title: "basics of sports betting part 4: bankroll management"
date: 2018-08-22T06:59:40-05:00
draft: true
---

*This is __Part Four__ of Four. [Part One]({{< ref "basic_intro_betting.md" >}}) covers definitions and betting language. [Part Two]({{< ref "basic_intro_betting_2.md" >}}) covers key probability concepts in betting. [Part Three]({{< ref "basic_intro_betting_3.md" >}}) covers implied odds. [Part Four]({{< ref "basic_intro_betting_4.md" >}}) covers bankroll management.*

This is the final part of the Basics of Sports Betting Guide. In this section we will cover the intuition behind the Kelly Criterion - a set of rules for bankroll management. 

I hesitated as to whether to include this section, as I don't actually use the Kelly Criterion much whenever I think about sports betting. However, it is certainly an interesting concept to think about - and could be especially useful for betting strategies that involve models which spit out win probabilities. 

### Answers to Part Three Questions

1. The Saints' breakeven probability is $\dfrac{150}{250} = 60\%$ and the Panthers' breakeven probability is $\dfrac{1}{2.3}$. Then we have:$$\text{Implied Odds of Saints Winning} = \dfrac{0.6}{0.6 + \dfrac{1}{2.3}} \approx 57.98\%\\\\\\text{Implied Odds of Panthers Winning} = \dfrac{\dfrac{1}{2.3}}{0.6 + \dfrac{1}{2.3}} \approx 42.02\%$$

2. By definition of implied odds, if we use our implied odds to calculate edge, the edge (and thus juice) will be equal on both sides.

	Thus we calculate for the Panthers. The Decimal Odds are 2.3.$$\text{Juice} \approx 2.3 \times 0.4202 - 1 = -0.034$$ Let's write juice as positive - with this spread, the sportsbook is charging approximately a $\boxed{3.4\%}$ juice. 

3. The Saints' breakeven probability is $\dfrac{145}{245} = \dfrac{29}{49}$ and the Panthers' is $\dfrac{1}{2.35}$. We have: $$\text{Implied Odds of Saints Winning} = \dfrac{\dfrac{29}{49}}{\dfrac{29}{49} + \dfrac{1}{2.35}} \approx 58.17\%\\\\\\text{Implied Odds of Panthers Winning} = \dfrac{\dfrac{1}{2.35}}{\dfrac{29}{49} + \dfrac{1}{2.35}} \approx 41.83\%$$The juice is the edge of either bet (again, they are the same due to how we calculated implied odds):$$\text{Juice} \approx 2.35\times0.4183 -1 = -0.0170$$Thus, with this spread, the sportsbook is charging approximately a $\boxed{1.7\%}$ juice.

4. Let's calculate the breakeven probabilities (BeP) of each team first:
$$\begin{align}
\text{Warriors BeP} &= \dfrac{1}{2.25} = \dfrac{4}{9}\\\\\
\text{Rockets BeP} &= \dfrac{1}{3} \\\\ 
\text{Cavs BeP} &= \dfrac{2}{7} \\\\ 
\text{Celtics BeP} &= \dfrac{1}{5}
\end{align}$$As expected, the sum of these is $\dfrac{398}{315} \approx 1.2635$, well over 1. From the large sum, we can already tell there is a sizable juice. 

	To calculate implied odds, we want two things:

	* We want to multiply each of the posted odds by a constant amount - this makes it so that the juice is the same for all four  lines.
	* We want the new, adjusted odds, to add up to 1.

	It follows that multiplying each posted odd by $\dfrac{315}{398}$ achieves this goal (basically they sum up to 1.26, so we divide all of them by 1.26). This gives us:
	$$\begin{align}
	\text{Implied Odds Warriors} &= \dfrac{4}{9} \times \dfrac{315}{398} \approx 35.18\% \\\\\
	\text{Implied Odds Rockets} &= \dfrac{1}{3}\times \dfrac{315}{398} \approx 26.38\%\\\\ 
	\text{Implied Odds Cavs} &= \dfrac{2}{7} \times \dfrac{315}{398} \approx 22.61\%\\\\ 
	\text{Implied Odds Celtics} &= \dfrac{1}{5}\times \dfrac{315}{398} \approx 15.83\%
	\end{align}$$And we can use any one of the implied odds to calculate juice:$$\text{Juice} \approx 5.0 \times 0.1583 - 1 = -0.2085$$That means the sportsbook is charging a whopping juice of $\boxed{20.85\%}$ on each of its bets!

	*Side note*: In practice, such large juices are not actually uncommon when it comes to bets with a lot of outcomes (i.e. who wins March Madness, who wins NBA Championship, who gets drafted first overall, who will Lebron sign with, etc).  

### Bankroll Management: Motivating Example

Suppose you are given a task: you are given \$100, and asked to grow it to \$1000 by engaging in a series of bets against me.

My first offer to you: You can bet on heads or tails. I'll offer you decimal odds of 4.0 on each side. How much should you bet?




### Things We Didn't Cover

- Moneyline, Totals, Teasers, Pleasers

Separate Article: Moneyline to Spread Ratio