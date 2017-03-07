Introduction to MonteJS
===================


**MonteJS** is a Javascript library that provides tools to help eliminate repetitive tasks when creating D3 charts. In addition to customization tools,  MonteJS comes with a wide selection of prebuilt, easily customizable D3 charts. The main philosophy behind MonteJS is to stay out of your way. MonteJS (hereafter referred to as **Monte**) adds a large amount of flexibility when working with D3 without reworking the way you work with D3. Anything you do with D3 you can still do while using Monte. Monte's goal is to enable you to create and customize D3 charts quicker and easier. This Introduction will walk you through creating and customizing D3 charts enhanced with Monte

----------


MonteJS Features
-------------

####Options
One of the foundation features of monte is the options object. Monte Options provide a easy way to set static and dynamic parameters for a created chart. Monte also Monte comes with a number of pre created option types such as:
> - **boundingWidth:** Sets the width of the bounding area of the chart.
> - **boundingHeight:** Sets the width of the bounding area of the chart.
> - **chartCss:** An option that allows the user to pass CSS styles to the chart.
> - **margin:** An object with 4 properties (top, left, bottom, right) used to set the chart margins.
> - **suppressAxes:** Suppress the display of the axes.
> - **pointSize:** Sets the width of the bounding area of the chart.
> - **transition:** Sets the width of the bounding area of the chart.
> - **resize:** Contains a reference to a resize function that is called when the window resizes.
> - **xProp:** The property name of the value for the X coordinate passed to the scale function.
> - **xScale:** The scale function for X values.
> - **xAxisCustomize:** Callback function to customize the X axis, such as tick count and format.
> - **xDomainCustomize:** Callback function to customize the X extent.
> - **xLabel:** The label for the x axis.
> - **yProp:** The property name of the value for the Y coordinate passed to the scale function.
> - **yScale:** The scale function for Y values.
> - **yAxisCustomize:** Callback function to customize the X axis, such as tick count and format.
> - **yDomainCustomize:** Callback function to customize the Y extent.
> - **yAxisTransform:** The label for the y axis.
You can pass a variable or an expression as a static option.  Monte also supports passing callback functions as options. 
#####Options Instances
In addition to the option types that Monte provides, Monte comes with a number of precreated options that you can use to populate some of those types.  Some of these options can be used to create visual elements ( like chart backgrounds or  overlay elements), while others can be used to calculate locations for other visual elements, or apply number formatting.
TODO -- expand this area
Some Instance example ( TODO-- is 'instance' the right word?)
> - **axisNoTicks** TODO--Add Description
> - **axisWholeNumberFormat** TODO--Add Description
> - **axisYLabelGenerator** TODO--Add Description
> - **needleRoundedEnd** TODO--Add Description
> - **needleFlatEnd** TODO--Add Description
> - **....and more to be added**
TODO-- complete list should be added to API docs.... 


Monte also adds the ability for you to create your own special type of option called an extension. More about that in the next section

####Extensions
TODO This is where we would talk about extensions
Extensions allow you to create custom code options for you particular graph. Monte comes with a number of pre created extension to provide useful functionality for you charts. These include:
> - **ExtArc:** TODO --Add Description
> - **ExtAxisTickTransform:** TODO --Add Description
> - **ExtAxisLabelWrap:** TODO --Add Description
> - **ExtCrosshair:** TODO --Add Description
> - **ExtFrame:** TODO --Add Description
> - **ExtGrid:** TODO --Add Description
> - **ExtHorizontalLines:** TODO --Add Description
> - **ExtVerticalLines:** TODO --Add Description
> - **ExtLabel:** TODO --Add Description
> - **ExtPolarGrid:** TODO --Add Description
> - **ExtPolarLine:** TODO --Add Description
> - **ExtPolarRotateLabel:** TODO --Add Description
> - **ExtPolarTicks:** TODO --Add Description
> - **ExtBarBg:** TODO --Add Description
> - **ExtHorizontalBarBg:** TODO --Add Description
> - **ExtReferenceLine:** TODO --Add Description
> - **ExtSelectionRect:** TODO --Add Description

####Monte Charts
Monte comes with a number of chart types in 2 different types of chart families; Axes charts and Polar charts. In addition Monte has a few non chart type pre-made visualizations Currently Monte ships with the following chart types:

>**Axes Charts**
> - StackEdit
> - AreaChart
> - AxesChart
> - BarChart
> - HorizontalBarChart
> - LineChart
> - ScatterPlotChart
> - SparklineChart

>**Polar Charts**
> - ArcChart
> - GaugeChart
> - PolarChart
> - SegmentChart
> - WedgeChart
> 
>**Other Charts**
> - IconArray


Monte Examples
-------------

