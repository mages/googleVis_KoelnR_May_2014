googleVis overview and recent developments
========================================================
author: Markus Gesmann
date: KoelnR, 23 May 2014
font-family: 'Helvetica'
transition: linear
css: custom.css
width: 1440
height: 900

Agenda
========================================================
incremental: false
- A brief introduction to googleVis
- Recent developments
- How I created this presentation with RStudio
- Summary and outlook





What is googleVis?
========================================================

- Inspired by [Hans Rosling's talk](http://www.youtube.com/embed/hVimVzgtD6w) 
  we wanted to use interactive data visualisation tools to foster the 
  dialogue between data analysts and others
- The software behind Hans' talk was bought by Google and 
  integrated as motion charts into their Visualisation API
- Hence, we created [googleVis](http://gihub.com/mages/googleVis) 
  an R package and interface to the 
  [Google Chart Tools API](https://developers.google.com/chart/)
  - First version published in 2010
  
Introduction to Google Chart Tools
========================================================

* [Google Chart Tools](https://developers.google.com/chart/) 
  provide a way to visualize data on web sites
* The API makes it easy to create interactive charts
* It uses JavaScript and DataTable / JSON as input
* Output is either HTML5/SVG or Flash
* Browser with internet connection required to display chart
* Please read the Google [Terms of Service](https://developers.google.com/terms/) before you start

Structure of Google Charts
========================================================

The chart code has five generic parts:

1. References to Google's AJAX and Visualisation API
2. Data to visualize as a DataTable
3. Instance call to create the chart
4. Method call to draw the chart including options
5. HTML &lt;div&gt; element to add the chart to the page

Overview of googleVis
========================================================

* [googleVis](http://github.com/mages/googleVis) is a package for [R](http://www.r-poject.org/) and provides an interface between R and the [Google Chart Tools](https://developers.google.com/chart/)

* The functions of the package allow users to visualize data with the Google Chart Tools without uploading their data to Google

* The output of googleVis functions is html code that contains the data and references to JavaScript functions hosted by Google

* To view the output a browser with an internet connection is required, the actual chart is rendered in the browser; some charts require Flash

* See also: **Using the Google Visualisation API with R**, 
  [The R Journal, 3(2):40-44, December 2011](http://journal.r-project.org/archive/2011-2/RJournal_2011-2_Gesmann+de~Castillo.pdf) and googleVis [package vignette](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis.pdf)


googleVis version 0.5.2 provides interfaces to 
========================================================

* Flash based
  * Motion Charts, Annotated Time Lines, Geo Maps
* HMTL5/SVG based
  * Maps, Geo Charts and Intensity Maps,
  * Tables, Gauges, Tree Maps, Timelines,
  * Line-, Bar-, Column-, Area- and Combo Charts,
  * Scatter-, Bubble-, Candlestick-, Pie- and Org Charts,
  * Annotation-, Calendar-, Histogram and Sankey Charts
* Support for roles and trendlines
* Support for [Shiny](http://shiny.rstudio.com/) via [renderGvis](http://lamages.blogspot.co.uk/2013/02/first-steps-of-using-googlevis-on-shiny.html)

Run ```demo(googleVis)``` to see examples of all charts and read the [vignette](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis.pdf) for more details.

Motion chart example
========================================================


```r
plot(gvisMotionChart(Fruits, "Fruit", "Year",
                     options=list(width=600, height=400)))
```

<!-- MotionChart generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:08 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataMotionChartID64416b6c02de () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Apples",
2008,
"West",
98,
78,
20,
"2008-12-31" 
],
[
 "Apples",
2009,
"West",
111,
79,
32,
"2009-12-31" 
],
[
 "Apples",
2010,
"West",
89,
76,
13,
"2010-12-31" 
],
[
 "Oranges",
2008,
"East",
96,
81,
15,
"2008-12-31" 
],
[
 "Bananas",
2008,
"East",
85,
76,
9,
"2008-12-31" 
],
[
 "Oranges",
2009,
"East",
93,
80,
13,
"2009-12-31" 
],
[
 "Bananas",
2009,
"East",
94,
78,
16,
"2009-12-31" 
],
[
 "Oranges",
2010,
"East",
98,
91,
7,
"2010-12-31" 
],
[
 "Bananas",
2010,
"East",
81,
71,
10,
"2010-12-31" 
] 
];
data.addColumn('string','Fruit');
data.addColumn('number','Year');
data.addColumn('string','Location');
data.addColumn('number','Sales');
data.addColumn('number','Expenses');
data.addColumn('number','Profit');
data.addColumn('string','Date');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartMotionChartID64416b6c02de() {
var data = gvisDataMotionChartID64416b6c02de();
var options = {};
options["width"] =    600;
options["height"] =    400;

    var chart = new google.visualization.MotionChart(
    document.getElementById('MotionChartID64416b6c02de')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "motionchart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartMotionChartID64416b6c02de);
})();
function displayChartMotionChartID64416b6c02de() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartMotionChartID64416b6c02de"></script>
 
<!-- divChart -->
  
<div id="MotionChartID64416b6c02de"
  style="width: 600px; height: 400px;">
</div>



The googleVis concept
========================================================

* Charts: *'gvis' + ChartType*
* For a motion chart we have


```r
M <- gvisMotionChart(data, idvar='id', timevar='date', 
                     options=list(), chartid)
```


* Output of googleVis is a list of list

* Display the chart by simply plotting the output: ```plot(M)```
* Plot will generate a temporary html-file and open it in a new browser window 
* Specific parts can be extracted, e.g. 
  * the chart: ```M$html$chart``` or 
  * data: ```M$html$chart["jsData"]```


gvis-Chart structure
========================================================

List structure:

<img height=350 src="https://dl.dropbox.com/u/7586336/googleVisExamples/gvisObject.png" alt="gvis object structure" />


Example: Scatter chart
========================================================


```r
df <- data.frame(year=1:11, x=1:11)
plot(gvisScatterChart(df,options=list(width=600, height=400)))
```

<!-- ScatterChart generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:08 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartID64413073eb () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 1,
1 
],
[
 2,
2 
],
[
 3,
3 
],
[
 4,
4 
],
[
 5,
5 
],
[
 6,
6 
],
[
 7,
7 
],
[
 8,
8 
],
[
 9,
9 
],
[
 10,
10 
],
[
 11,
11 
] 
];
data.addColumn('number','year');
data.addColumn('number','x');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartID64413073eb() {
var data = gvisDataScatterChartID64413073eb();
var options = {};
options["allowHtml"] = true;
options["width"] =    600;
options["height"] =    400;

    var chart = new google.visualization.ScatterChart(
    document.getElementById('ScatterChartID64413073eb')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartID64413073eb);
})();
function displayChartScatterChartID64413073eb() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartID64413073eb"></script>
 
<!-- divChart -->
  
<div id="ScatterChartID64413073eb"
  style="width: 600px; height: 400px;">
</div>



Example: Line chart with options set
========================================================


```r
df <- data.frame(label=c("US", "GB", "BR"), val1=c(1,3,4), val2=c(23,12,32))
Line <- gvisLineChart(df, xvar="label", yvar=c("val1","val2"),
        options=list(title="Hello World", legend="bottom",
                titleTextStyle="{color:'red', fontSize:18}",                         
                vAxis="{gridlines:{color:'red', count:3}}",
                hAxis="{title:'My Label', titleTextStyle:{color:'blue'}}",
                series="[{color:'green', targetAxisIndex: 0}, 
                         {color: 'blue',targetAxisIndex:1}]",
                vAxes="[{title:'Value 1 (%)', format:'##,######%'}, 
                                  {title:'Value 2 (\U00A3)'}]",                          
                curveType="function", width=500, height=300                         
                ))
```

Options in googleVis have to follow the Google Chart API options


Line chart with options
========================================================


```r
plot(Line)
```

<!-- LineChart generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:08 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartID64416d0a4965 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
1,
23 
],
[
 "GB",
3,
12 
],
[
 "BR",
4,
32 
] 
];
data.addColumn('string','label');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartID64416d0a4965() {
var data = gvisDataLineChartID64416d0a4965();
var options = {};
options["allowHtml"] = true;
options["title"] = "Hello World";
options["legend"] = "bottom";
options["titleTextStyle"] = {color:'red', fontSize:18};
options["vAxis"] = {gridlines:{color:'red', count:3}};
options["hAxis"] = {title:'My Label', titleTextStyle:{color:'blue'}};
options["series"] = [{color:'green', targetAxisIndex: 0}, 
                         {color: 'blue',targetAxisIndex:1}];
options["vAxes"] = [{title:'Value 1 (%)', format:'##,######%'}, 
                                  {title:'Value 2 (£)'}];
options["curveType"] = "function";
options["width"] =    500;
options["height"] =    300;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartID64416d0a4965')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartID64416d0a4965);
})();
function displayChartLineChartID64416d0a4965() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartID64416d0a4965"></script>
 
