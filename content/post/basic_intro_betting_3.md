---
title: "basics of sports betting part 3: implied odds"
date: 2018-08-21T14:55:00+08:00
---

*This is __Part Three__ of Four. [Part One]({{< ref "basic_intro_betting.md" >}}) covers definitions and betting language. [Part Two]({{< ref "basic_intro_betting_2.md" >}}) covers key probability concepts in betting. [Part Three]({{< ref "basic_intro_betting_3.md" >}}) covers implied odds.*

Welcome to Part Three of this guide! We'll cover implied odds and calculating juice, and briefly cover bankroll management theory (Kelly Criterion).

The hope is after finishing this final section of the guide, you'll understand (most) of the basic concepts needed to build sports betting strategies that work for you.

### Answers to Part Two Questions

Here are the answers to the practice questions from [Part Two]({{< ref "basic_intro_betting_2.md" >}}).

1. There are two ways to solve this problem - the first is to calculate the edge you have on the bet, and the second is the calculate the breakeven probability and see if it is greater or less than 5%.

	* **Using Edge**: To calculate edge, convert fractional odds to decimal odds - 15 to 1 fractional odds is 16.0 decimal odds. Remember, edge is $$[\text{Decimal Odds}]\times[\text{Probability of Cover}] -1$$Then your edge on this bet is $16 \times 0.05 -1 = -0.2$; therefore you shouldn' make this bet.

	* **Using Breakeven Probability**: The breakeven probability is $\dfrac{1}{\text{Decimal Odds}} = \dfrac{1}{16}$. This is greater than $5\%$, telling us we should not take the bet.

2. Suppose you bet \$1. We want $p$ such that $$ p \times 2.2 + \(1-p\) \times (-1) = 0$$Solving, we find $p = \boxed{\dfrac{1}{3.2}}$.

	Alternatively we can convert +220 American odds to decimal odds. +220 means if you bet \$1 and win, you get \$2.20 in profit and your \$1 back, for a total of \$3.20 back. Thus your decimal odds are 3.20. Since breakeven probability is $\dfrac{1}{\text{Decimal Odds}}$, we once again have $p = \dfrac{1}{3.2}$.

3. No, you should not, as 30% is less than the breakeven probability $\left(\dfrac{1}{3.2}\right)$. Your edge is 
$$
\begin{align}
[\text{Decimal Odds}]\times[\text{Probability You Cover}] -1 &= 3.2\times0.3 -1 \\\\\
&= -0.04
\end{align}$$Thus, your expected loss on this bet would be 4% of your wager.

4. For negative American odds '-A', you bet A in order to win \$100. For instance, -150 means you bet \$150 to win \$100. 

	Let's solve for breakeven probability $p$ - the **probability where edge is equal to 0**. We have:
$$
\begin{align}
p\times \text{Profit} + \(1-p\)\times\text{Loss}&= 0 \\\\\
&\to p\times100 + \(1-p\)\times A = 0 \\\\\
&\to 100p = A\times p -A \\\\\
&\to (100-A)\times p = -A \\\\\
&\to p = \dfrac{A}{A-100}
\end{align}
$$as desired.

5. For positive American odds A, you bet \$100 in order to win A. For instance, +120 means you bet \$100 to win \$120. 

	As with Question 4, we solve for $p$:
	$$
	\begin{align}
	p\times \text{Profit} + \(1-p\)\times\text{Loss}&= 0 \\\\\
	&\to p\times A + \(1-p\)\times \(-100\) = 0 \\\\\
	&\to p\times A -100 + 100p = 0 \\\\\
	&\to (A+100)\times p = 100 \\\\\
	&\to p = \dfrac{100}{A+100}
	\end{align}$$as desired.

6. Suppose you bet \$105. If you win the bet (0.5 probability), you profit \$100. If you lose the bet (0.5 probability), you lose \$105. Thus, if you bet \$105, your expected value on the bet is $$0.5\times 100 - 0.5\times 105 = -2.5$$It follows your expected value is $-\dfrac{2.5}{105} = -\boxed{\dfrac{1}{42}} \approx -2.38\%$.
 
### Implied Odds

Loosely defined, **implied odds are what a sportsbook believes are the odds of an event happening.**

Consider the Super Bowl coin flip example from [Part Two]({{< ref "basic_intro_betting_2.md" >}}), where a sportsbook might post the following line:

<p style='text-align: center;'>
<b>Heads -110<br>
Tails -110</b>
</p>

From here, we might intuitively gather that the sportsbook believes heads and tails are equally likely - since they offer the same odds on each.

However, it is not always clear what the sportsbook believes are the probabilities of each event occuring. Consider the following 'moneyline bet' (bet on which team wins outright, not on the spread)

<p style='text-align: center;'>
<b>Patriots -250<br>
Jets +200</b>
</p>

The breakeven probabilities (see [Part Two]({{< ref "basic_intro_betting_2.md" >}})) are 71.4% for the Patriots and 33.3% for the Jets. However, it is not quite accurate to say the sportsbook believes the Patriots and Jets have 71.4% and 33.3% chances of winning, respectively, since these add up to over 100% - due to the juice in the bet.

