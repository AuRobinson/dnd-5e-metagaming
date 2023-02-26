# dnd-5e-metagaming
_I do not condone metagaming purely to "win". Narrative is more important than max-deeps._

## What is metagaming?

Metagaming refers to a player utilizing knowledge outside of or not available to the character they're playing in the game. For example, calculating the chance of you hitting a monster depending on specific measurements wouldn't be something that the character would know, only you as the player would.

## Is it Fair?

It depends. If you're metagaming purely to "win", then I'd lean into a **no**. If you're using it to better understand the world and apply the difficulty into a narrative for your characters then I'd say **yes**.

## Method and Conditions

The method in determining the enemie's Armor Class (AC) and your general hit-chance is framed around Dungeons & Dragons 5th edition (5e), but can easily be tweaked to any TTRPG with a dice system. 

_All hail the math rocks_.

### Finding the Difficulty

There are 2 notable difficulty types in D&D 5th edition. To simplify you can think of this as **attacking** and **defending**.

> The target number for an ability check or a saving throw is called a Difficulty Class (DC). The target number for an attack roll is called an Armor Class (AC).
> 
> _D&D Player's Handbook; introduction p. 7_

Within the rules of 5e, players tell or are told the DC of a spell or save, where in contrast, an enemy or target's AC is not explicitly mentioned. This presentes us with a situation where we only need to identify the chance of success in defence of something, but we need to identify the target's AC before we are able to find the chance of hitting something very hard.

_Important note: if you are in a game where crit-failure is a thing the math changes a little bit._

### Attacking (AC)

Finding the Armor Classin 5e is a simple process of noting when you succeed and fail to hit. So keep note of the successes and failures and you can narrow down the AC range.

#### Finding AC

_For the sake of simplicity we'll assume there's no bonus to attack_

| Roll | Hit |
| -: | :-: |
| 5 | FALSE |
| 18 | TRUE |
| 10 | FALSE |
| 11 | FALSE |
| 17 | TRUE |
| 15 | FALSE |

From these 6 attack rolls we were able to hit twice. So we can confidently assume that the AC of what we're hitting is between 15 and 18 (given 17 and 18 both hit).

**Warning: Math**

We can denote the _minimum_ possible AC value as $a$ and the _maximum_ possible AC value as $b$.

$$a < R \le b$$

Where $R$ is the set of possible AC values that could result in a successful outcome. And we can further express the system of inequalities:

$$
\begin{align*}
a < r_{1}, a < r_{2}, .., a < r_{k} \\
b \ge r_{1}, b \ge r_{2}, .., b \ge r_{k}
\end{align*}
$$

where $r_i$ is the AC value that would have resulted in the $i$-th successful attack. Keep in mind, there is a possability that you'll never know the AC during combat.

If you are able to identify the enemie's AC, or are willing to guess the AC and find the chance of hitting, you can use the following function:

$$
1 - \frac{\text{Difficulty} - \text{Bonus} - 1}{\text{Dice}} \\
$$

If you want to plug the equation in a spreadsheet or function (python, R, julia, etc.)

$$
f(x, y, z) = 1 - \frac{x - y - 1}{z}
$$

### Defending (DC)

Defending is similar to attacking, but you know what the DC save is as a GM/Player, so your chances is simply the function presented earlier $f(x, y, z)$. 

### Conditions

If your game consideres ones as a failure regardless of applicable bonuses you'd use the following:

$$
f(x, y, z) = 1 - \frac{x - y}{z}
$$

## Chance Table

If we have a range of the Difficulty between 15 and 18 as mentioned earlier we can represent it in this matrix, where the rows are the possible AC and the columns are the bonuses to the roll.

|   |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  |  10 |
|---|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|
| **16** | 0.25| 0.3 | 0.35| 0.4 | 0.45| 0.5 | 0.55| 0.6 | 0.65| 0.7 | 0.75|
| **17** | 0.2 | 0.25| 0.3 | 0.35| 0.4 | 0.45| 0.5 | 0.55| 0.6 | 0.65| 0.7 |


<!--
## Code

![R code]()

-->
