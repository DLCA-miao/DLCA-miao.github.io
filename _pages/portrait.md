---
title: "Developmental Lung Cell Atlas - Portrait"
layout: piclay
excerpt: "Developmental Lung Cell Atlas -- Portrait"
permalink: /portrait/
---
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

  .portrait-frame {
    width: 100%;
    overflow: hidden;
    border-radius: 10px;
    box-shadow: 0 0 2px grey;
  }

  .portrait-iframe {
    display: block;
    width: 100%;
    height: 900px;
    border: 0;
  }

  .portrait-table-wrap {
    width: 100%;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }

  @media (max-width: 767px) {
    .portrait-iframe {
      height: 560px;
    }

    .table-description {
      font-size: 14px;
      line-height: 1.6;
    }

    .portrait-table-wrap table {
      min-width: 640px;
    }
  }
</style>

<br>
<div class="portrait-frame">
  <iframe src="../dist/index.html" class="rounded-iframe portrait-iframe"></iframe>
</div>
<br>
<p class="table-description">The table shows the standardization of region naming across different publications.
</p>
<div class="portrait-table-wrap">
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Original Region</th>
      <th>Broad Region</th>
      <th>Region</th>
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
</div>
