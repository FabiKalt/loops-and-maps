# <center>Are for loops really that "bad"?</center>
## <center>An exploration into the differences between for() loops and mapping functions using the `Purrr` Package</center>
###### _Created by Fabian Kalt_, s1968412@ed.ac.uk

### Tutorial Aims

#### <a href="#section1"> 1. Find answer to "Are `for()` loops bad?"</a>

#### <a href="#section2"> 2. Explore the differences between `for()` loops and `map()` functions</a>

#### <a href="#section3"> 3. Explore mapping functions of the Purrr package</a>

test 00:44


All the resources for this tutorial can be downloaded from [this Github repository](https://github.com/EdDataScienceEES/tutorial-FabiKalt). Clone and download the repo as a zipfile, then unzip it.


### Welcome
Welcome to this workshop where we explore the question of ‘Are for() loops really that bad?’. This tutorial builds on basic knowledge on `for()` loops, particularly on the Coding Club tutorial [Intro to Functional Programming](https://ourcodingclub.github.io/tutorials/funandloops/) and is designed for those who want to delve a bit deeper into functional programming and take a look at what happens behind the scenes. Have you ever wondered why many coders in the R universe consider using for() loops bad practice? We learned previously in the Coding Club tutorial that `for()` loops are a great tool to minimise replication of code by allowing us to run the same operation on a group of objects. We also covered, that `for()` loops can get a bit slow if complex functions or large data datasets are involved and that they might be more difficult to read compared to other methods of functional programming such as the apply() functions for example. But what really is the difference between `for()` loops and other functional programming methods? In this tutorial we will tackle this question and take a look behind the scenes of functional programming. To explore this question we will compare `for()` loops with the map() functions of the Purr package, using a personal real life analogy of bread baking.





<a name="section1"></a>

## 1. Bread Recipes

In order to visualize the difference between for() loops and other functional programming methods, I would like to diverge from the coding world for a bit and take a dip into a hobby of mine – sourdough bread baking! During the first Covid-19 lockdown in spring 2020, like many others, I took up bread baking to make good use of the fact that I was home every day. After achieving some decent results (see photos!) and a little bit of experimenting with different bread recipes, I noticed that a lot of the recipes were very similar and only changed a little between different bread types. Now, since baking sourdough bread is quite an elaborate process (the first mixing of the dough to retrieving a fresh sourdough loaf from the oven it takes about 36 hours!), there are a lot of steps involved and as such the recipes in the cookbook can be quite long. This is an example of two recipes, one for a rye sourdough and one for a wholemeal sourdough bread:

1.	Rye: 10% rye flour, 90% plain white
2.	Wholemeal: 10% wholemeal flour, 90% plain white


#- photo 2x of recipe -#

Can you spot the difference? Exactly, only the flour input changed. But still, we have all this text for the remaining steps. Let's try to make this recipe more efficient by generalising the recipe and removing unnecessary lines of text.

Steps:			Rye			wholemeal			(seeds)
1 flour mix
2
3
(easy to see change. Could add more wholemeal for a heartier bread. Easy to make own recipes now)

Let’s keep that in mind for now and move back to the coding world.



<a name="section2"></a>

## 2. For() loops and map() functions

For the coding part of this tutorial, we will be using data from an experiment I conducted during lockdown on the rising time of doughs. I explored how long the dough needs to proof in order to grow to double its size, depending on the composition of flour and the temperature of the environment.


{% capture callout %}
Info on dough behavior/excursion:
An essential part of bread making is to give the dough time to rise. This process is called proofing. Flour, water and yeast is mixed. The yeast bacteria feeds on the sugars in the flour and multiply. This chemical reaction releases CO2 gas which ideally gets captured in the developed gluten structure of the dough. This gives the bread its rise during the proof and later on makes the bread rise in the oven and also guarantees a fluffy and airy crumb of the bread. This chemical reaction is sped up by warmer temperatures during the proofing process. The flour type used also has an impact on the reaction speed as the sugars in the flour are more or less accessible for the yeast bacteria to process. Note that the temperature not only affects the proofing time but also affects the taste! (e.g. a slow proof makes for a heartier and more tangy bread)
{% endcapture %}
{% include callout.html content=callout colour=alert %}

