<!-- divChart -->
  
<div id="LineChartID64416d0a4965"
  style="width: 500px; height: 300px;">
</div>



Example: Displaying geographical information
========================================================

Plot countries' S&P credit rating sourced from Wikipedia

```r
library(XML)
url <- "http://en.wikipedia.org/wiki/List_of_countries_by_credit_rating"
x <- readHTMLTable(readLines(url), which=3)
levels(x$Rating) <- substring(levels(x$Rating), 4, 
                            nchar(levels(x$Rating)))
x$Ranking <- x$Rating
levels(x$Ranking) <- nlevels(x$Rating):1
x$Ranking <- as.character(x$Ranking)
x$Rating <- paste(x$Country, x$Rating, sep=": ")
G <- gvisGeoChart(x, "Country", "Ranking", hovervar="Rating",
                options=list(gvis.editor="S&P",
                             projection="kavrayskiy-vii",
                             colorAxis="{colors:['#91BFDB', '#FC8D59']}"))
```



Chart countries' S&P credit rating
========================================================


```r
plot(G)
```

<!-- GeoChart generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:10 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartID64413e58bdd0 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Albania",
"Albania: 1",
6 
],
[
 "Angola",
"Angola: a3",
4 
],
[
 "Argentina",
"Argentina: 3",
8 
],
[
 "Armenia",
"Armenia: a2",
5 
],
[
 "Australia",
"Australia: aa",
1 
],
[
 "Austria",
"Austria: aa",
1 
],
[
 "Azerbaijan",
"Azerbaijan: aa3",
10 
],
[
 "Bahamas",
"Bahamas: 3",
8 
],
[
 "Bahrain",
"Bahrain: aa1",
9 
],
[
 "Bangladesh",
"Bangladesh: a3",
4 
],
[
 "Barbados",
"Barbados: aa3",
10 
],
[
 "Belarus",
"Belarus: 3",
8 
],
[
 "Belgium",
"Belgium: a3",
4 
],
[
 "Belize",
"Belize: 3",
8 
],
[
 "Bermuda",
"Bermuda: a2",
5 
],
[
 "Bolivia",
"Bolivia: a3",
4 
],
[
 "Bosnia and Herzegovina",
"Bosnia and Herzegovina: 3",
8 
],
[
 "Botswana",
"Botswana: 2",
7 
],
[
 "Brazil",
"Brazil: aa2",
2 
],
[
 "Bulgaria",
"Bulgaria: aa2",
2 
],
[
 "Cambodia",
"Cambodia: 2",
7 
],
[
 "Canada",
"Canada: aa",
1 
],
[
 "Cayman Islands",
"Cayman Islands: a3",
4 
],
[
 "Chile",
"Chile: a3",
4 
],
[
 "China",
"China: a3",
4 
],
[
 "Colombia",
"Colombia: aa3",
10 
],
[
 "Costa Rica",
"Costa Rica: aa3",
10 
],
[
 "Croatia",
"Croatia: aa3",
10 
],
[
 "Cuba",
"Cuba: aa1",
9 
],
[
 "Cyprus",
"Cyprus: aa3",
10 
],
[
 "Czech Republic",
"Czech Republic: 1",
6 
],
[
 "Denmark",
"Denmark: aa",
1 
],
[
 "Dominican Republic",
"Dominican Republic: 1",
6 
],
[
 "Ecuador",
"Ecuador: aa1",
9 
],
[
 "Egypt",
"Egypt: aa1",
9 
],
[
 "El Salvador",
"El Salvador: a2",
5 
],
[
 "Estonia",
"Estonia: 1",
6 
],
[
 "Fiji",
"Fiji: 1",
6 
],
[
 "Finland",
"Finland: aa",
1 
],
[
 "France",
"France: a1",
3 
],
[
 "Georgia",
"Georgia: a3",
4 
],
[
 "Germany",
"Germany: aa",
1 
],
[
 "Greece",
"Greece: aa3",
10 
],
[
 "Guatemala",
"Guatemala: a1",
3 
],
[
 "Honduras",
"Honduras: 2",
7 
],
[
 "Hong Kong",
"Hong Kong: a1",
3 
],
[
 "Hungary",
"Hungary: a1",
3 
],
[
 "Iceland",
"Iceland: aa3",
10 
],
[
 "India",
"India: aa3",
10 
],
[
 "Indonesia",
"Indonesia: aa3",
10 
],
[
 "Ireland",
"Ireland: aa1",
9 
],
[
 "Isle of Man",
"Isle of Man: aa",
1 
],
[
 "Israel",
"Israel: 1",
6 
],
[
 "Italy",
"Italy: aa2",
2 
],
[
 "Jamaica",
"Jamaica: 3",
8 
],
[
 "Japan",
"Japan: a3",
4 
],
[
 "Jordan",
"Jordan: a2",
5 
],
[
 "Kazakhstan",
"Kazakhstan: aa2",
2 
],
[
 "Kuwait",
"Kuwait: a2",
5 
],
[
 "Latvia",
"Latvia: aa2",
2 
],
[
 "Lebanon",
"Lebanon: 1",
6 
],
[
 "Lithuania",
"Lithuania: aa1",
9 
],
[
 "Luxembourg",
"Luxembourg: aa",
1 
],
[
 "Macao",
"Macao: a3",
4 
],
[
 "Malaysia",
"Malaysia: 3",
8 
],
[
 "Malta",
"Malta: 1",
6 
],
[
 "Mauritius",
"Mauritius: aa2",
2 
],
[
 "Mexico",
"Mexico: 3",
8 
],
[
 "Moldova",
"Moldova: 3",
8 
],
[
 "Mongolia",
"Mongolia: 1",
6 
],
[
 "Montenegro",
"Montenegro: a3",
4 
],
[
 "Morocco",
"Morocco: a1",
3 
],
[
 "Netherlands",
"Netherlands: aa",
1 
],
[
 "New Zealand",
"New Zealand: aa",
1 
],
[
 "Nicaragua",
"Nicaragua: 3",
8 
],
[
 "Norway",
"Norway: aa",
1 
],
[
 "Oman",
"Oman: 1",
6 
],
[
 "Pakistan",
"Pakistan: aa1",
9 
],
[
 "Panama",
"Panama: aa2",
2 
],
[
 "Papua New Guinea",
"Papua New Guinea: 1",
6 
],
[
 "Paraguay",
"Paraguay: 1",
6 
],
[
 "Peru",
"Peru: aa2",
2 
],
[
 "Philippines",
"Philippines: aa3",
10 
],
[
 "Poland",
"Poland: 2",
7 
],
[
 "Portugal",
"Portugal: a2",
5 
],
[
 "Qatar",
"Qatar: a2",
5 
],
[
 "Romania",
"Romania: aa3",
10 
],
[
 "Russia",
"Russia: aa1",
9 
],
[
 "Saudi Arabia",
"Saudi Arabia: a3",
4 
],
[
 "Senegal",
"Senegal: 1",
6 
],
[
 "Serbia",
"Serbia: 1",
6 
],
[
 "Singapore",
"Singapore: aa",
1 
],
[
 "Slovakia",
"Slovakia: 1",
6 
],
[
 "Slovenia",
"Slovenia: a1",
3 
],
[
 "South Africa",
"South Africa: aa1",
9 
],
[
 "South Korea",
"South Korea: a3",
4 
],
[
 "Spain",
"Spain: aa2",
2 
],
[
 "Sri Lanka",
"Sri Lanka: 1",
6 
],
[
 "St. Vincent & the Grenadines",
"St. Vincent & the Grenadines: 1",
6 
],
[
 "Suriname",
"Suriname: 1",
6 
],
[
 "Sweden",
"Sweden: aa",
1 
],
[
 "Switzerland",
"Switzerland: aa",
1 
],
[
 "Taiwan",
"Taiwan: a3",
4 
],
[
 "Thailand",
"Thailand: aa1",
9 
],
[
 "Trinidad and Tobago",
"Trinidad and Tobago: aa1",
9 
],
[
 "Tunisia",
"Tunisia: aa3",
10 
],
[
 "Turkey",
"Turkey: aa3",
10 
],
[
 "Ukraine",
"Ukraine: aa1",
9 
],
[
 "United Arab Emirates",
"United Arab Emirates: a2",
5 
],
[
 "United Kingdom",
"United Kingdom: a1",
3 
],
[
 "United States",
"United States: aa",
1 
],
[
 "Uruguay",
"Uruguay: aa3",
10 
],
[
 "Venezuela",
"Venezuela: 2",
7 
],
[
 "Vietnam",
"Vietnam: 1",
6 
] 
];
data.addColumn('string','Country');
data.addColumn('string','Rating');
data.addColumn('number','Ranking');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartGeoChartID64413e58bdd0() {
var data = gvisDataGeoChartID64413e58bdd0();
var options = {};
options["width"] =    556;
options["height"] =    347;
options["projection"] = "kavrayskiy-vii";
options["colorAxis"] = {colors:['#91BFDB', '#FC8D59']};

    chartGeoChartID64413e58bdd0 = new google.visualization.ChartWrapper({
    dataTable: data,       
    chartType: 'GeoChart',
    containerId: 'GeoChartID64413e58bdd0',
    options: options
    });
    chartGeoChartID64413e58bdd0.draw();
    

}

  function openEditorGeoChartID64413e58bdd0() {
  var editor = new google.visualization.ChartEditor();
  google.visualization.events.addListener(editor, 'ok',
  function() { 
  chartGeoChartID64413e58bdd0 = editor.getChartWrapper();  
  chartGeoChartID64413e58bdd0.draw(document.getElementById('GeoChartID64413e58bdd0')); 
  }); 
  editor.openDialog(chartGeoChartID64413e58bdd0);
  }
    
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "charteditor";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartGeoChartID64413e58bdd0);
})();
function displayChartGeoChartID64413e58bdd0() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartID64413e58bdd0"></script>
 
