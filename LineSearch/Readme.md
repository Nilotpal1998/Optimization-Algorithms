<h1><u>The Golden Section</u></h1>
<p>The <b>Golden Section Search</b> is  mainly a line search technique which helps us to find the extremum of a given function inside a specified interval.This reacts differently for unimodal and multimodal functions :-</p>
<p>1.For any unimodal funtion we find the extremum lying within the interval .</p>
<p>2.For multimodal data we will be able to find any one of the extremum lying within the interval.</p>
<p>This mainly itteratively narrows down the interval in which the extremum lies and due to this phenomenon the algorithm becomes very slow but the process becomes acutely robust.</p>
<p>Now , the main aim will be to select the probes which will drive us to the optimum interval level.Thus we will be going for our <b>probe selection</b>.We can go for the codes for our probe selection. </p>
<h3>Visualisation Of The Function</h3>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/LineSearch/golden%20section%20images/Funtion.png" width="350" title="Convex Function">
</p>
<h3>Analysis</h3>
<p>The analysis can be reffered from the following figure :-</p>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/LineSearch/golden%20section%20images/325px-GoldenSectionSearch.png" width="350" title="Convex Function">
</p>
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/LineSearch/golden%20section%20images/Interval_Cut.png" width="350" title="Convex Function">
</p>
<p>Here , we can clearly see that we are focussing on reduction of interval only on one side at a time i.e we fix one side at a time and reduce the other side of the interval,which is what we are exactly done in the algorithm.</p>
<h3>Convergence</h3>
The convergence rate we can be analysed from the below graph : -
<p align="center">
  <img src="https://github.com/Nilotpal1998/Optimization-Algorithms/blob/main/LineSearch/golden%20section%20images/Convergence.png" width="350" title="Convex Function">
</p>
<h3>Source</h3>
[Wikipedia](https://en.wikipedia.org/wiki/Golden-section_search "Wikipedia")
