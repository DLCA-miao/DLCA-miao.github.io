---
title: "Ribo centre - Exploration"
layout: piclay
excerpt: "Ribo centre -- Exploration"
permalink: /exploration/
---
<script src='https://cdn.plot.ly/plotly-2.11.1.min.js'></script>

<div id='myDiv'><!-- Plotly chart will be drawn inside this DIV --></div>

<script>
var testData = await import ('{{ site.url }}{{ site.baseurl }}/assets/exploration/Fetal_all.json')
/* var testData = import ('/Users/chenxiaofeng/jekyll/RCA_web/assets/exploration/Fetal_all.json') */
Plotly.newPlot('myDiv', testData.cell, testData.layout, testData.config);

/* async function getLoadData(params, geneVal) { */
/*   let jsonDataModule1 = await import(`../../../mock/BCAWebJson/json/pie/${params['atlas']}_${params['region'].trim()}.json`);
  let jsonData = jsonDataModule1.default;
  await this.dealChartData(jsonData); */
/* } */



</script>