<!-- divChart -->
<input type='button' onclick='openEditorGeoChartID64413e58bdd0()' value='S&P'/>  
<div id="GeoChartID64413e58bdd0"
  style="width: 556px; height: 347px;">
</div>



New developments since googleVis 0.5.0
========================================================

* New functions gvisSankey, gvisAnnotationChart, gvisHistogram,
  gvisCalendar and gvisTimeline 
  
* New demos and vigenttes for trendlines and roles

* New [vignettes](http://cran.r-project.org/web/packages/googleVis/index.html) 
  written in R Markdown

* Dynamic help pages with [roxygen2](http://cran.r-project.org/web/packages/roxygen2/index.html)

* Moved code development from [Google Code](https://code.google.com/p/google-motion-charts-with-r/) with SVN to [GitHub](https://github.com/mages/googleVis) with git


Add additional columns to define roles - NEW
========================================================


```r
df <- data.frame(year=1:11, x=1:11,
                 x.scope=c(rep(TRUE, 8), rep(FALSE, 3)),
                 y=11:1, y.html.tooltip=LETTERS[11:1],                 
                 y.certainty=c(rep(TRUE, 5), rep(FALSE, 6)),
                 y.emphasis=c(rep(FALSE, 4), rep(TRUE, 7)))
plot(gvisScatterChart(df,options=list(lineWidth=2, width=600, height=400)))
```

<!-- ScatterChart generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:10 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartID64413415c2aa () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 1,
1,
true,
11,
"K",
true,
false 
],
[
 2,
2,
true,
10,
"J",
true,
false 
],
[
 3,
3,
true,
9,
"I",
true,
false 
],
[
 4,
4,
true,
8,
"H",
true,
false 
],
[
 5,
5,
true,
7,
"G",
true,
true 
],
[
 6,
6,
true,
6,
"F",
false,
true 
],
[
 7,
7,
true,
5,
"E",
false,
true 
],
[
 8,
8,
true,
4,
"D",
false,
true 
],
[
 9,
9,
false,
3,
"C",
false,
true 
],
[
 10,
10,
false,
2,
"B",
false,
true 
],
[
 11,
11,
false,
1,
"A",
false,
true 
] 
];
data.addColumn('number','year');
data.addColumn('number','x');
data.addColumn({type: 'boolean', role: 'scope'});
data.addColumn('number','y');
data.addColumn({type: 'string', role: 'tooltip', 'p': {'html': true}});
data.addColumn({type: 'boolean', role: 'certainty'});
data.addColumn({type: 'boolean', role: 'emphasis'});
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartID64413415c2aa() {
var data = gvisDataScatterChartID64413415c2aa();
var options = {};
options["allowHtml"] = true;
options["lineWidth"] =      2;
options["width"] =    600;
options["height"] =    400;

    var chart = new google.visualization.ScatterChart(
    document.getElementById('ScatterChartID64413415c2aa')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartID64413415c2aa);
})();
function displayChartScatterChartID64413415c2aa() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartID64413415c2aa"></script>
 
