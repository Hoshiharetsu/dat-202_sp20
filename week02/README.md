# Week 2

## Agenda
0. [Announcements](#announcements)
1. [Data sets](#readings)
2. [Talking about our schedule](#schedule)

## <span id="announcements">0. Announcements</span>

[This looks cool](https://pitt.libc  al.com/calendar/today/pghhistories). Unfortunately for most of us, it's in Oakland in the middle of the day. Anyone want to go, though? 

## <span id="readings">1. Talking about our data sets</span>

What have we found? Anything cool? Anything we want to talk about? Do you want to share them with me, and we'll start a data horde here on GitHub or something? 

## <span id="schedule">2. Talking about our schedule</span>

We should talk about our schedule.

## <span id="excel">3. Let's look at Excel

* Adding a trendline (deceptively straightforward!) [Office Support's version of this is here](https://support.office.com/en-us/article/choosing-the-best-trendline-for-your-data-1bb3c9e7-0280-45b5-9ab0-d0c93161daa8)
    * Linear: kind of the roughest approximation, good if there's an obvious visual trend already and you want to know its slope; y=bx + a, where b is slope and a is intercept
    * Exponential: when there appears to be a curve in the data (an exponential increase or decrease); there's an exponential increase or decrease between successive points; y = a * e^(bx), but they are a different a and b
    * Logarithmic: when there's a rapid change followed by a leveling-off
    * Polynomial: when there's not an obvious "shape" to the data, a few peaks and valleys
        * You have to specify a polynomial's "order," which correlates with how many bends (peaks and valleys) you see in the data (order: number of peaks/valleys - 1)
    * Power: similar to exponential, but points increase/decrease at roughly the same rate
    * Moving average: your data fluctuates too much to use a polynomial
* Showing the equation for the trendline.
* Looking at its reliability (R-squared: you want it to be close to 1)
    * "coefficient of determination"

## <span id="homework">x. Homework

### Readings
* [The Hidden Biases in Big Data](https://hbr.org/2013/04/the-hidden-biases-in-big-data)
* [How big data is unfair](https://medium.com/@mrtz/how-big-data-is-unfair-9aa544d739de)