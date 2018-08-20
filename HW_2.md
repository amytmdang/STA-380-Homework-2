Flights at ABIA
===============

### Best Time of Day

For all of the below analysis on delayed flights, we have standardized
the number of delayed flights with the total number of flights in the
given time period, and only considered delays longer than 20 minutes. We
did not want to include a large number of trivial delays of only a few
minutes. We also separated flights departing from those arriving in
Austin with the hope of isolating delays happening at ABIA from those
all around the country. When looking at time of day, delays esspecially
for arrivals increases towards the end of the day because of the effects
from delays in previous connecting flights that day. Interestingly,
departure delays spike at 11 AM, which might be caused by heavy air
traffic as many people don't want to fly early in the morning.

![](HW_2_files/figure-markdown_strict/Time%20of%20Day-1.png)

### Best Day of the Week

A similar analysis was run below for delayed flights by aggregating
across the day of the week. The delay frequencies seem to follow busy
times of air travel (Friday and Sunday/Monday). While people commonly
avoid flying on weekends in general, Saturday actually shows the lowest
percentage of delayed flights while Thursday has an unexpectedly high
number of delays. Again, arrival delays are consistently more common
than departures because they have a much larger number of influencing
factors in airports around the country.

![](HW_2_files/figure-markdown_strict/Day%20of%20the%20Week-1.png)

### Best Time of Year

Now looking at a weekly scale, we can see seasonal and event-driven
fluctuations in flight delays such as during the holidays, summer
vacations, and SXSW. An important observation to note that we have seen
in some form above, is that departure delays follow arrival delay
patterns almost exaclty, just to a lesser degree. If we assume a
majority of delayed departures from ABIA are caused by delayed arrivals,
the consistent difference between them can be interpreted as the arrival
delays that were compensated for at ABIA. The fall season has
significantly less delayed flights, likely to lower traffic in general.
Here we can see the gap between arrivals and departures approach zero as
the delay frequency approaches 5%. This may be the actual amount of
departures that were delayed due to issues at ABIA.

![](HW_2_files/figure-markdown_strict/Time%20of%20Year-1.png)

### Best Locations

Aggregating flights over the entire year, we can see the best and worst
airports in terms of flight delays to and from Austin. A majority of the
most delayed destinations are in the north of the country, which sees a
much higher rate of delays simply due to weather. As expected the
largest airports including JFK, Newark, and O'hare also show the most
flight delays going both ways. The exception to this is LAX, which shows
a surpsingly low rate of delays (under 10% overall). Other than LAX, the
least delayed airports are generally smaller than average.

![](HW_2_files/figure-markdown_strict/Airports-1.png)

### Traffic

The histogram below shows the frequency of flights based on their flight
times. The majority of flights to and from Austin are less than one
hour, most of which go through Houston and Dallas. The next peak in
number of flights is in the 2.5 hour range and major airports within
this range include Pheonix, Denver, and Chicago. The far right tail
includes the longest flights to areas in the US such as Seattle and
Boston. These inferences are supported by the map below, which shows the
number of flights departing Austin by airport. The map for flights
arriving in Austin is virtually identical.

![](HW_2_files/figure-markdown_strict/Maps-1.png)![](HW_2_files/figure-markdown_strict/Maps-2.png)

Author Attribution
==================

### PCA

After pre-proccessing all authors in the train and test set, we ran a
principal component analysis and the variance explained is shown in the
graph below. The main classifications shown in the first principal
components seem to primarily distinguish between articles about China
and articles about global economics and finance. For example, the first
PC has strong positive coefficents for the words China, Hong Kong,
Chinese, and Communist, and has negative coefficients for words such as
computer, software, quarter, bank, funds, etc. The next two components
are similar, but there is variation in the focus on either economics or
politics.

![](HW_2_files/figure-markdown_strict/PCA-1.png)

### Boosting

Individual words are weak classifiers becauese they are relatively
infrequent across so many documents. Since boosting combines weak
classifiers into stronger ones, we thought this approach would best for
connecting sets of words to authors. Accuracy on the training documents
was high at 85.6%, but test accuracy dropped to 39%.