<!-- divChart -->
  
<div id="ScatterChartID64413415c2aa"
  style="width: 600px; height: 400px;">
</div>



Google Map - NEW individual markers
========================================================


```r
df <- data.frame(Adress=c("EC3M 7HA", "東京都新宿区北新宿2-21-1"),
                 Tip=c("Lloyd's", "Tokyo R User Group"))
plot(gvisMap(df, "Adress", "Tip",
              options=list(mapType='normal',
                icons="{'default': {'normal': 'http://icons.iconarchive.com/icons/icons-land/vista-map-markers/48/Map-Marker-Ball-Azure-icon.png',
                                               'selected': 'http://icons.iconarchive.com/icons/icons-land/vista-map-markers/48/Map-Marker-Ball-Right-Azure-icon.png'}
                                  }", width=800, height=250)))
```

<iframe src="https://dl.dropboxusercontent.com/u/7586336/blogger/MapTokyoRUserGroup.html" width=900 height=400 frameborder=0>Loading</iframe>


Timeline - NEW
========================================================


```r
dat <- data.frame(Room=c("Room 1","Room 2","Room 3"),
                  Language=c("Japanese", "English", "German"),
                  start=as.POSIXct(c("2014-04-17 14:00", 
                                     "2014-04-17 15:00",
                                     "2014-04-17 14:30")),
                  end=as.POSIXct(c("2014-04-17 15:00", 
                                   "2014-04-17 16:00",
                                   "2014-04-17 15:30")))
plot(gvisTimeline(data=dat, rowlabel="Room", barlabel="Language",
                  start="start", end="end", options=list(width=1000, height=250)))
```

