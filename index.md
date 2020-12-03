# <center>Are for loops really that "bad"?</center>
## <center>An exploration into the differences between for() loops and mapping functions using the `Purrr` Package</center>
###### _Created by Fabian Kalt_, s1968412@ed.ac.uk

### Tutorial Aims

#### <a href="#section1"> 1. Find answer to "Are `for()` loops bad?"</a>

#### <a href="#section2"> 2. Explore the differences between `for()` loops and `map()` functions</a>

#### <a href="#section3"> 3. Explore mapping functions of the Purrr package</a>


{% capture callout %}
All the resources for this tutorial can be downloaded from [this Github repository](https://github.com/EdDataScienceEES/tutorial-FabiKalt). Clone and download the repo as a zipfile, then unzip it.
{% endcapture %}
{% include callout.html content=callout colour=alert %}

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





























At the beginning of your tutorial you can ask people to open `RStudio`, create a new script by clicking on `File/ New File/ R Script` set the working directory and load some packages, for example `ggplot2` and `dplyr`. You can surround package names, functions, actions ("File/ New...") and small chunks of code with backticks, which defines them as inline code blocks and makes them stand out among the text, e.g. `ggplot2`.

When you have a larger chunk of code, you can paste the whole code in the `Markdown` document and add three backticks on the line before the code chunks starts and on the line after the code chunks ends. After the three backticks that go before your code chunk starts, you can specify in which language the code is written, in our case `R`.

To find the backticks on your keyboard, look towards the top left corner on a Windows computer, perhaps just above `Tab` and before the number one key. On a Mac, look around the left `Shift` key. You can also just copy the backticks from below.

```r
# Set the working directory
setwd("your_filepath")

# Load packages
library(ggplot2)
library(dplyr)
```



You can add more text and code, e.g.

```r
# Create fake data
x_dat <- rnorm(n = 100, mean = 5, sd = 2)  # x data
y_dat <- rnorm(n = 100, mean = 10, sd = 0.2)  # y data
xy <- data.frame(x_dat, y_dat)  # combine into data frame
```

Here you can add some more text if you wish.

```r
xy_fil <- xy %>%  # Create object with the contents of `xy`
	filter(x_dat < 7.5)  # Keep rows where `x_dat` is less than 7.5
```

And finally, plot the data:

```r
ggplot(data = xy_fil, aes(x = x_dat, y = y_dat)) +  # Select the data to use
	geom_point() +  # Draw scatter points
	geom_smooth(method = "loess")  # Draw a loess curve
```

At this point it would be a good idea to include an image of what the plot is meant to look like so students can check they've done it right. Replace `IMAGE_NAME.png` with your own image file:

<center> <img src="{{ site.baseurl }}/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>

<a name="section1"></a>

## 3. The third section

More text, code and images.

This is the end of the tutorial. Summarise what the student has learned, possibly even with a list of learning outcomes. In this tutorial we learned:

##### - how to generate fake bivariate data
##### - how to create a scatterplot in ggplot2
##### - some of the different plot methods in ggplot2

We can also provide some useful links, include a contact form and a way to send feedback.

For more on `ggplot2`, read the official <a href="https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf" target="_blank">ggplot2 cheatsheet</a>.

Everything below this is footer material - text and links that appears at the end of all of your tutorials.

<hr>
<hr>

#### Check out our <a href="https://ourcodingclub.github.io/links/" target="_blank">Useful links</a> page where you can find loads of guides and cheatsheets.

#### If you have any questions about completing this tutorial, please contact us on ourcodingclub@gmail.com

#### <a href="INSERT_SURVEY_LINK" target="_blank">We would love to hear your feedback on the tutorial, whether you did it in the classroom or online!</a>

<ul class="social-icons">
	<li>
		<h3>
			<a href="https://twitter.com/our_codingclub" target="_blank">&nbsp;Follow our coding adventures on Twitter! <i class="fa fa-twitter"></i></a>
		</h3>
	</li>
</ul>

### &nbsp;&nbsp;Subscribe to our mailing list:
<div class="container">
	<div class="block">
        <!-- subscribe form start -->
		<div class="form-group">
			<form action="https://getsimpleform.com/messages?form_api_token=de1ba2f2f947822946fb6e835437ec78" method="post">
			<div class="form-group">
				<input type='text' class="form-control" name='Email' placeholder="Email" required/>
			</div>
			<div>
                        	<button class="btn btn-default" type='submit'>Subscribe</button>
                    	</div>
                	</form>
		</div>
	</div>
</div>