For a given event, let us more rigorously define **implied odds** as **the odds such that the edge is the same on both sides**. Another way of looking at it is the sportsbook adds the same juice to both sides of the bet.

Here is the formula for implied odds: given 'competing odds' $a$ and $b$ (they refer to events A and B such that *one and only one will occur*), let the breakeven probabilities be $p_a$ and $p_b$ respectively. Then: $$\text{Implied odds of A occurring}= \dfrac{p_a}{p_a + p_b}\\\\ \text{Implied odds of B occurring}= \dfrac{p_b}{p_a + p_b}$$In the previous example with the Patriots and Jets, we would have:

$$\text{Implied odds of Patriots Winning}= \dfrac{71.4}{71.4 + 33.3} \approx 68.18\% \\\\ \text{Implied odds of Jets Winning}= \dfrac{33.3}{71.4 + 33.3} \approx 31.82\% $$While I won't prove that this formula for implied odds necessarily determines that the edge is the same on both sides (though the proof is not that difficult if you want to try it), we can see it is true here. Converting to Decimal Odds, -250 becomes 1.40 and +200 becomes 3.0. We can calculate the edge for both sides using our calculated implied odds:

$$\text{Edge when Betting on Patriots}= 1.40\times 0.6818 -1 = 0.9548 - 1 \approx -0.0455\\\\ \text{Edge when Betting on Jets}= 3.0 \times 0.3182 - 1 \approx -0.0454$$
### Usefulness of Implied Odds 

**What a sportsbook believes are the odds of an event occuring is valuable information as a strong, objective proxy for true probability.**  Consider:

* Humans are pretty terrible at estimating odds; for instance, there is a tendency to overrate the chances a favorite wins. If I'm watching Federer vs Nadal, I simply don't trust a regular fan to give me an accurate percentage chance each player wins.
* Sportsbooks have a tendency to be very accurate - i.e. events that sportsbooks give 80% chance of happening tend to happen around 80% of the time. This is because sportsbooks derive their livelihood off of accurately predicting odds (setting poor odds means they'll likely lose money to bettors). 
* In addition to being accurate, sportsbook implied odds are *objective* - in that they are common for every game and can be cited. Objective data is valuable when doing projects because a) it allows the project to be reproducible (i.e. if you use 'my personally estimated odds', no one can reproduce your project in the future because they're not you) and b) it allows meaningful comparisons to be made.


### Python Script

Below is a Python script you can use for calculating implied odds (for events with two outcomes - i.e. Moneyline bets, spread bets, totals):

	def getOdds(a):
    """getOdds finds the breakeven probability, given American odds 'a'"""

	    odds = 0
	    if a < 0:
	        odds = (-a)/(-a + 100)
	    else:
	        odds = 100/(100+a)

	    return odds

	def impliedOdds(a, b):
	    """Given American odds a and b of some two-outcome event, impliedOdds finds
	    the implied odds of each event occurring."""

	    oddsA = getOdds(a)
	    oddsB = getOdds(b)

	    impliedA = oddsA/(oddsA + oddsB)
	    impliedB = oddsB/(oddsA + oddsB)

	    totalOdds = oddsA + oddsB

	    print("Team A has an implied Vegas win probability of " + str(impliedA))
	    print("Team B has an implied Vegas win probability of " + str(impliedB))

For example, if we have:
<p style='text-align: center;'>
<b>Patriots -250<br>
Jets +200</b>
</p>
Then we can run:

	    >>> impliedOdds(-250, 200)
		Team A has an implied Vegas win probability of 0.6818181818181818
		Team B has an implied Vegas win probability of 0.3181818181818181

### Calculating Juice

It is often useful to get an idea of how large the 'juice' is for a given bet - i.e. how much commission you have to pay in order to place this bet. For instance, if you are considering which sportsbook to use, you might prefer sportsbooks with smaller juices.

As with before, consider:
<p style='text-align: center;'>
<b>Heads -110<br>
Tails -110</b>
</p>
Here, it is easy to calculate juice. Regardless of which side you bet on, your edge is -4.5%. Thus, the juice can be said to be 4.5%. 

**Good to Know**: Most sportsbooks use -110 as the default odds for spread bets. Some, however, use -105. When using -105, the juice is $\approx$ 2.4%, as calculated in Part Two Practice Question 6.

Intuitively, we see that perhaps it makes sense to define juice such that the juice on both sides is the same. But this is the whole point behind implied odds. Thus, defining juice in this manner, we can calculate juice for any two-outcome bet by calculating the edge for either side using that side's implied odds. 

As an example, the juice on the Patriots-Jets moneyline from earlier is 4.5%.

### Practice Questions

1. The Saints are playing the Panthers. The moneyline for the Saints is -150 and the money for the Panthers is +130. Assuming no tie, what are the implied odds of each outcome occurring?

2. In the previous example, what is the juice?

3. Suppose a rival sportsbook posts the moneyline for the Saints as -145 and the Panthers as +135. Now, what are the implied odds of each outcome occurring? What is the juice?

4. **Bonus**: It is the conference finals of the NBA playoffs - four teams remain. The odds for each winning the NBA Championship are Warriors +125, Rockets +200, Cavaliers +250, and Celtics +400. What is the juice on these bets?