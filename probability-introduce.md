


in this course, hope you will understand probability is from deterministic statistics,  not from random dice.

## Understanding What Probability Means

[Probability is the likelihood of a random event happening.](https://www.mathsisfun.com/data/probability.html) It is usually expressed as a ratio. The probability of something happening is defined by the ratio

$$probability = \frac{no. of\space favorable\space outcomes}{no. of\space possible\space outcomes}$$

where a favorable outcome is the event you are seeking to happen

 For example, if you roll a 6-sided die, each outcome has a 1 out of 6 probability.

In deep learning, probability can be used to describe the prediction results of a neural network on input data.

For example, a neural network can be used to predict whether an image contains a dog. It can output a probability value indicating the probability that the image contains a dog. For example, in the following three images, as the resolution increases, the probability that we determine that the image contains a dog also increases.

![](https://pic4.zhimg.com/80/v2-32bb66ff5175316e8c91afc05199c907_720w.webp)

## 1.Determine the probability of a single event happening.

understand how to figure out the probability of a single, random event happening, and understand what that probability means.

For example, if you have a jar with 10 red marbles and 5 blue marbles, you might want to know what the possibility of randomly pulling out a blue marble is. Since you have 5 blue marbles, the number of favorable outcomes is 5. Since you have 15 marbles total in your jar, the number of possible outcomes is 15. Your probability ratio will look like this: the probability of randomly pulling out a blue marble is 1 out of 3.

### 1.1.Understand the probability from a certain perspective

|marble index |1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
||R|R|R|R|R|R|R|R|R|R||||||
||||||||||||B|B|B|B|B|

from the god of view, there are 15 theaters, in each theater, Actors perform a certain performance
|select |1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|pick out red marble |x|x|x|x|x|x|x|x|x|x||||||
|pick out blue marble|||||||||||y|y|y|y|y|
|||||||||||||||||

the probability of randomly pulling out a blue marble is:
$$\frac{no.theaters\space that\space pick\space out\space red}{total no.theaters}=\frac{5}{15}$$


## 2.Understanding the Probability of Multiple Independent Events

Independent events are ones in which the outcome of one event does not affect the probability of the other event happening.
    
***For example, if you are using two dice, you might want to know what the probability is that you will roll a double 3. The chance that you will throw a 3 with one die does not affect the chance that you will throw a 3 with the second die, thus the events are independent.***

- Determine the probability of the first event. 

    For example, if the first event is throwing a 3 with one die, the number of favorable outcomes is 1, since there is only one 3 on a die. The number of possible outcomes is 6, since a die has six sides. So, your ratio will look like this: $probability={\frac  {1}{6}}$

- Determine the probability of the second event. To do this, set up the ratio, just like you did for the first event

    For example, if the second event is also throwing a 3 with one die, the probability is the same as the first event: $probability={\frac  {1}{6}}.$

- Multiply the probabilities of the individual events. This will give you the probability of both events happening

    For example, if the probability of throwing a 3 with one die is${\frac  {1}{6}}$, and the probability of throwing a 3 with a second die is also ${\frac  {1}{6}}$, to find the probability of both events happening, you would calculate ${\frac  {1}{6}}\times {\frac  {1}{6}}={\frac  {1}{36}}$. So, the probability of throwing double threes is 1 out of 36.

### 2.1.Understand the probability from a certain perspective

from the god of view, there are 36 theaters, in each theater, Actors perform a certain performance. there only exist one theater that play double 3

|1th dice|2rd dice||1th dice|2rd dice||1th dice|2rd dice|
|-|-|             -|-|-|              -|-|-|                             
|1|1|             |2|1|               |3|1|                           
|1|2|             |2|2|               |3|2|                           
|1|3|             |2|3|               |3|3|                           
|1|4|             |2|4|               |3|4|                           
|1|5|             |2|5|               |3|5|                           
|1|6|             |2|6|               |3|6|                           
|||

|1th dice|2rd dice||1th dice|2rd dice||1th dice|2rd dice|
|-|-|             -|-|-|              -|-|-|                                       
|4|1|             |5|1|               |6|1|                                     
|4|2|             |5|2|               |6|2|                                     
|4|3|             |5|3|               |6|3|                                     
|4|4|             |5|4|               |6|4|                                     
|4|5|             |5|5|               |6|5|                                     
|4|6|             |5|6|               |6|6|                                     
|||


## 3.Understanding the Probability of Conditional Events

A conditional event, also called a dependent event, is an event that may be affected by the event(s) that come before.

***For example, if you are drawing from a standard deck of cards, you might want to know what the probability is of drawing a heart on the first and second draws. Drawing a heart the first time affects the probability of it happening again, because once you draw one heart, there are fewer hearts in the deck, and fewer cards in the deck.***

- Determine the probability of the first event happening. 

    For example, if the first event is drawing a heart from a deck of cards, the number of favorable outcomes is 13, since there are 13 hearts in a deck. The number of possible outcomes is 52, since a deck has 52 cards total. So, your ratio will look like this: $probability={\frac  {13}{52}}$. Simplified, the probability is ${\frac  {1}{4}}.$

- Determine the probability of the second event happening, given that the first event already happened.[9] To do this, you will need to examine how the first event happening will affect the number of favorable and possible outcomes of the second event.

    For example, if you pulled a heart on your first draw, now there are only 12 hearts in the deck, and there are only 51 cards total. So, the probability of drawing a heart on your second draw is ${\frac  {12}{51}}$. Simplified, the probability is ${\frac  {4}{17}}.$

- Multiply the probabilities of the individual events. This will give you the probability of both events happening

    For example, if the probability of pulling a heart on your first draw is ${\frac  {1}{4}}$, and the probability of pulling a heart on your second draw, given that you pulled a heart on your first draw, is ${\frac  {4}{17}}$, to find the probability of both events happening, you would calculate: ${\frac  {1}{4}}\times {\frac  {4}{17}}={\frac  {4}{68}}={\frac  {1}{17}}$ So, the probability of pulling hearts on your first and second draw is 1 out of 17.


## 4.Understanding the Probability of Mutually Exclusive Events

Mutually exclusive events are events that cannot happen at the same time.

***For example, if you are rolling one die, you might want to know the probability of rolling a 3 or a 4. You cannot roll a 3 and a 4 with one die, so the events are mutually exclusive.***

- Determine the probability of the first event. 

    For example, if the first event is throwing a 3 with one die, the number of favorable outcomes is 1, since there is only one 3 on a die. The number of possible outcomes is 6, since a die has six sides. So, your ratio will look like this: $probability={\frac  {1}{6}}.$

- Determine the probability of the second event. To do this, set up the ratio, just like you did for the first event.

    For example, if the second event is throwing a 4 with one die, the probability is the same as the first event: $probability={\frac  {1}{6}}$

- Add the probabilities of the individual events. This will give you the probability of either event happening

    For example, if the probability of throwing a 3 with one die is ${\frac  {1}{6}}$, and the probability of throwing a 4 with one die is also ${\frac  {1}{6}}$, to find the probability of both events happening, you would calculate: ${\frac  {1}{6}}+{\frac  {1}{6}}={\frac  {2}{6}}={\frac  {1}{3}}$ So, the probability of throwing a 3 or a 4 is 1 out of 3.

## monty hall problem

![](https://brilliant-staff-media.s3-us-west-2.amazonaws.com/tiffany-wang/gWotbuEdYC.png)


In the problem, you are on a game show, being asked to choose between three doors. Behind each door, there is either a car or a goat. You choose a door. The host, Monty Hall, picks one of the other doors, which he knows has a goat behind it, and opens it, showing you the goat. (You know, by the rules of the game, that Monty will always reveal a goat.) Monty then asks whether you would like to switch your choice of door to the other remaining door. Assuming you prefer having a car more than having a goat, do you choose to switch or not to switch?

The solution is that switching will let you win twice as often as sticking with the original choice

||channger sel 1|channger sel 2|channger sel 3|
|-|-|-|-|
|is 1|T:40|F:40|F:40|
|is 2|F:40|T:40|F:40|
|is 3|F:40|F:40|T:40|
|||||


<table>
<tr>
  <th></th>
  <th colspan="2">channger sel 1st</th>
  <th colspan="2">channger sel 2rd</th>
  <th colspan="2">channger sel 3th</th>
</tr>

<tr>
  <th>host open</th>
  <th>2rd</th>
  <th>3th</th>
  <th>1st</th>
  <th>3th</th>
  <th>1st</th>
  <th>2rd</th>
</tr>

<tr>
  <th>1st is car</th>
  <th>T:20</th>
  <th>T:20</th>
  <th>-</th>
  <th>F:40</th>
  <th>-</th>
  <th>F:40</th>
</tr>
<tr>
  <th>2rd is car</th>
  <th>-</th>
  <th>F:40</th>
  <th>T:20</th>
  <th>T:20</th>
  <th>F:40</th>
  <th>-</th>
</tr>
<tr>
  <th>3th is car</th>
  <th>F:40</th>
  <th>-</th>
  <th>F:40</th>
  <th>-</th>
  <th>T:20</th>
  <th>T:20</th>
</tr>

</table>



## ref

Online Statistics Education: A Multimedia Course of Study (http://onlinestatbook.com/). Project Leader: David M. Lane, Rice University.