<!-- Timeline generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:10 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTimelineID64419f419d () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Room 1",
"Japanese",
new Date(2014,3,17,14,0,0),
new Date(2014,3,17,15,0,0) 
],
[
 "Room 2",
"English",
new Date(2014,3,17,15,0,0),
new Date(2014,3,17,16,0,0) 
],
[
 "Room 3",
"German",
new Date(2014,3,17,14,30,0),
new Date(2014,3,17,15,30,0) 
] 
];
data.addColumn('string','Room');
data.addColumn('string','Language');
data.addColumn('datetime','start');
data.addColumn('datetime','end');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTimelineID64419f419d() {
var data = gvisDataTimelineID64419f419d();
var options = {};
options["width"] =   1000;
options["height"] =    250;

    var chart = new google.visualization.Timeline(
    document.getElementById('TimelineID64419f419d')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "timeline";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTimelineID64419f419d);
})();
function displayChartTimelineID64419f419d() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTimelineID64419f419d"></script>
 
<!-- divChart -->
  
<div id="TimelineID64419f419d"
  style="width: 1000px; height: 250px;">
</div>



Sankey chart - NEW
========================================================


```r
dat <- data.frame(From=c(rep("A",3), rep("B", 3)), 
                  To=c(rep(c("X", "Y", "Z"),2)),
                  Weight=c(5,7,6,2,9,4))
plot(gvisSankey(dat, from="From", to="To", weight="Weight",
                options=list(height=250)))
```

