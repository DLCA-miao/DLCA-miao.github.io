---
title: "Developmental Lung Cell Atlas - Portrait"
layout: piclay
excerpt: "Developmental Lung Cell Atlas -- Portrait"
permalink: /portrait/
---
<!-- <meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width,initial-scale=1">
<script defer="defer" src="../dist/js/chunk-vendors.7a6e8a2d.js"></script>
<script defer="defer" src="../dist/js/app.3b0bc1fc.js"></script>
<link href="../css/app.2e1a2c1f.css" rel="stylesheet">
<noscript><strong>We're sorry but rca_web doesn't work properly without JavaScript enabled. Please enable it to continue.</strong></noscript>
<div id="app"></div> -->

<!-- 
<meta charset="utf-8"><meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width,initial-scale=1">
<script defer="defer" src="../dist/js/chunk-vendors.7a6e8a2d.js"></script>
<script defer="defer" src="../dist/js/app.fd9671bb.js"></script>
<link href="../dist/css/app.2e1a2c1f.css" rel="stylesheet">
<noscript><strong>We're sorry but rca_web doesn't work properly without JavaScript enabled. Please enable it to continue.</strong></noscript>
<div id="app"></div> -->
<!-- <p style="color:#00528e; font-size:20px;">Clicking on different regions will lead to the <b>Data Viewer</b> page to display the characteristics of the cells in that region.</p> -->
<style>
  .table-custom {
    font-size: 0.9rem; /* 调整字体大小 */
    width: 300px; /* 调整表格宽度 */
    height:100px
  }
  
  /* 表格表头样式 */
  .table thead th {
    background-color: #00528e;
    color: rgba(255,255,255,0.9);
    white-space: nowrap;
    padding: 10px;
  }
</style>
<br>
<iframe src="../dist/index.html" class="rounded-iframe" width="100%" height="900" frameborder="0"></iframe>
<br>
<p class="table-description">The table shows the standardization of region naming across different publications.
</p>
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Concrete Region</th>
      <th>Broad Region</th>
      <th>Anatomical Region</th>
    </tr>
  </thead>
  <tbody>
    {% for region in site.data.portrait_regions %}
    <tr>
     <td>{{ region.concrete_region }}</td>
      <td>{{ region.broad_region }}</td>
      <td>{{ region.anatomical_region }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