<table>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Training
</th>
<th style="text-align:right;">
Test
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Accuracy
</td>
<td style="text-align:right;">
0.8524
</td>
<td style="text-align:right;">
0.3956
</td>
</tr>
</tbody>
</table>
<br>

### Random Forest

Random Forset is a generally strong model for classification, and we
wanted to use this as a baseline to compare to Boosting. With 250 trees,
the test accuracy equalled 50%, which is substantially higher than that
of the boosting model. However there is large variability in the accury
of predicting individual authors, which can be seen in the table of
error rates below. For example, the model accuracy was over 90% when the
author of a document was Aaron Pressman, but less than 30% for Scott
Hillis. This is because 30 out of 50 times, the model predicted Scott's
articles to be written by Samuel Perry. This is one example of two
others having similar word frequencies, making it hard to distinguish
between their works using just a bag of words.

<table>
<tbody>
<tr>
<td style="text-align:left;">
RF Test Accuracy
</td>
<td style="text-align:right;">
0.4936
</td>
</tr>
</tbody>
</table>
<table>
<tbody>
<tr>
<td style="text-align:left;">
AaronPressman
</td>
<td style="text-align:right;">
0.08
</td>
</tr>
<tr>
<td style="text-align:left;">
AlanCrosby
</td>
<td style="text-align:right;">
0.16
</td>
</tr>
<tr>
<td style="text-align:left;">
AlexanderSmith
</td>
<td style="text-align:right;">
0.36
</td>
</tr>
<tr>
<td style="text-align:left;">
BenjaminKangLim
</td>
<td style="text-align:right;">
0.42
</td>
</tr>
<tr>
<td style="text-align:left;">
BernardHickey
</td>
<td style="text-align:right;">
0.40
</td>
</tr>
<tr>
<td style="text-align:left;">
BradDorfman
</td>
<td style="text-align:right;">
0.44
</td>
</tr>
<tr>
<td style="text-align:left;">
DarrenSchuettler
</td>
<td style="text-align:right;">
0.18
</td>
</tr>
<tr>
<td style="text-align:left;">
DavidLawder
</td>
<td style="text-align:right;">
0.22
</td>
</tr>
<tr>
<td style="text-align:left;">
EdnaFernandes
</td>
<td style="text-align:right;">
0.42
</td>
</tr>
<tr>
<td style="text-align:left;">
EricAuchard
</td>
<td style="text-align:right;">
0.42
</td>
</tr>
<tr>
<td style="text-align:left;">
FumikoFujisaki
</td>
<td style="text-align:right;">
0.04
</td>
</tr>
<tr>
<td style="text-align:left;">
GrahamEarnshaw
</td>
<td style="text-align:right;">
0.32
</td>
</tr>
<tr>
<td style="text-align:left;">
HeatherScoffield
</td>
<td style="text-align:right;">
0.26
</td>
</tr>
<tr>
<td style="text-align:left;">
JaneMacartney
</td>
<td style="text-align:right;">
0.56
</td>
</tr>
<tr>
<td style="text-align:left;">
JanLopatka
</td>
<td style="text-align:right;">
0.26
</td>
</tr>
<tr>
<td style="text-align:left;">
JimGilchrist
</td>
<td style="text-align:right;">
0.04
</td>
</tr>
<tr>
<td style="text-align:left;">
JoeOrtiz
</td>
<td style="text-align:right;">
0.28
</td>
</tr>
<tr>
<td style="text-align:left;">
JohnMastrini
</td>
<td style="text-align:right;">
0.24
</td>
</tr>
<tr>
<td style="text-align:left;">
JonathanBirt
</td>
<td style="text-align:right;">
0.40
</td>
</tr>
<tr>
<td style="text-align:left;">
JoWinterbottom
</td>
<td style="text-align:right;">
0.20
</td>
</tr>
<tr>
<td style="text-align:left;">
KarlPenhaul
</td>
<td style="text-align:right;">
0.24
</td>
</tr>
<tr>
<td style="text-align:left;">
KeithWeir
</td>
<td style="text-align:right;">
0.24
</td>
</tr>
<tr>
<td style="text-align:left;">
KevinDrawbaugh
</td>
<td style="text-align:right;">
0.42
</td>
</tr>
<tr>
<td style="text-align:left;">
KevinMorrison
</td>
<td style="text-align:right;">
0.40
</td>
</tr>
<tr>
<td style="text-align:left;">
KirstinRidley
</td>
<td style="text-align:right;">
0.58
</td>
</tr>
<tr>
<td style="text-align:left;">
KouroshKarimkhany
</td>
<td style="text-align:right;">
0.18
</td>
</tr>
<tr>
<td style="text-align:left;">
LydiaZajc
</td>
<td style="text-align:right;">
0.10
</td>
</tr>
<tr>
<td style="text-align:left;">
LynneO'Donnell
</td>
<td style="text-align:right;">
0.02
</td>
</tr>
<tr>
<td style="text-align:left;">
LynnleyBrowning
</td>
<td style="text-align:right;">
0.08
</td>
</tr>
<tr>
<td style="text-align:left;">
MarcelMichelson
</td>
<td style="text-align:right;">
0.10
</td>
</tr>
<tr>
<td style="text-align:left;">
MarkBendeich
</td>
<td style="text-align:right;">
0.34
</td>
</tr>
<tr>
<td style="text-align:left;">
MartinWolk
</td>
<td style="text-align:right;">
0.28
</td>
</tr>
<tr>
<td style="text-align:left;">
MatthewBunce
</td>
<td style="text-align:right;">
0.22
</td>
</tr>
<tr>
<td style="text-align:left;">
MichaelConnor
</td>
<td style="text-align:right;">
0.36
</td>
</tr>
<tr>
<td style="text-align:left;">
MureDickie
</td>
<td style="text-align:right;">
0.62
</td>
</tr>
<tr>
<td style="text-align:left;">
NickLouth
</td>
<td style="text-align:right;">
0.22
</td>
</tr>
<tr>
<td style="text-align:left;">
PatriciaCommins
</td>
<td style="text-align:right;">
0.30
</td>
</tr>
<tr>
<td style="text-align:left;">
PeterHumphrey
</td>
<td style="text-align:right;">
0.20
</td>
</tr>
<tr>
<td style="text-align:left;">
PierreTran
</td>
<td style="text-align:right;">
0.20
</td>
</tr>
<tr>
<td style="text-align:left;">
RobinSidel
</td>
<td style="text-align:right;">
0.16
</td>
</tr>
<tr>
<td style="text-align:left;">
RogerFillion
</td>
<td style="text-align:right;">
0.14
</td>
</tr>
<tr>
<td style="text-align:left;">
SamuelPerry
</td>
<td style="text-align:right;">
0.40
</td>
</tr>
<tr>
<td style="text-align:left;">
SarahDavison
</td>
<td style="text-align:right;">
0.32
</td>
</tr>
<tr>
<td style="text-align:left;">
ScottHillis
</td>
<td style="text-align:right;">
0.72
</td>
</tr>
<tr>
<td style="text-align:left;">
SimonCowell
</td>
<td style="text-align:right;">
0.28
</td>
</tr>
<tr>
<td style="text-align:left;">
TanEeLyn
</td>
<td style="text-align:right;">
0.62
</td>
</tr>
<tr>
<td style="text-align:left;">
TheresePoletti
</td>
<td style="text-align:right;">
0.50
</td>
</tr>
<tr>
<td style="text-align:left;">
TimFarrand
</td>
<td style="text-align:right;">
0.24
</td>
</tr>
<tr>
<td style="text-align:left;">
ToddNissen
</td>
<td style="text-align:right;">
0.32
</td>
</tr>
<tr>
<td style="text-align:left;">
WilliamKazer
</td>
<td style="text-align:right;">
0.64
</td>
</tr>
</tbody>
</table>
<br>