<!-- Sankey generated in R 3.1.0 by googleVis 0.5.2 package -->
<!-- Sun May 18 13:50:11 2014 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataSankeyID6441578caabc () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "A",
"X",
5 
],
[
 "A",
"Y",
7 
],
[
 "A",
"Z",
6 
],
[
 "B",
"X",
2 
],
[
 "B",
"Y",
9 
],
[
 "B",
"Z",
4 
] 
];
data.addColumn('string','From');
data.addColumn('string','To');
data.addColumn('number','Weight');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartSankeyID6441578caabc() {
var data = gvisDataSankeyID6441578caabc();
var options = {};
options["width"] =    400;
options["height"] =    250;

    var chart = new google.visualization.Sankey(
    document.getElementById('SankeyID6441578caabc')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "sankey";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartSankeyID6441578caabc);
})();
function displayChartSankeyID6441578caabc() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartSankeyID6441578caabc"></script>
 
<!-- divChart -->
  
<div id="SankeyID6441578caabc"
  style="width: 400px; height: 250px;">
</div>




Calendar chart - NEW
========================================================


```r
plot(gvisCalendar(Cairo, datevar="Date",
                  numvar="Temp",
                  options=list(calendar="{ cellSize: 10 }"))
```

<iframe src="https://dl.dropboxusercontent.com/u/7586336/blogger/CalendarCario.html" width=800 height=600 frameborder=0>Loading</iframe>