Lets walk through some examples on how to use Monte to create customizable D3 charts. To use Monte first make sure you include a reference to the MonteJS library. Monte can be installed using NPM or downloaded from MonteJS.com.  You will also need to add a reference to D3 ( Monte doesn't work without D3 installed!).  

Once you have included these references you can add a Monte chart. To add a Monte chart to your page you create an instance of the type of chart you want like so:

```
var myMonteChart = new monte.LineChart();
```

So -- Lets show a complete example of a start page . In this page we will add some sample data to show a bar chart
> **Note:** We have included JSFiddle examples for each step of the walkthrough.

 [(Example 1)][1] 
```
<!DOCTYPE html>
<html>
<head>
	<script type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
	<script type="text/javascript" src="https://unpkg.com/monte@0.0.0-alpha27/build/monte.min.js"></script>
  	<script type='text/javascript'>//<![CDATA[
		window.onload=function(){
			var BAR_DATA = [{
  				"id": "First",
  				"value": 200,
  				"css": "first-bar"
			},{
  				"id": "Second",
  				"value": 150,
  				"css": "second-bar"
			}];
		var barChart = new monte.BarChart('#barChart').data(BAR_DATA);
		}//]]> 
		</script>  
	</head>
	<body>
  		<div id="barChart"></div>
	</body>
</html>
```
Note that when we call the Constructor function to create a new Monte chart we pass a JQuery Selector string which is a reference to the HTML element that will contain the chart. Once we view the page we should see a small, 2 element bar graph. Lets take a quick look at what Monte created. When we inspect the page here is what we see: 
```
<div id="barChart">
 <svg monte-chart-0="" class="monte-chart monte-bar-chart" width="250" height="250"> 
	 <defs>
			 <clipPath id="drawPath0">
				 <rect x="0" y="0" width="210" height="220"></rect>
			 </clipPath>
	 </defs>
	 <g class="monte-bg" transform="translate(40, 0)"></g>
	 <g class="monte-support" transform="translate(40, 0)">
		 ...[This is where Axes are Drawn]...
	 </g>
	 <g class="monte-selection" transform="translate(40, 0)"></g>
	 <g class="monte-draw" transform="translate(40, 0)">
			  ... [This is where the Graph is drawn] ...
		  </g>
	 <g class="monte-overlay" transform="translate(40, 0)"></g>
 </svg>
</div>
```

If we take a look at the generated HTML we will notice that Monte  has created an SVG element with 5 child groups. By default Monte creates 5 draw layers for each Monte chart, these are:

 - **monte-bg** -- The Background layer 
 - **monte-support** -- The Support layer. This layer contains elements that you want to appear below the chart but above the background. By default this is where Monte draws Chart Axes.
 - **monte-selection** -- The Selection layer.  ( TODO: Need more info -- what normally goes here?)
 - **monte-draw** -- The Draw layer. This is where Monte creates the rendered chart elements.
 - **monte-overlay** -- The Overlay layer. This is where top level items, like tooltips, would go.

Later we will explore how Monte allow you to access and add items to these layers. For now lets use some of Monte's features to customize our graph. We will start by adding a few Monte option.

If we look at our first Monte Graph we notice that the top most y axis tick is cut off. Lets fix it by adding a margin to the top of our graph. We can do this by creating a Monte options object and setting a margin option like this:
```
var barOpts = {
				margin: {
    				top: 20,
  				},
			};
```
This object, barOpts, has a single object margin with a top property set to 20. All we need to do to use this options object is pass it to our Monte chart constructor like this:
```
var barChart = new monte.BarChart('#barChart', barOpts).data(BAR_DATA);
```
 [(Example 2)][2] 
As we can see the second argument to a Monte chart constructor is an options object that Monte uses when creating a chart. to add addition customization, just add additional options to the options object.  Let continue customizing our chart by adding a few more options.

OK, lets make the graph a little smaller by adding some bounds. We'll add the following:
```
var barOpts = {
				boundingWidth: 200,
  				boundingHeight: 200,
				margin: {
    				top: 20,
  				},
			};
```
 [(Example 3)][3] 
Now when we view our page we can see that the graph is a little smaller. Neat!

In addition to static values you can also add functions as options.  Lets say you wanted the Graph to resize to fit the window whenever the window resizes, you could accomplish that with an additional option like so:
```
resize: new monte.HorizontalResizer(),
```
Now let's test this out by loading the page and resizing the browser window. You should see the graph resize as the window width changes.  [(Example 4)][4]

You can also use options to load CSS styles for the chart. First lets declare some CSS styles:
```
.bar-style {
  stroke: blue;
  stroke-width: 1;
  fill: yellow;
}
```
Then we will reference the style by class name.
```
var barOpts = {
				boundingWidth: 200,
  				boundingHeight: 200,
  				css: 'bar-styles',
  				margin: {
    				top: 20,
  				},
			};
```
[(Example 5)][5] 
Now when we run it we see 2 yellow bars with blue outlines. We can 


[1]:https://jsfiddle.net/MarkRocks/uunLd2wh/1/
[2]:https://jsfiddle.net/MarkRocks/uunLd2wh/2/
[3]:https://jsfiddle.net/MarkRocks/uunLd2wh/3/
[4]:https://jsfiddle.net/MarkRocks/uunLd2wh/4/
[5]:https://jsfiddle.net/MarkRocks/uunLd2wh/5/