Association Rules
=================

The plot below shows the overall prior frequencies of items in our
dataset of transactions. Whole milk is the most frequenly purchased by a
considerable margin, followed by vegetables, rolls/buns, soda, and so
on. Before looking for associations, we know that many of these items
will have to be frequently purchased together, so we would want a
significant confidence in any rules we find in predicting these items.

![](HW_2_files/figure-markdown_strict/unnamed-chunk-3-1.png)

After trying different combinations, we decided on a support metric of
0.005 and confidence of 0.5 when creating our association rules. We also
limited the length of the item list in the each rule to five items. The
confidence was the most important factor to consider, given the high
frequency of some of the items discussed before. A confidence of 0.5
means that all rules follow the format of "Given this item list there is
at least a 50% chance of the person also buying X." These parameters
yielded a set of 120 assocation rules shown below. The highest
confidence rules have a lift of between 2 and 3 times above the prior
probabilities. There is also a large numbers of rules at this level of
lift with a confidence barely above 50%. However, we felt that 120
assocation rules provides a reasonable amount of predictive itemsets and
predicted items. Also, the highest lift rules all have relatively low
support as expected because the most informative rules should be less
common.

    ## To reduce overplotting, jitter is added! Use jitter = 0 to prevent jitter.

![](HW_2_files/figure-markdown_strict/unnamed-chunk-5-1.png)