Annotation Chart - NEW
========================================================


```r
xtable(tail(Stock, 3))
```

<!-- html table generated in R 3.1.0 by xtable 1.7-3 package -->
<!-- Sun May 18 13:50:11 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Date </TH> <TH> Device </TH> <TH> Value </TH> <TH> Title </TH> <TH> Annotation </TH>  </TR>
  <TR> <TD align="right"> 10 </TD> <TD align="right"> 13882.00 </TD> <TD> Pens </TD> <TD align="right"> 14334.00 </TD> <TD> Out of stock </TD> <TD> Ran out of stock of pens at 4pm </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD align="right"> 13883.00 </TD> <TD> Pens </TD> <TD align="right"> 66467.00 </TD> <TD>  </TD> <TD>  </TD> </TR>
  <TR> <TD align="right"> 12 </TD> <TD align="right"> 13884.00 </TD> <TD> Pens </TD> <TD align="right"> 39463.00 </TD> <TD>  </TD> <TD>  </TD> </TR>
   </TABLE>

```r
A <- gvisAnnotationChart(
  Stock, datevar="Date",
  numvar="Value", idvar="Device",
  titlevar="Title", 
  annotationvar="Annotation",
  options=list(displayAnnotations=TRUE,
               legendPosition='newRow',
               fill=10, displayExactValues=TRUE,
               colors="['#0000ff','#00ff00']",
               width=600, height=300)
  )
```



Annotation Chart - NEW
========================================================


```r
plot(A, tag='chart')
```

<iframe src="https://dl.dropboxusercontent.com/u/7586336/blogger/AnnotationChart.html" frameborder="0" width="800" height="600">Loading</iframe>


Further reading and examples
========================================================

