<center><img src="{{ site.baseurl }}/tutheaderbl.png" alt="Img"></center>

To add images, replace `tutheaderbl1.png` with the file name of any image you upload to your GitHub repository.

### Tutorial Aims

#### <a href="#section1"> 1.Import dqtq</a>

#### <a href="#section2"> 2. The second section</a>

#### <a href="#section3"> 3. The third section</a>

You can read this text, then delete it, and replace it with your text about your tutorial - what are the aims, what code do you need to achieve them?
---------------------------
We are using `<a href="#section_number">text</a>` to create anchors within our text - for example when you click on section one, the page will automatically go to where you have put `<a name="section_number"></a>`.

To create subheadings, you can use `#`, e.g. `# Subheading 1` creates a subheading with a large font size. The more hashtags you add, the smaller the text becomes. If you want to make text bold, you can surround it with `__text__`, which creates __text__. For italics, use only one understore around the text, e.g. `_text_`, _text_.

# Subheading 1
## Subheading 2
### Subheading 3

This is some introductory text for your tutorial. Explain the skills that will be learned and why they are important. Set the tutorial in context.

You can get all of the resources for this tutorial from <a href="https://github.com/ourcodingclub/CC-EAB-tut-ideas" target="_blank">this GitHub repository</a>. Clone and download the repo as a zip file, then unzip it.

<a name="section1"></a>

## 1. The first section


At the beginning of your tutorial you can ask people to open `RStudio`, create a new script by clicking on `File/ New File/ R Script` set the working directory, and load some packages, for example `ggplot2` and `dplyr`. You can surround package names, functions, actions ("File/ New...") and small chunks of code with backticks, which defines them as inline code blocks and makes them stand out among the text, e.g. `ggplot2`.

When you have a larger chunk of code, you can paste the whole code in the `Markdown` document and add three backticks on the line before the code chunks starts and on the line after the code chunks ends. After the three backticks that go before your code chunk starts, you can specify in which language the code  is written, in our case `R`.

To find the backticks on your keyboard, look towards the top left corner on a Windows computer, perhaps just above `Tab` and before the number one key. On a Mac, look around the left `Shift` key. You can also just copy the backticks from below.

```r
# Set the working directory
setwd("your_filepath")

# Load packages
library(ggplot2)
library(dplyr)
library(readr)
library(viridis)
```

<a name="section2"></a>

```r
# Import tree locations and diameters
tree_loc_diam_1_2_summ <- read_csv("tree_loc_diam_1_2.csv")
```

```r
# Plot bounding boxes
plot_bbox_1 <- read_csv("plot_bb_1.csv")  # Elephant plot
plot_bbox_2 <- read_csv("plot_bb_2.csv")  # No elephant plot
```

## 2. The second section

You can add more text and code, e.g.

```r
# Is there an effect of elephants on spatial clustering of trees?
# Split data frames to make two graphs
tree_loc_diam_1_summ <- tree_loc_diam_1_2_summ %>%
	filter(plot == "elephants")

tree_loc_diam_2_summ <- tree_loc_diam_1_2_summ %>%
	filter(plot == "no_elephants")

```

And finally, plot the data:

```r
# Create heatmaps based on density of trees
(elephant_plot <- ggplot(tree_loc_diam_1_summ, aes(x = dec_lon, y = dec_lat)) + 
	stat_density2d(aes(fill = ..level..), geom = "polygon") +
	scale_fill_viridis() + 
	geom_polygon(data = plot_bbox_1, aes(x = dec_lon, y = dec_lat), fill = NA, colour = "black") + 
	geom_point() + 
	xlim(min(plot_bbox_1$dec_lon) - 0.001, max(plot_bbox_1$dec_lon) + 0.001) + 
	ylim(min(plot_bbox_1$dec_lat) - 0.001, max(plot_bbox_1$dec_lat) + 0.001) + 
	xlab("Decimal Longitude") +
	ylab("Decimal Latitude") +
	labs(fill = "Tree Density") +
	theme_classic())

```

```r
(no_elephant_plot <- ggplot(tree_loc_diam_2_summ, aes(x = dec_lon, y = dec_lat)) + 
	stat_density2d(aes(fill = ..level..), geom = "polygon") +
	scale_fill_viridis() + 
	geom_polygon(data = plot_bbox_2, aes(x = dec_lon, y = dec_lat), fill = NA, colour = "black") + 
	geom_point() + 
	xlim(min(plot_bbox_2$dec_lon) - 0.001, max(plot_bbox_2$dec_lon) + 0.001) + 
	ylim(min(plot_bbox_2$dec_lat) - 0.001, max(plot_bbox_2$dec_lat) + 0.001) + 
	xlab("Decimal Longitude") +
	ylab("Decimal Latitude") +
	labs(fill = "Tree Density") +
	theme_classic())
```

```r
# Save the plots
ggsave(filename = "elephant_plot.png", plot = elephant_plot)
ggsave(filename = "no_elephant_plot.png", plot = no_elephant_plot)
```


At this point it would be a good idea to include an image of what the plot is meant to look like, so students can check they've done it right. Replace `IMAGE_NAME.png` with your own image file:

<center> <img src="{{ site.baseurl }}/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>

<a name="section1"></a>

## 3. The third section

What did you learn in this tutorial?

setwd("your_filepath"): this function sets the working directory.




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