The rules shown below have the highest support and confidence,
respectively, and they all contain Whole Milk on the right hand side of
the rule. While we know whole milk is already the most commonly
purchased product, the lift on all of these rules is above 2, meaning
that the conditional probability of a person getting whole milk is
double that of the probability before they have any other items.

<table class="table table-striped table-hover" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
lhs
</th>
<th style="text-align:left;">
rhs
</th>
<th style="text-align:right;">
support
</th>
<th style="text-align:right;">
confidence
</th>
<th style="text-align:right;">
lift
</th>
<th style="text-align:right;">
count
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
{tropical fruit,yogurt}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0151500
</td>
<td style="text-align:right;">
0.5173611
</td>
<td style="text-align:right;">
2.024770
</td>
<td style="text-align:right;">
149
</td>
</tr>
<tr>
<td style="text-align:left;">
{other vegetables,yogurt}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0222674
</td>
<td style="text-align:right;">
0.5128806
</td>
<td style="text-align:right;">
2.007235
</td>
<td style="text-align:right;">
219
</td>
</tr>
</tbody>
</table>
<table class="table table-striped table-hover" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
lhs
</th>
<th style="text-align:left;">
rhs
</th>
<th style="text-align:right;">
support
</th>
<th style="text-align:right;">
confidence
</th>
<th style="text-align:right;">
lift
</th>
<th style="text-align:right;">
count
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
{root vegetables,tropical fruit,yogurt}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0056940
</td>
<td style="text-align:right;">
0.700
</td>
<td style="text-align:right;">
2.739554
</td>
<td style="text-align:right;">
56
</td>
</tr>
<tr>
<td style="text-align:left;">
{other vegetables,pip fruit,root vegetables}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0054906
</td>
<td style="text-align:right;">
0.675
</td>
<td style="text-align:right;">
2.641713
</td>
<td style="text-align:right;">
54
</td>
</tr>
<tr>
<td style="text-align:left;">
{butter,whipped/sour cream}
</td>
<td style="text-align:left;">
{whole milk}
</td>
<td style="text-align:right;">
0.0067107
</td>
<td style="text-align:right;">
0.660
</td>
<td style="text-align:right;">
2.583008
</td>
<td style="text-align:right;">
66
</td>
</tr>
</tbody>
</table>
A network graph of our 120 association rules using a ForceAtlas 2 layout
in Gephi is shown below. Whole milk, root vegetables, other vegetables,
and yogurt appear as the most frequently predicted items from our rules.
However, they are not all necessarily the most purchased products
overall. Rolls and Soda do not appear significant in associations, even
though they are relatively common in item baskets. Whole milk is again
the most predicted item by far, and a grocery store can leverage this
since it is already the most commonly purchased item by promoting deals
with known associated products such as root vegetables and yogurt (seen
above).

![](HW_2_files/figure-markdown_strict/GroceryRules.png)
