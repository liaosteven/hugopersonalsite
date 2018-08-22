---
title: "basics of sports betting part 2: probability concepts"
date: 2018-08-20T20:00:38+08:00
---

*This is __Part Two__ of Four. [Part One]({{< ref "basic_intro_betting.md" >}}) covers definitions and betting language. [Part Two]({{< ref "basic_intro_betting_2.md" >}}) covers key probability concepts in betting. [Part Three]({{< ref "basic_intro_betting_3.md" >}}) covers implied odds.*

Welcome to Part Two of the guide! Here, we'll move on from simply understanding terminology to introducing some probablistic concepts in sports betting. 

If you have no prior sports betting knowledge and are reading this, it is highly recommended you read [Part One]({{< ref "basic_intro_betting.md" >}}) first to understand some of the terminology I'll be using.

### Answers to Part One Questions

Here are the answers to the practice questions from the end of [Part One]({{< ref "basic_intro_betting.md" >}}).

1. The Cowboys won the game (they scored more points), but the Eagles covered, as: $$\text{the Eagle's points} (16) + 5 > \text{the Cowboy's points} (20)$$
2. **2 to 1** Fractional odds means you bet \$1 to win \$2 (plus your dollar back). Decimal odds represent the ratio of [amount you win + your wager] to [your wager]; in this case you receive \$3 total for every \$1 you bet (if you win), so the decimal odds are $\boxed{3.0}$.

3. **+200** American Odds means you bet \$1 to win \$2 (plus your dollar back). As with before, the total amount you receive if you win, relative to your wager, is $\boxed{3.0}$.

4. **-200** American Odds means you bet \$2 to win \$1 (plus your \$2 back). Thus if you bet \$2 and win, the total amount you receive back (including your wager) is \$3. Then, the decimal odds are 3/2 or $\boxed{1.5}$.

We'll leave the bonus question unanswered - that is the content of this post!

### Juice

Every sportsbook I know charges 'juice', or 'vigorish'.

Juice serves as a sportsbook's 'commission.'' If we continue the restaurant analogy from Part One, if sportsbooks didn't add 'juice' to their betting lines, it would be equivalent to a restaurant not adding any margin to their food costs (i.e. restaurant breaks even on every dish).

**Example**: Perhaps the example that is easiest to understand is a fair coin flip - for instance, many sportsbooks set odds for whether the Super Bowl coin flip will be heads or tails. You might see odds like so:

<p style='text-align: center;'>
<b>Heads -110<br>
Tails -110</b>
</p>

Obviously, a (fair) coin flip is a 50-50 proposition. But instead of paying \$1 to win \$1, you would pay \$1.10 to win \$1. If the sportsbook accepts \$1.1 million dollars in bets on heads, and \$1.1 million dollars in bets on tails, regardless of the result, it makes a chill \$100,000.

That's the idea behind juice - **it allows the sportsbook to make money regardless of the outcome of the event.** 

For bettors, the implication is that **juice lowers the EV of your bets.**

### Edge

**Edge** is defined as expected profit (expected value) on a bet. This is arguably the most fundamental concept in betting - if your goal is long-term profitability, you want to avoid bets with negative edge (EV) and prioritize bets with the highest edge (EV). 

I'll assume familiarity with Expected Value (EV) in this post (basic probability concept) - google it if you're not familiar.

If we assume a) sportsbooks generally are good at estimating the odds of events occurring (a fair statement imo), and b) all lines include juice, then it follows that **lines generally have negative EV as a rule of thumb.**

**Example**: Consider a typical spread bet:

<p style='text-align: center;'>
<b>Patriots -3 -110<br>
Dolphins +3 -110</b>
</p>