* [Demonstartion of googleVis](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis_examples.html)
* [Using the Google Chart Tools with R](http://cran.r-project.org/web/packages/googleVis/vignettes/googleVis.pdf)
* [Using Roles via googleVis](http://cran.r-project.org/web/packages/googleVis/vignettes/Using_Roles_via_googleVis.html)
* [Using Trendlines with googleVis](http://cran.r-project.org/web/packages/googleVis/vignettes/Using_Trendlines_with_googleVis.html)
* [Markdown example with knitr and googleVis](http://cran.r-project.org/web/packages/googleVis/vignettes/Using_googleVis_with_knitr.html)
* [My blog posts](http://lamages.blogspot.co.uk/search/label/googleVis)


How I created this presentation with RStudio
========================================================

* Simply started a new presentation file in RStudio and wrote markdown
* Customised the CSS file
* Ensured googleVis output is included as html, e.g.
<pre><code>{r setOptions, message=FALSE}
library(googleVis)
options(gvis.plot.tag="chart")
</code></pre>
* Used `results='asis'` to display googleVis `plot` statements
<pre><code>{r scatterchart, results="asis"}
plot(gvisScatterChart(women))
</code></pre>
* Note, Flash charts are only displayed when hosted on a web server, or the local 
  directory has been added as a [trusted folder in the Adobe settings](http://www.adobe.com/support/documentation/en/flashplayer/help/settings_manager04.html)

Summary and Outlook
========================================================
* The Google Chart Tools have developed into a powerful API
  * Data stays local, commercial use fine, see [Terms of Service](https://developers.google.com/chart/terms) for more details
* googleVis provides an interface to the Google Chart Tools API
  * Function's arguments and parameters follow the Google API
  * Move of googleVis code base to GitHub should encrouage further collaboration
* Alternative R packages are in development for interactive charts, e.g.
  * [rCharts](http://ramnathv.github.io/rCharts/)
  * [ggvis](http://ggvis.rstudio.com)
  * [Acinonyx aka iPlots eXtreme](http://rforge.net/Acinonyx/index.html)


The End. Questions? 
========================================================


Thanks
========================================================

* Google, who make the visualisation API available
* All the guys behind www.gapminder.org and Hans Rosling for telling
    everyone that data is not boring 
* Sebastian Perez Saaibi for his inspiring talk on 'Generator
    Tool for Google Motion Charts' at the R/RMETRICS conference 2010
* Henrik Bengtsson for providing the 'R.rsp: R Server Pages'
    package and his reviews and comments
* Duncan Temple Lang for providing the 'RJSONIO' package
* Deepayan Sarkar for showing us in the lattice package how to deal
    with lists of options  
* Paul Cleary for a bug report on the handling of months:
    Google date objects expect the months Jan.- Dec. as 0 - 11 and
    not 1 - 12.
* Ben Bolker for comments on plot.gvis and the usage of temporary
    files  



Thanks 
========================================================

* John Verzani for pointing out how to use the R http help server
* Cornelius Puschmann and Jeffrey Breen for highlighting a
    dependency issue with RJONSIO version 0.7-1
* Manoj Ananthapadmanabhan and Anand Ramalingam for providing
    ideas and code to animate a Google Geo Map
* Rahul Premraj for pointing out a rounding issue with Google Maps 
* Mike Silberbauer for an example showing how to shade the
    areas in annotated time line charts
* Tony Breyal for providing instructions on changing the Flash
    security settings to display Flash charts locally 
* Alexander Holcroft for reporting a bug in gvisMotionChart
    when displaying data with special characters in column names
* Pat Burns for pointing out typos in the vignette


Thanks
========================================================

* Jason Pickering for providing a patch to allow for quarterly 
    and weekly time dimensions to be displayed with gvisMotionChart
* Oliver Jay and Wai Tung Ho for reporting an issue with one-row 
    data sets
* Erik Bülow for pointing out how to load the Google API via a
    secure connection
* Sebastian Kranz for comments to enhance the argument list for
    gvisMotionChart to make it more user friendly 
* Sebastian Kranz and Wei Luo for providing ideas and code to
    improve the transformation of R data frames into JSON code
* Sebastian Kranz for reporting a bug in version 0.3.0
* Leonardo Trabuco for helping to clarify the usage of the
    argument state in the help file of gvisMotionChart
* Mark Melling for reporting an issue with jsDisplayChart and
    providing a solution


Thanks
========================================================

* Joe Cheng for code contribution to make googleVis work with shiny
* John Maindonald for reporting that the WorldBank demo didn't 
    download all data, but only the first 12000 records.
* Sebastian Campbell for reporting a typo in the Andrew and Stock
    data set and pointing out that the core charts, such as line
  charts accept also date variables for the x-axis. 
* John Maindonald for providing a simplified version of the
    WorldBank demo using the WDI package.
* John Muschelli for suggesting to add 'hovervar' as an additional
    argument to gvisGeoChart.
* Jacqueline Buros for providing code to include formats parameter 
    to gvisTable()
* JJ Allaire for pointing out how to use the viewer pane in RStudio
  o Oliver Gjoneski and Ashton Trey Belew for patches on roles and tooltips
* [Ramnath Vaidyanathan](https://github.com/ramnathv) for slidify.


Session Info
========================================================


```r
sessionInfo()
```

```
R version 3.1.0 (2014-04-10)
Platform: x86_64-apple-darwin13.1.0 (64-bit)

locale:
[1] en_GB.UTF-8/en_GB.UTF-8/en_GB.UTF-8/C/en_GB.UTF-8/en_GB.UTF-8

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] XML_3.98-1.1    xtable_1.7-3    googleVis_0.5.2 knitr_1.5      

loaded via a namespace (and not attached):
[1] evaluate_0.5.3 formatR_0.10   RJSONIO_1.0-3  stringr_0.6.2 
[5] tools_3.1.0   
```


