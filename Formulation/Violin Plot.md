# Violin Plots
In general, violin plots are a method of plotting numeric data and can be considered a combination of the [box plot](https://en.wikipedia.org/wiki/Box_plot) with a [kernel density plot](https://en.wikipedia.org/wiki/Kernel_density_estimation). In the violin plot, we can find the same information as in the box plots:

-   median (a white dot on the violin plot)
-   interquartile range (the black bar in the center of violin)
-   the lower/upper adjacent values (the black lines stretched from the bar) — defined as `first quartile — 1.5 IQR` and `third quartile + 1.5 IQR` respectively. These values can be used in a simple outlier detection technique (Tukey’s fences) — observations lying outside of these “fences” can be considered outliers.


![](https://miro.medium.com/max/1040/1*TTMOaNG1o4PgQd-e8LurMg.png)


The unquestionable advantage of the violin plot over the box plot is that aside from showing the abovementioned statistics it also shows the entire distribution of the data. This is of interest, especially when dealing with multimodal data, _i.e._, a distribution with more than one peak.

# Implementation in Python

In this article we use the following libraries:

~~~
seaborn    0.9.0  
numpy      1.17.2  
pandas     0.25.1  
matplotlib 3.1.1
~~~

We start by defining the number of random observations we will draw from certain distributions, as well as setting the seed for reproducibility of the results.

~~~
N = 10 \*\* 4  
np.random.seed(42)
~~~

Then, we define a function plotting the following:

-   a histogram with a kernel density estimate (KDE)
-   a boxplot
-   a violin plot

We will use this function for inspecting the randomly created samples.

~~~python
def plot_comparison(x, title):  
    fig, ax = plt.subplots(3, 1, sharex=True)  
    sns.distplot(x, ax=ax[0])  
    ax[0].set_title('Histogram + KDE')  
    sns.boxplot(x, ax=ax[1])  
    ax[1].set_title('Boxplot')  
    sns.violinplot(x, ax=ax[2])  
    ax[2].set_title('Violin plot')  
    fig.suptitle(title, fontsize=16)  
    plt.show()
~~~

## Standard Normal distribution

We start with the most basic distribution — Standard Normal. We draw 10000 numbers at random and plot the results.
~~~
sample_gaussian = np.random.normal(size=N)  
plot_comparison(sample\_gaussian, 'Standard Normal Distribution')
~~~
![](https://miro.medium.com/max/1400/1*dLw-Ib14E5VNSR_w1eIFug.png)

Some of the observations we can make:

-   in the histogram we see the symmetric shape of the distribution
-   we can see the previously mentioned metrics (median, IQR, Tukey’s fences) in both the box plot as well as the violin plot
-   the kernel density plot used for creating the violin plot is the same as the one added on top of the histogram. Wider sections of the violin plot represent a higher probability of observations taking a given value, the thinner sections correspond to a lower probability.

I believe that showing these three plots together provides good intuition to what a violin plot actually is and what kind of information it contains.

## Log-normal distribution

In the second example, we consider the log-normal distribution, which is definitely more skewed than the Normal distribution.

~~~
sample\_lognormal = np.random.lognormal(size=N)  
plot\_comparison(sample\_lognormal, 'Log-normal Distribution')
~~~

![](https://miro.medium.com/max/1400/1*PeX4ZV2hxkZF2DOrZU6CSw.png)

## Mixture of Gaussians — bimodal

In the previous two examples, we have already seen that the violin plots contain more information than the box plot. This is even more apparent when we consider a multimodal distribution. In this example, we create a bimodal distribution as a mixture of two Gaussian distributions.

Without looking at a histogram/density plot, it would be impossible to spot the two peaks in our data.

![](https://miro.medium.com/max/1400/1*Uv7CXOXoYKM4B7ZkuvoXCQ.png)

# Advanced usage

Violin plots are often used to compare the distribution of a given variable across some categories. We present a few of the possibilities below. To do so, we load the `tips` dataset from `seaborn`.

tips = sns.load\_dataset("tips")

In the first example, we look at the distribution of the tips per gender. Additionally, we change the structure of the violin plot to display the quartiles only. Some other possibilities include `point` for showing all the observations or `box` for drawing a small box plot inside the violin plot.

~~~
ax = sns.violinplot(x="sex", y="tip", inner='quartile', data=tips)  
ax.set\_title('Distribution of tips', fontsize=16);
~~~

![](https://miro.medium.com/max/1400/1*6hGDrjT5BICKPBfE4BgrcQ.png)

We see that the overall shape and distribution of the tips are similar for both genders (quartiles very close to each other), but there are more outliers in the case of males.

In the second example, we investigate the distribution of the total bill amount per day. Additionally, we split by gender. Immediately we see that the largest difference in the shape of the distribution between genders happens on Fridays.

~~~
ax = sns.violinplot(x="day", y="total\_bill", hue="sex", data=tips)  
ax.set\_title('Distribution of total bill amount per day', fontsize=16);
~~~
![](https://miro.medium.com/max/1400/1*RCinTh4NKSYRW0L7tKTLyA.png)

In the last example, we investigate the same thing as in the previous case, however, we set `split=True`. By doing so, instead of 8 violins, we end up with four — each side of the violin corresponds to a different gender.

~~~
ax = sns.violinplot(x="day", y="total\_bill", hue="sex", split=True, data=tips)  
ax.set\_title('Distribution of total bill amount per day', fontsize=16);
~~~

![](https://miro.medium.com/max/1400/1*FFZjRMfziX_ALy4KVPrAkw.png)

# Conclusions

In this article, I showed what are the violin plots, how to interpret them and what are their advantages over the box plots. One last remark worth making is that the box plots do not adapt as long as the quartiles stay the same. We can modify the data in a way that the quartiles do not change, but the shape of the distribution differs dramatically. The following GIF illustrates the point.

![](https://miro.medium.com/max/1400/1*G5GJ9_M68FBFeZB2wePnjQ.gif)