What is your edge on betting on one of these lines? By definition of EV, we calculate edge (EV) as follows:$$\text{Edge} = [\text{Probability of Cover}] \times [\text{Amount You Would Win}] + [\text{Probability of Loss}] \times [\text{Amount You Would Lose}]$$Let's assume both sides are indeed equally likely. Let $x$ be the amount you wager on the Patriots. Your edge then is:
$\begin{align}
[\dfrac{1}{2} \times \dfrac{x}{1.1}] + [\dfrac{1}{2} \times (-x)] &= \dfrac{x}{2.2} - \dfrac{x}{2} \\\\ 
&= \dfrac{2x}{4.4} - \dfrac{2.2x}{4.4} \\\\\
&= -\dfrac{0.2x}{4.4} \\\\\
&= \boxed{-\dfrac{x}{22}}
\end{align}$

So on your typical bet against the spared (where we assume both outcomes are 50-50) - with **-110** odds on both sides - you should expect to lose 4.5% of your wager on each bet!

### Decimal Odds

**Decimal odds offer one key convenience - they make calculating edge (significantly) easier.** Using Decimal Odds, edge is calculated as:$$[\text{Decimal Odds}] \times [\text{Probability you Cover}] -1$$This formula can be derived / seen by working through an example where you bet \$1:

* You start with \$1. After the bet, there is an $[\text{Probability You Cover}]$ chance you get $[\text{Decimal Odds}]$ back (i.e. if decimal odds are 2.70, you get \$2.70 back if you win, which includes your original wager). There is a  $[\text{Probability You Don't Cover}]$ chance you get \$0 back. Thus, at the end of the bet, you expect to have 

$$[\text{Decimal Odds}] \times [\text{Probability you Cover}] + 0\times[\text{Probability you Don't Cover}] = [\text{Decimal Odds}]\\times [\text{Probability you Cover}]$$ Subtract \$1, your starting total, and you get how much you expect to make off that bet.

Note the Decimal Odds Equivalent of -110 is $\dfrac{2.1}{1.1}$ or about $1.909$. So on a typical spread bet, your edge calculated using decimal odds is $1.909 \times \dfrac{1}{2} - 1 = \boxed{-0.0455} $, as expected.

### Breakeven Probability

Assume a sportsbook offers -110 odds on some event occurring. What is the 'breakeven probability' - **the probability of the event occuring where your edge would be 0**? Worded more practically, how likely does the event need to occur for you to make this bet?

Let the breakeven probability be $p$. By definition, we want $p$ such that:$$1 \times p - 1.1 \times \(1-p\) = 0$$Solving, we find $p = \boxed{\dfrac{1.1}{2.1}}$, or $\approx 52.38\%$.

**Breakeven probability is also significantly easier to calculate with decimal odds** (I honestly wish decimal odds were the norm). Assume decimal odds are $d$. Remember, we derived the formula for edge as:$$d \times [\text{Probability you Cover}] -1$$It follows that if $p$ is the breakeven probability, then we solve
$$
\begin{align}
d \times p -1 &=0 \\\\\
&\to p = \boxed{\dfrac{1}{d}}
\end{align}
$$

### Practice Questions

Depending on your experience with probability, these questions may be challenging. If that is the case, don't fret! It's a sign you're growing. 

1. You think the Browns have a 5% chance of winning the Super Bowl. The betting odds for the Browns winning the Super Bowl is 15 to 1 (fractional odds). Should you take the bet?

2. The odds for the Lakers beating the Clippers is +220. What is the breakeven probability? 

3. If you think the Lakers have a $30\%$ chance of winning, should you bet on the Lakers at +220 odds? What is your edge?

4. Let the American Odds for a given line be A. The formula for breakeven probability for 'negative' American odds (i.e. -110, -200, -350) is $\dfrac{A}{A-100}$ - i.e. for -110 odds, the breakeven probability is $\dfrac{-110}{-210}$. Derive this formula.

5. Let the American odds for a given line be A. The formula for breakeven probability for 'positive' American odds (i.e. +120, +200) is $\dfrac{100}{A + 100}$ - i.e. for +220 odds, the breakeven probability is $\dfrac{100}{320}$. Derive this formula.

6. Suppose instead of offering **-110** lines on both sides of a spread bet, a sportsbook offers **-105** lines (a smaller juice). Assuming 50-50 outcome probability, what is the new edge if betting on this line (either side)?

Answers can be found in [Part Three]({{< ref "basic_intro_betting_3.md" >}}).