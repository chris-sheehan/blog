---
layout: post
title:  "NBA Shot Distribution and Winning"
date:   2015-09-09 22:55:00
categories: posts
---

It's been a while, as I've been busy with <a href="http://www.nytimes.com/2015/08/24/technology/the-unicorn-club-now-admitting-new-members.html" target="_blank">work</a> and TA'ing at <a href="https://generalassemb.ly/education/data-science" target="_blank">General Assembly</a>. Need to get back into the habit of doing these every week, so just a small one to break the seal.

I've been reading _Basketball Analytics: Spatial Tracking_ by Stephen Shea from <a href = "http://www.basketballanalyticsbook.com" target= "_blank">basketballanalyticsbook.com</a> -- great book, A++ will read again. One of the **many** concepts that caught my fancy was Scoring Versatility Index (SVI), a measure of a player's ability to score on multiple types of shots -- drives, catch/shoot, and" pull ups. I wondered how that versatility, really measuring the concentration of a player's scoring by shot type, would translate to measuring the concentration of a team's points scored in a game and season. I've seen the <a href = "https://en.wikipedia.org/wiki/Herfindahl_index" target = "_blank">Herfindahl Index</a> applied to team balance, but was never particularly impressed by the results. So for fun, let's try one more method.

The calculation of SVI is the entropy of the shot distributions. A player who takes 1/3 of his shots on drives, 1/3 on catch/shoot, and 1/3 on pull ups, has the most difficult game to predict. Any given shot has an equal chance of being a certain type. Another player who takes 3/4 of his shots pull up, and 1/8 each drive and catch/shoot is much more predictable -- he's probably going to take a pull up jumper. Mathematically, less predictability == higher entropy, the formula being -Σ<sub>i</sub>p<sub>i</sub>log<sub>2</sub>p<sub>i</sub>.

The results were not great for v1. There appears to be downward pattern (higher season-long entropy correlates somewhat negatively with win percentage), but there are a lot of dots that are nowhere near that trend line. In the second plot, on a game-level, higher entropy performances appear in both extreme wins and losses, indicating that there's something else more important than scoring balance at play (like maybe quality of the players taking those shots). I'm curious to see which teams are on either end of the spectrum.

![Scoring Distribution vs. Season Win %]({{site.baseurl}}/assets/img/scoring_dist_win_perc.png)

![Scoring Distribution vs. Margin of Victory]({{site.baseurl}}/assets/img/scoring_dist_mov.png)


Despite the crappy R^2, there's I feel like there's some interesting things to look into here, so hopefully I'll do a follow-up soon. A few things that'll likely cover:

* Using proper box score data instead of shot logs, which omit fouls and so also FT.
* Exploring shot/pts distribution vs. offensive efficiency rather than winning % or margin of victory.
* "Crunch" time offensive efficiency vs. earlier in games.
