---
title: "Developmental Lung Cell Atlas - Database"
layout: textlay
excerpt: " The Databases in Developmental Lung Cell Atlas, GZNL-RDC. "
sitemap: true
permalink: /database/
---
<html lang="en">
<head>
<!--set sort order in table header begin-->
<meta http-equiv="Content-type" content="text/html; charset=utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
  <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/jquery.dataTables.min.css">
  <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/2.2.3/css/buttons.dataTables.min.css">
<script type="text/javascript" src="https://code.jquery.com/jquery-3.5.1.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/dist/echarts.min.js"></script>
  <!--set sort order in table header finish-->
  <style>
    /* 页面主布局 */
    .page-container {
      display: flex;
      gap: 20px;
      margin-bottom: 30px;
    }
    
    /* 左侧筛选面板 */
    .filter-sidebar {
      width: 280px;
      flex-shrink: 0;
      background: #f8f9fa;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 20px;
      height: fit-content;
      max-height: calc(100vh - 200px);
      overflow-y: auto;
    }
    
    .filter-title {
      font-size: 18px;
      font-weight: bold;
      color: #333;
      margin-bottom: 20px;
      padding-bottom: 10px;
      border-bottom: 2px solid #00528e;
    }
    
    .filter-group {
      margin-bottom: 20px;
    }
    
    .filter-group-title {
      font-size: 14px;
      font-weight: bold;
      color: #00528e;
      margin-bottom: 10px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    
    .filter-group-title:hover {
      color: #7a98b5;
    }
    
    .filter-arrow {
      font-size: 12px;
      transition: transform 0.3s;
    }
    
    .filter-arrow.collapsed {
      transform: rotate(-90deg);
    }
    
    .filter-options {
      padding-left: 10px;
    }
    
    .filter-options.collapsed {
      display: none;
    }
    
    .filter-option {
      margin: 8px 0;
      display: flex;
      align-items: flex-start;
      gap: 8px;
    }
    
    .filter-option input[type="checkbox"] {
      margin: 2px 0 0 0;
      cursor: pointer;
      flex-shrink: 0;
    }
    
    .filter-option label {
      font-size: 13px;
      cursor: pointer;
      flex: 1;
      margin-bottom: 0;
      font-weight: normal;
      line-height: 1.4;
    }
    
    .filter-count {
      color: #999;
      font-size: 12px;
      margin-left: 5px;
    }
    
    .filter-actions {
      margin-bottom: 20px;
      padding-bottom: 15px;
      border-bottom: 1px solid #ddd;
    }
    
    .filter-btn {
      width: 100%;
      padding: 8px 16px;
      margin-bottom: 8px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 14px;
      transition: all 0.3s;
    }
    
    .filter-btn-reset {
      background-color: #e9ecef;
      color: #333;
    }
    
    .filter-btn-reset:hover {
      background-color: #ddd;
    }
    
    /* 右侧内容区域 */
    .content-area {
      flex: 1;
      min-width: 0;
    }
    
    /* 统计图表区域 */
    .charts-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      margin-bottom: 30px;
    }
    
    .chart-box {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    
    .chart-title {
      font-size: 16px;
      font-weight: bold;
      color: #333;
      margin-bottom: 15px;
      text-align: center;
    }
    
    .chart-content {
      width: 100%;
      height: 300px;
    }
    
    /* 搜索框样式 */
    .search-container {
      margin-bottom: 20px;
    }
    
    #searchBox {
      padding: 10px;
      font-size: 16px;
      border: 2px solid #ccc;
      border-radius: 4px;
      width: 100%;
      max-width: 400px;
    }
    
    #searchBox:focus {
      outline: none;
      border-color: #00528e;
    }
    
    /* 表格容器 */
    .table-container {
      width: 100%;
      overflow-x: auto;
    }
    
    /* 保持原有表格样式 */
    table {
      border: 2px solid #767676;
      border-radius: 5px;
      background-color: #fff;
      width: auto !important;
      table-layout: auto;
    }
    
    th {
      background-color: #00528e;
      color: rgba(255,255,255,0.9);
      cursor: pointer;
      white-space: nowrap;
      padding: 10px 28px 10px 10px;
      position: relative;
    }

    #cfttable thead th.sorting,
    #cfttable thead th.sorting_asc,
    #cfttable thead th.sorting_desc {
      background-image: none !important;
    }

    #cfttable thead th.sorting::before,
    #cfttable thead th.sorting::after,
    #cfttable thead th.sorting_asc::before,
    #cfttable thead th.sorting_asc::after,
    #cfttable thead th.sorting_desc::before,
    #cfttable thead th.sorting_desc::after {
      content: "";
      position: absolute;
      right: 10px;
      width: 0;
      height: 0;
      border-left: 4px solid transparent;
      border-right: 4px solid transparent;
      opacity: 0.38;
      transition: opacity 0.16s ease, border-color 0.16s ease;
    }

    #cfttable thead th.sorting::before,
    #cfttable thead th.sorting_asc::before,
    #cfttable thead th.sorting_desc::before {
      top: calc(50% - 7px);
      border-bottom: 5px solid #ffffff;
    }

    #cfttable thead th.sorting::after,
    #cfttable thead th.sorting_asc::after,
    #cfttable thead th.sorting_desc::after {
      top: calc(50% + 2px);
      border-top: 5px solid #ffffff;
    }

    #cfttable thead th.sorting:hover::before,
    #cfttable thead th.sorting:hover::after,
    #cfttable thead th.sorting_asc:hover::before,
    #cfttable thead th.sorting_asc:hover::after,
    #cfttable thead th.sorting_desc:hover::before,
    #cfttable thead th.sorting_desc:hover::after {
      opacity: 0.72;
    }

    #cfttable thead th.sorting_asc::before,
    #cfttable thead th.sorting_desc::after {
      opacity: 1;
    }
    
    td {
      background-color: #f9f9f9;
      padding: 10px;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 300px;
    }
    
    /* 表格行悬停效果 */
    #cfttable tbody tr {
      cursor: pointer;
      transition: background-color 0.2s;
    }
    
    #cfttable tbody tr:hover {
      background-color: #e3edf7 !important;
    }
    
    #cfttable tbody tr:hover td {
      background-color: #e3edf7 !important;
    }
    
    /* 抽屉样式 */
    .drawer-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 9998;
      display: none;
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    
    .drawer-overlay.active {
      display: block;
      opacity: 1;
    }
    
    .drawer {
      position: fixed;
      right: -600px;
      top: 0;
      width: 600px;
      height: 100%;
      background-color: #fff;
      box-shadow: -2px 0 8px rgba(0, 0, 0, 0.15);
      z-index: 9999;
      overflow-y: auto;
      transition: right 0.3s ease;
    }
    
    .drawer.active {
      right: 0;
    }
    
    .drawer-header {
      position: sticky;
      top: 0;
      background-color: #00528e;
      color: white;
      padding: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 10;
    }
    
    .drawer-title {
      color: white;
      font-size: 20px;
      font-weight: bold;
      margin: 0;
    }
    
    .drawer-close {
      background: none;
      border: none;
      color: white;
      font-size: 28px;
      cursor: pointer;
      padding: 0;
      width: 30px;
      height: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.2s;
    }
    
    .drawer-close:hover {
      transform: scale(1.2);
    }
    
    .drawer-content {
      padding: 30px;
    }
    
    .drawer-section {
      margin-bottom: 25px;
      padding-bottom: 20px;
      border-bottom: 1px solid #e0e0e0;
    }
    
    .drawer-section:last-child {
      border-bottom: none;
    }
    
    .drawer-section-title {
      font-size: 16px;
      font-weight: bold;
      color: #00528e;
      margin-bottom: 15px;
      display: flex;
      align-items: center;
    }
    
    .drawer-section-title::before {
      content: '';
      display: inline-block;
      width: 4px;
      height: 16px;
      background-color: #00528e;
      margin-right: 10px;
    }
    
    .drawer-field {
      margin-bottom: 15px;
    }
    
    .drawer-field-label {
      font-size: 13px;
      color: #666;
      margin-bottom: 5px;
      font-weight: 600;
    }
    
    .drawer-field-value {
      font-size: 14px;
      color: #333;
      line-height: 1.6;
      word-wrap: break-word;
    }
    
    .drawer-field-value a {
      color: #00528e;
      text-decoration: none;
      font-weight: 600;
    }
    
    .drawer-field-value a:hover {
      text-decoration: underline;
    }
    
    .drawer-tag {
      display: inline-block;
      background-color: #f0f0f0;
      padding: 4px 12px;
      border-radius: 12px;
      font-size: 13px;
      margin-right: 8px;
      margin-bottom: 8px;
    }
    
    .drawer-button {
      display: inline-block;
      padding: 10px 20px;
      background-color: #00528e;
      color: white;
      text-decoration: none;
      border-radius: 4px;
      font-size: 14px;
      font-weight: 600;
      transition: background-color 0.3s;
      border: none;
      cursor: pointer;
      margin-right: 10px;
      margin-top: 10px;
    }
    
    .drawer-button:hover {
      background-color: #7a98b5;
      color: white;
    }
    
    /* 物种切换按钮样式 */
    .species-filter-container {
      margin: 24px 0 30px;
      display: flex;
      gap: 15px;
      align-items: center;
    }
    
    .species-filter-label {
      font-size: 16px;
      font-weight: bold;
      color: #333;
    }
    
    .species-btn {
      padding: 10px 30px;
      border: 2px solid #00528e;
      background-color: #fff;
      color: #00528e;
      border-radius: 6px;
      cursor: pointer;
      font-size: 15px;
      font-weight: 600;
      transition: all 0.3s;
    }
    
    .species-btn:hover {
      background-color: #e3edf7;
    }
    
    .species-btn.active {
      background-color: #00528e;
      color: white;
    }

    @media (max-width: 991px) {
      .page-container {
        flex-direction: column;
      }

      .filter-sidebar {
        width: 100%;
        max-height: none;
      }

      .charts-container {
        grid-template-columns: 1fr;
      }

      .drawer {
        right: -100%;
        width: min(100%, 480px);
      }
    }

    @media (max-width: 767px) {
      .page-container {
        gap: 16px;
      }

      .filter-sidebar,
      .chart-box,
      .drawer-content {
        padding: 16px;
      }

      .chart-content {
        height: 240px;
      }

      .species-filter-container {
        margin: 24px 0 24px;
        flex-wrap: wrap;
        gap: 10px;
      }

      .species-filter-label {
        width: 100%;
      }

      .species-btn {
        flex: 1 1 calc(50% - 10px);
        min-width: 120px;
        padding: 10px 16px;
      }

      .drawer {
        width: 100%;
      }

      .drawer-header {
        padding: 16px;
      }

      .drawer-title {
        font-size: 18px;
      }

      .table-container {
        overflow-x: auto;
        -webkit-overflow-scrolling: touch;
      }

      table.dataTable th,
      table.dataTable td,
      th,
      td {
        white-space: nowrap;
      }

      div.dataTables_wrapper {
        width: 100%;
        overflow-x: auto;
      }

      .dt-buttons {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        margin-bottom: 12px;
      }

      .dataTables_filter,
      .dataTables_length {
        width: 100%;
        margin-bottom: 10px;
      }

      .dataTables_filter input {
        width: 100% !important;
        margin-left: 0 !important;
        margin-top: 8px;
      }
    }
  </style>
</head> 

<!-- 物种筛选按钮 -->
<div class="species-filter-container">
  <button class="species-btn active" onclick="filterBySpecies('all')">All</button>
  <button class="species-btn" onclick="filterBySpecies('human')">Human</button>
  <button class="species-btn" onclick="filterBySpecies('mouse')">Mouse</button>
</div>

<div class="page-container">
  <!-- 左侧筛选面板 -->
  <div class="filter-sidebar">
    <div class="filter-title">Filters</div>
    
    <div class="filter-actions">
      <button class="filter-btn filter-btn-reset" onclick="resetFilters()">Reset All</button>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('year')">
        Year
        <span class="filter-arrow" id="arrow-year">▼</span>
      </div>
      <div class="filter-options" id="filter-year"></div>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('seqtech')">
        Seq Tech
        <span class="filter-arrow" id="arrow-seqtech">▼</span>
      </div>
      <div class="filter-options" id="filter-seqtech"></div>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('seqmethod')">
        Seq Method
        <span class="filter-arrow" id="arrow-seqmethod">▼</span>
      </div>
      <div class="filter-options" id="filter-seqmethod"></div>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('region')">
        Region
        <span class="filter-arrow" id="arrow-region">▼</span>
      </div>
      <div class="filter-options" id="filter-region"></div>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('disease')">
        Disease
        <span class="filter-arrow" id="arrow-disease">▼</span>
      </div>
      <div class="filter-options" id="filter-disease"></div>
    </div>
    
    <div class="filter-group">
      <div class="filter-group-title" onclick="toggleFilterGroup('devstage')">
        Developmental Stage
        <span class="filter-arrow" id="arrow-devstage">▼</span>
      </div>
      <div class="filter-options" id="filter-devstage"></div>
    </div>
  </div>
  
  <!-- 右侧内容区域 -->
  <div class="content-area">
    <!-- 统计图表 -->
    <div class="charts-container">
      <div class="chart-box">
        <div class="chart-title">Year Distribution</div>
        <div class="chart-content" id="chart-year"></div>
      </div>
      
      <div class="chart-box">
        <div class="chart-title">Seq Method Distribution</div>
        <div class="chart-content" id="chart-seqmethod"></div>
      </div>
      
      <div class="chart-box">
        <div class="chart-title">Region Distribution</div>
        <div class="chart-content" id="chart-region"></div>
      </div>
      
      <div class="chart-box">
        <div class="chart-title">Disease Distribution</div>
        <div class="chart-content" id="chart-disease"></div>
      </div>
    </div>
    
    <!-- 搜索框 -->
    <div class="search-container">
      <p>You can use keywords to search.</p>
      <input type="text" id="searchBox" placeholder="Search by keyword..." oninput="searchTable()">
    </div>
    
    <!-- 表格 -->
    <div class="table-container">
      <p>You can download the tables by clicking on the buttons below the table. Click on any row to view details.</p>
<table id="cfttable" class="table table-hover table-bordered">
            <thead>
            <tr>
            <th onclick="sortTable(0)">DOI</th>
            <th onclick="sortTable(2)">Author</th>
            <th onclick="sortTable(3)">Journal</th>
            <th onclick="sortTable(4)">Year</th>
            <th onclick="sortTable(5)">Title</th>
            <th onclick="sortTable(7)">Accession code</th>
            <th onclick="sortTable(8)">Seq technology</th>
            <th onclick="sortTable(9)">Seq method</th>
            <th onclick="sortTable(10)">Species</th>
            <th onclick="sortTable(11)">Donor status</th>
            <th onclick="sortTable(12)">Organ</th>
            <th onclick="sortTable(13)">Region</th>
            <th onclick="sortTable(14)">Developmental stage</th>
            <th onclick="sortTable(15)">Cloud drive link</th>
          </tr>
            </thead>
    <tbody>
        {% for item in site.data.dataset_table   %}
           <tr data-year="{{item.Year}}" 
               data-seqtech="{{item['Seq technology']}}" 
               data-seqmethod="{{item['Seq method']}}" 
               data-region="{{item.Region}}" 
               data-disease="{{item['Donor status']}}" 
               data-disease-full="{{item.Disease}}"
               data-devstage="{{item['Developmental stage']}}"
               data-name="{{item.Name}}"
               data-title="{{item.Title}}"
               data-accession="{{item['Accession code']}}"
               data-doi="{{item['Article link']}}"
               data-doi-text="{{item.DOI}}"
               data-species="{{item['Species']}}"
               data-download="{{item['Download link']}}"
               data-cloud-link="{{item['Cloud drive link']}}"
               data-cellnumber="{{item['Cell number']}}"
               data-samplesize="{{item['Sample size']}}"
               data-age="{{item.Age}}"
               data-sex="{{item.Sex}}"
               data-ethnicity="{{item.Ethnicity}}"
               data-journal="{{item.Journal}}"
               data-pmid="{{item.PMID}}"
               onclick="openDrawer(this)">
              <td name="td0"><a href="{{item['Article link']}}" target="_blank" style="color:#00528e" onclick="event.stopPropagation();"><b>{{item["DOI"]}}</b></a></td>
              <td name="td2">{{item.Author}}</td>
              <td name="td3">{{item.Journal}}</td>
              <td name="td4">{{item.Year}}</td>
              <td name="td5">{{item.Title}}</td>
              <td name="td7"><a href="{{item['Download link']}}" target="_blank" style="color:#00528e" onclick="event.stopPropagation();"><b>{{item["Accession code"]}}</b></a></td>
              <td name="td8">{{item['Seq technology']}}</td>
              <td name="td9">{{item['Seq method']}}</td>
              <td name="td10">{{item['Species']}}</td>
              <td name="td11">{{item['Donor status']}}</td>
              <td name="td12">{{item.Organ}}</td>
              <td name="td13">{{item.Region}}</td>
              <td name="td14">{{item['Developmental stage']}}</td>
              <td name="td15"><a href="{{item['Cloud drive link']}}" target="_blank" style="color:#00528e" onclick="event.stopPropagation();"><b>Link</b></a></td>
            </tr>
        {% endfor %}
       
       </tbody>
    </table>
      </div>
    </div>
</div>

<!-- 抽屉组件 -->
<div class="drawer-overlay" id="drawerOverlay" onclick="closeDrawer()"></div>
<div class="drawer" id="drawer">
  <div class="drawer-header">
    <h2 class="drawer-title">Dataset Details</h2>
    <button class="drawer-close" onclick="closeDrawer()">&times;</button>
  </div>
  <div class="drawer-content" id="drawerContent">
    <!-- 内容将通过JavaScript动态填充 -->
  </div>
</div>                
<script>
  var dataTable;
  var allData = [];
  var fullDataset = {{ site.data.dataset_table | jsonify }};  // 从Jekyll获取完整数据集
  var filteredData = [];
  var currentSpecies = 'all';  // 当前选择的物种: 'all', 'human', 'mouse'
  var selectedFilters = {
    year: [],
    seqtech: [],
    seqmethod: [],
    region: [],
    disease: [],
    devstage: []
  };
  
  // 导出时去除 HTML，使用 data 属性中的纯文本/URL
  // 表格列索引: 0=DOI, 1=Author, 2=Journal,3=Year, 4=Title, 5=Accession, 6=Seq tech,
  //             7=Seq method, 8=Species, 9=Donor status, 10=Organ, 11=Region,
  //             12=Dev stage, 13=Cloud link
  function formatExportCell(data, row, column, node) {
    var $tr = $(node).closest('tr');
    if (column === 0) {
      return $tr.attr('data-doi-text') || $(node).text().trim() || data;
    }
    if (column === 4) {
      return $tr.attr('data-title') || $(node).text().trim() || data;
    }
    if (column === 5) {
      return $tr.attr('data-accession') || $(node).text().trim() || data;
    }
    if (column === 13) {
      return $tr.attr('data-cloud-link') || $(node).find('a').attr('href') || data;
    }
    if (typeof data === 'string' && data.indexOf('<') !== -1) {
      return $('<div>').html(data).text().trim();
    }
    return data;
  }

  function addDownloadLinksToExport(exportData) {
    var exportedRows = dataTable.rows({
      search: 'applied',
      order: 'applied',
      page: 'all'
    }).nodes().toArray();

    exportData.header.splice(5, 0, 'Accession code link');
    exportData.body.forEach(function(row, index) {
      var downloadUrl = $(exportedRows[index]).attr('data-download') || '';
      row.splice(5, 0, downloadUrl);
    });
  }

  var exportFormatOptions = {
    format: {
      body: formatExportCell
    },
    modifier: {
      page: 'all'
    },
    customizeData: addDownloadLinksToExport
  };

  $(document).ready(function() {
    $.noConflict();
    
    // 初始化DataTable
    dataTable = $('#cfttable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        { extend: 'copy', exportOptions: exportFormatOptions },
        {
          extend: 'csvHtml5',
          exportOptions: exportFormatOptions,
          bom: true,
          charset: 'utf-8'
        },
        { extend: 'excelHtml5', exportOptions: exportFormatOptions },
        {
          extend: 'pdfHtml5',
          orientation: 'landscape',
          pageSize: 'A2',
          title: 'Developmental Lung Cell Atlas - Database',
          exportOptions: exportFormatOptions,
          customize: function(doc) {
            doc.defaultStyle.fontSize = 6;
            doc.styles.tableHeader.fontSize = 7;
            doc.pageMargins = [8, 24, 8, 12];
          }
        },
        { extend: 'print', exportOptions: exportFormatOptions }
      ],
      autoWidth: true,
      scrollX: true,
      orderFixed: {
        pre: [[6, 'asc']]
      },
      infoCallback: function(settings, start, end, max, total, pre) {
        // 自定义info显示，移除"(filtered from X total entries)"部分
        if (max === total) {
          return 'Showing ' + start + ' to ' + end + ' of ' + total + ' entries';
        } else {
          return 'Showing ' + start + ' to ' + end + ' of ' + total + ' entries';
        }
      }
    });
    
    // 隐藏DataTables默认搜索框
    $('#cfttable_filter').css('display', 'none');
    
    // 收集所有数据
    collectAllData();
    
    // 初始化筛选器（基于完整数据集）
    initializeFilters();
    
    // 初始化图表（基于完整数据集）
    updateCharts();
    
    // 检查URL参数中是否有search参数
    var urlParams = new URLSearchParams(window.location.search);
    var searchParam = urlParams.get('search');
    if (searchParam) {
      // 将搜索关键词填入搜索框
      $('#searchBox').val(searchParam);
      // 触发搜索
      searchTable();
    }
  });
  
  // 收集表格中的所有数据
  function collectAllData() {
    $('#cfttable tbody tr').each(function() {
      var row = $(this);
      allData.push({
        year: row.attr('data-year'),
        seqtech: row.attr('data-seqtech'),
        seqmethod: row.attr('data-seqmethod'),
        region: row.attr('data-region'),
        disease: row.attr('data-disease'),
        devstage: row.attr('data-devstage'),
        element: row
      });
    });
    filteredData = [...allData];
  }
  
  // 初始化筛选器选项（基于完整数据集）
  function initializeFilters() {
    var filterData = {
      year: {},
      seqtech: {},
      seqmethod: {},
      region: {},
      disease: {},
      devstage: {}
    };
    
    // 使用完整数据集进行统计（Seq Tech 使用原始完整值，组合项如 10X,Cite-seq 单独计数）
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var year = item.Year || '';
      var seqtech = item['Seq technology'] || '';
      var seqmethod = item['Seq method'] || '';
      var region = item.Region || '';
      var disease = item['Donor status'] || '';
      var devstage = item['Developmental stage'] || '';
      
      filterData.year[year] = (filterData.year[year] || 0) + 1;
      
      if (seqtech) {
        filterData.seqtech[seqtech] = (filterData.seqtech[seqtech] || 0) + 1;
      }
      
      // 直接使用原始值统计
      if (seqmethod) {
        filterData.seqmethod[seqmethod] = (filterData.seqmethod[seqmethod] || 0) + 1;
      }
      
      // 直接使用原始值统计
      if (region) {
        filterData.region[region] = (filterData.region[region] || 0) + 1;
      }
      
      // 直接使用原始值统计
      if (disease) {
        filterData.disease[disease] = (filterData.disease[disease] || 0) + 1;
      }
      
      filterData.devstage[devstage] = (filterData.devstage[devstage] || 0) + 1;
    });
    
    // 生成筛选器HTML
    createFilterOptions('year', filterData.year);
    createFilterOptions('seqtech', filterData.seqtech);
    createFilterOptions('seqmethod', filterData.seqmethod);
    createFilterOptions('region', filterData.region);
    createFilterOptions('disease', filterData.disease);
    createFilterOptions('devstage', filterData.devstage);
  }
  
  // 根据当前选择的物种过滤数据集
  function getFilteredDatasetBySpecies() {
    if (currentSpecies === 'all') {
      return fullDataset;
    } else if (currentSpecies === 'human') {
      return fullDataset.filter(function(item) {
        return item.Species === 'Homo sapiens';
      });
    } else if (currentSpecies === 'mouse') {
      return fullDataset.filter(function(item) {
        return item.Species === 'Mus musculus';
      });
    }
    return fullDataset;
  }
  
  // 创建筛选器选项
  function createFilterOptions(filterType, data) {
    var container = $('#filter-' + filterType);
    var sortedKeys = Object.keys(data).sort();
    
    sortedKeys.forEach(function(key) {
      if (key && key !== 'undefined' && key !== 'null') {
        var count = data[key];
        var safeKey = key.replace(/[^a-zA-Z0-9]/g, '-');
        var html = '<div class="filter-option">' +
                   '<input type="checkbox" id="' + filterType + '-' + safeKey + 
                   '" value="' + key.replace(/'/g, "\\'") + '" onchange="updateFilterSelection(\'' + 
                   filterType + '\', this.value, this.checked)">' +
                   '<label for="' + filterType + '-' + safeKey + '">' + 
                   key + '<span class="filter-count">(' + count + ')</span></label>' +
                   '</div>';
        container.append(html);
      }
    });
  }
  
  // 更新筛选选择（勾选后立即应用筛选）
  function updateFilterSelection(filterType, value, checked) {
    var index = selectedFilters[filterType].indexOf(value);
    if (checked && index === -1) {
      selectedFilters[filterType].push(value);
    } else if (!checked && index > -1) {
      selectedFilters[filterType].splice(index, 1);
    }
    
    // 立即应用筛选（会同时更新图表和统计值）
    applyFilters();
  }
  
  // 应用筛选
  function applyFilters() {
    // 更新表格显示
    updateTableDisplay();
    
    // 更新图表和筛选项统计（基于筛选和搜索后的数据）
    updateChartsAfterSearch();
    updateFilterCountsAfterSearch();
  }

  function splitMultiValue(value) {
    if (!value) {
      return [];
    }

    return value.split(',').map(function(part) {
      return part.trim();
    }).filter(function(part) {
      return part && part !== 'undefined' && part !== 'null';
    });
  }

  function matchesMultiValueFilter(rowValue, selectedValues) {
    if (!rowValue) {
      return false;
    }

    if (selectedValues.includes(rowValue)) {
      return true;
    }

    var normalizedValues = splitMultiValue(rowValue);

    return selectedValues.some(function(selectedValue) {
      return normalizedValues.includes(selectedValue);
    });
  }
  
  // 更新表格显示
  function updateTableDisplay() {
    // 清除之前的自定义搜索
    $.fn.dataTable.ext.search = [];
    
    // 添加自定义搜索函数
    $.fn.dataTable.ext.search.push(
      function(settings, data, dataIndex, rowData, counter) {
        // 获取当前行的DOM元素
        var $row = $(dataTable.row(dataIndex).node());
        
        // 首先检查物种筛选
        if (currentSpecies !== 'all') {
          var rowSpecies = $row.attr('data-species');
          if (currentSpecies === 'human' && rowSpecies !== 'Homo sapiens') {
            return false;
          }
          if (currentSpecies === 'mouse' && rowSpecies !== 'Mus musculus') {
            return false;
          }
        }
        
        // 检查Year
        if (selectedFilters.year.length > 0) {
          var rowYear = $row.attr('data-year');
          if (!selectedFilters.year.includes(rowYear)) {
            return false;
          }
        }
        
        // 检查Seq Tech（精确匹配完整值，10X,Cite-seq 与 10X 为不同选项）
        if (selectedFilters.seqtech.length > 0) {
          var rowSeqtech = $row.attr('data-seqtech');
          if (!selectedFilters.seqtech.includes(rowSeqtech)) {
            return false;
          }
        }
        
        // 检查Seq Method（可能包含逗号分隔的多个值）
        if (selectedFilters.seqmethod.length > 0) {
          var rowSeqmethod = $row.attr('data-seqmethod');
          if (!selectedFilters.seqmethod.includes(rowSeqmethod)) {
            return false;
          }
        }
        
        // 检查Region（可能包含逗号分隔的多个值）
        if (selectedFilters.region.length > 0) {
          var rowRegion = $row.attr('data-region');
          if (!matchesMultiValueFilter(rowRegion, selectedFilters.region)) {
            return false;
          }
        }
        
        // 检查Disease（可能包含逗号分隔的多个值）
        if (selectedFilters.disease.length > 0) {
          var rowDisease = $row.attr('data-disease');
          if (!matchesMultiValueFilter(rowDisease, selectedFilters.disease)) {
            return false;
          }
        }
        
        // 检查Developmental Stage
        if (selectedFilters.devstage.length > 0) {
          var rowDevstage = $row.attr('data-devstage');
          if (!selectedFilters.devstage.includes(rowDevstage)) {
            return false;
          }
        }
        
        return true;
      }
    );
    
    // 重新绘制表格（保留搜索框的搜索内容）
    dataTable.draw();
  }
  
  // 重置筛选
  function resetFilters() {
    selectedFilters = {
      year: [],
      seqtech: [],
      seqmethod: [],
      region: [],
      disease: [],
      devstage: []
    };
    
    $('input[type="checkbox"]').prop('checked', false);
    
    // 清除搜索框
    $('#searchBox').val('');
    
    // 清除自定义搜索并重新绘制表格
    $.fn.dataTable.ext.search = [];
    dataTable.search('').draw();
    
    // 重置图表（显示全部数据）
    updateCharts();
    
    // 重置筛选器统计值为初始值
    resetFilterCounts();
  }
  
  // 切换筛选组显示
  function toggleFilterGroup(groupName) {
    var options = $('#filter-' + groupName);
    var arrow = $('#arrow-' + groupName);
    
    options.toggleClass('collapsed');
    arrow.toggleClass('collapsed');
  }
  
  // 搜索功能
  function searchTable() {
    var keyword = $('#searchBox').val();
    dataTable.search(keyword).draw();
    
    // 搜索后更新筛选器统计值和图表
    updateFilterCountsAfterSearch();
    updateChartsAfterSearch();
  }
  
  // 文本截断辅助函数（添加省略号）
  function truncateText(text, maxLength) {
    if (!text) return '';
    if (text.length <= maxLength) return text;
    return text.substring(0, maxLength) + '...';
  }

  function getDiseaseLabels(item) {
    var shortLabel = item['Donor status'] || item['Disease'] || '';
    var fullLabel = item['Disease'] || shortLabel;
    return {
      shortLabel: shortLabel,
      fullLabel: fullLabel
    };
  }

  function buildDiseaseChartData(dataset) {
    var diseaseData = {};
    dataset.forEach(function(item) {
      var labels = getDiseaseLabels(item);
      if (!labels.shortLabel) {
        return;
      }

      if (!diseaseData[labels.shortLabel]) {
        diseaseData[labels.shortLabel] = {
          name: labels.shortLabel,
          fullName: labels.fullLabel,
          value: 0
        };
      }

      diseaseData[labels.shortLabel].value += 1;
    });

    return Object.keys(diseaseData).map(function(key) {
      return diseaseData[key];
    }).sort(function(a, b) {
      return b.value - a.value;
    }).slice(0, 15);
  }
  
  // 更新图表（基于全表数据）
  function updateCharts() {
    updateYearChart();
    updateSeqMethodChart();
    updateRegionChart();
    updateDiseaseChart();
  }
  
  // Year 饼图（基于完整数据集）
  function updateYearChart() {
    var yearData = {};
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var year = item.Year || '';
      if (year) {
        yearData[year] = (yearData[year] || 0) + 1;
      }
    });
    
    var chartData = Object.keys(yearData).map(function(key) {
      return {name: key, value: yearData[key]};
    }).sort(function(a, b) {
      return a.name - b.name;
    });
    
    var chart = echarts.init(document.getElementById('chart-year'));
    var option = {
      tooltip: {
        trigger: 'item',
        formatter: '{b}: {c} ({d}%)'
      },
      legend: {
        orient: 'vertical',
        right: 10,
        top: 'center',
        type: 'scroll'
      },
      series: [{
        type: 'pie',
        radius: '60%',
        center: ['40%', '50%'],
        data: chartData,
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }]
    };
    chart.setOption(option);
  }
  
  // Seq Method 饼图（基于完整数据集，直接使用原始值）
  function updateSeqMethodChart() {
    var methodData = {};
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var method = item['Seq method'] || '';
      if (method) {
        // 直接使用原始值统计
        methodData[method] = (methodData[method] || 0) + 1;
      }
    });
    
    var chartData = Object.keys(methodData).map(function(key) {
      return {name: key, value: methodData[key]};
    });
    
    var chart = echarts.init(document.getElementById('chart-seqmethod'));
    var option = {
      tooltip: {
        trigger: 'item',
        formatter: '{b}: {c} ({d}%)'
      },
      legend: {
        orient: 'vertical',
        right: 10,
        top: 'center',
        type: 'scroll'
      },
      series: [{
        type: 'pie',
        radius: '60%',
        center: ['40%', '50%'],
        data: chartData,
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }]
    };
    chart.setOption(option);
  }
  
  // Region 柱状图（基于完整数据集，直接使用原始值）
  function updateRegionChart() {
    var regionData = {};
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var region = item.Region || '';
      if (region) {
        // 直接使用原始值统计
        regionData[region] = (regionData[region] || 0) + 1;
      }
    });
    
    var sortedData = Object.keys(regionData).map(function(key) {
      return {name: key, value: regionData[key]};
    }).sort(function(a, b) {
      return b.value - a.value;
    }).slice(0, 15);
    
    var chart = echarts.init(document.getElementById('chart-region'));
    var option = {
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'shadow'
        }
      },
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'category',
        data: sortedData.map(function(d) { return d.name; }),
        axisLabel: {
          rotate: 45,
          interval: 0,
          fontSize: 10,
          formatter: function(value) {
            return truncateText(value, 15);
          }
        }
      },
      yAxis: {
        type: 'value'
      },
      series: [{
        type: 'bar',
        data: sortedData.map(function(d) { return d.value; }),
        itemStyle: {
          color: '#00528e'
        }
      }]
    };
    chart.setOption(option);
  }
  
  // Disease 柱状图（基于完整数据集，直接使用原始值）
  function updateDiseaseChart() {
    var diseaseData = {};
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var disease = item['Donor status']|| '';
      if (disease) {
        // 直接使用原始值统计
        diseaseData[disease] = (diseaseData[disease] || 0) + 1;
      }
    });
    
    var sortedData = buildDiseaseChartData(datasetToUse);
    
    var chart = echarts.init(document.getElementById('chart-disease'));
    var option = {
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'shadow'
        },
        formatter: function(params) {
          if (!params.length) return '';
          var data = params[0].data || {};
          return (data.fullName || params[0].name) + ': ' + params[0].value;
        }
      },
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'category',
        data: sortedData.map(function(d) { return d.name; }),
        axisLabel: {
          rotate: 45,
          interval: 0,
          fontSize: 10,
          formatter: function(value) {
            return truncateText(value, 15);
          }
        }
      },
      yAxis: {
        type: 'value'
      },
      series: [{
        type: 'bar',
        data: sortedData.map(function(d) {
          return {
            value: d.value,
            fullName: d.fullName
          };
        }),
        itemStyle: {
          color: '#4472C4'
        }
      }]
    };
    chart.setOption(option);
  }
  
  function sortTable(columnIndex) {
    // DataTables handles sorting
  }
  
  // 打开抽屉并显示详情
  function openDrawer(row) {
    var data = {
      name: row.getAttribute('data-name'),
      year: row.getAttribute('data-year'),
      title: row.getAttribute('data-title'),
      accession: row.getAttribute('data-accession'),
      doi: row.getAttribute('data-doi'),
      species: row.getAttribute('data-species'),
      seqtech: row.getAttribute('data-seqtech'),
      seqmethod: row.getAttribute('data-seqmethod'),
      region: row.getAttribute('data-region'),
      disease: row.getAttribute('data-disease'),
      devstage: row.getAttribute('data-devstage'),
      cellnumber: row.getAttribute('data-cellnumber'),
      samplesize: row.getAttribute('data-samplesize'),
      age: row.getAttribute('data-age'),
      sex: row.getAttribute('data-sex'),
      ethnicity: row.getAttribute('data-ethnicity'),
      journal: row.getAttribute('data-journal'),
      pmid: row.getAttribute('data-pmid'),
      download: row.getAttribute('data-download')
    };
    
    // 构建抽屉内容
    var content = '';
    
    // 基本信息
    content += '<div class="drawer-section">';
    content += '<div class="drawer-section-title">Basic Information</div>';
    
    if (data.name) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Author</div>';
      content += '<div class="drawer-field-value">' + data.name + ' <i>et al.</i></div>';
      content += '</div>';
    }
    
    if (data.year) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Year</div>';
      content += '<div class="drawer-field-value">' + data.year + '</div>';
      content += '</div>';
    }
    
    if (data.title) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Title</div>';
      content += '<div class="drawer-field-value">' + data.title + '</div>';
      content += '</div>';
    }
    
    if (data.journal) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Journal</div>';
      content += '<div class="drawer-field-value">' + data.journal + '</div>';
      content += '</div>';
    }
    
    content += '</div>';
    
    // 数据访问
    content += '<div class="drawer-section">';
    content += '<div class="drawer-section-title">Data Access</div>';
    
    if (data.accession) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Accession Code</div>';
      content += '<div class="drawer-field-value">' + data.accession + '</div>';
      content += '</div>';
    }
    
    if (data.pmid) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">PMID</div>';
      content += '<div class="drawer-field-value">' + data.pmid + '</div>';
      content += '</div>';
    }
    
    if (data.doi) {
      content += '<a href="' + data.doi + '" target="_blank" class="drawer-button">View Publication</a>';
    }
    
    content += '</div>';
    
    // 技术信息
    content += '<div class="drawer-section">';
    content += '<div class="drawer-section-title">Technical Information</div>';
    
    if (data.seqtech) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Sequencing Technology</div>';
      content += '<div class="drawer-field-value">';
      var seqtechs = data.seqtech.split(',').map(function(s) { return s.trim(); });
      seqtechs.forEach(function(tech) {
        content += '<span class="drawer-tag">' + tech + '</span>';
      });
      content += '</div></div>';
    }
    
    if (data.seqmethod) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Sequencing Method</div>';
      content += '<div class="drawer-field-value">';
      var seqmethods = data.seqmethod.split(',').map(function(s) { return s.trim(); });
      seqmethods.forEach(function(method) {
        content += '<span class="drawer-tag">' + method + '</span>';
      });
      content += '</div></div>';
    }
    
    if (data.cellnumber) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Cell Number</div>';
      content += '<div class="drawer-field-value">' + data.cellnumber + '</div>';
      content += '</div>';
    }
    
    content += '</div>';
    
    // 样本信息
    content += '<div class="drawer-section">';
    content += '<div class="drawer-section-title">Sample Information</div>';
    
    if (data.species) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Species</div>';
      content += '<div class="drawer-field-value">' + data.species + '</div>';
      content += '</div>';
    }
    
    if (data.region) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Region</div>';
      content += '<div class="drawer-field-value">';
      var regions = data.region.split(',').map(function(r) { return r.trim(); });
      regions.forEach(function(region) {
        content += '<span class="drawer-tag">' + region + '</span>';
      });
      content += '</div></div>';
    }
    
    if (data.disease) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Disease / Donor Status</div>';
      content += '<div class="drawer-field-value">';
      var diseases = data.disease.split(',').map(function(d) { return d.trim(); });
      diseases.forEach(function(disease) {
        content += '<span class="drawer-tag">' + disease + '</span>';
      });
      content += '</div></div>';
    }
    
    if (data.devstage) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Developmental Stage</div>';
      content += '<div class="drawer-field-value">' + data.devstage + '</div>';
      content += '</div>';
    }
    
    if (data.samplesize) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Sample Size</div>';
      content += '<div class="drawer-field-value">' + data.samplesize + '</div>';
      content += '</div>';
    }
    
    if (data.age) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Age</div>';
      content += '<div class="drawer-field-value">' + data.age + '</div>';
      content += '</div>';
    }
    
    if (data.sex) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Sex</div>';
      content += '<div class="drawer-field-value">' + data.sex + '</div>';
      content += '</div>';
    }
    
    if (data.ethnicity) {
      content += '<div class="drawer-field">';
      content += '<div class="drawer-field-label">Ethnicity</div>';
      content += '<div class="drawer-field-value">' + data.ethnicity + '</div>';
      content += '</div>';
    }
    
    content += '</div>';
    
    // 填充内容并显示抽屉
    document.getElementById('drawerContent').innerHTML = content;
    document.getElementById('drawer').classList.add('active');
    document.getElementById('drawerOverlay').classList.add('active');
    
    // 防止body滚动
    document.body.style.overflow = 'hidden';
  }
  
  // 关闭抽屉
  function closeDrawer() {
    document.getElementById('drawer').classList.remove('active');
    document.getElementById('drawerOverlay').classList.remove('active');
    
    // 恢复body滚动
    document.body.style.overflow = '';
  }
  
  // ESC键关闭抽屉
  document.addEventListener('keydown', function(event) {
    if (event.key === 'Escape') {
      closeDrawer();
    }
  });
  
  // 更新单个筛选组的统计值
  function updateFilterGroupCounts(filterType, data) {
    $('#filter-' + filterType + ' .filter-option').each(function() {
      var $option = $(this);
      var $checkbox = $option.find('input[type="checkbox"]');
      var value = $checkbox.val();
      var $label = $option.find('label');
      var $count = $label.find('.filter-count');
      
      // 获取新的统计值
      var newCount = data[value] || 0;
      
      // 更新显示的统计值
      $count.text('(' + newCount + ')');
      
      // 如果统计值为0且未被选中，可以选择性地添加灰色样式
      if (newCount === 0 && !$checkbox.prop('checked')) {
        $option.css('opacity', '0.5');
      } else {
        $option.css('opacity', '1');
      }
    });
  }
  
  // 重置筛选器统计值为初始值（基于完整数据集）
  function resetFilterCounts() {
    var filterData = {
      year: {},
      seqtech: {},
      seqmethod: {},
      region: {},
      disease: {},
      devstage: {}
    };
    
    var datasetToUse = getFilteredDatasetBySpecies();
    datasetToUse.forEach(function(item) {
      var year = item.Year || '';
      var seqtech = item['Seq technology'] || '';
      var seqmethod = item['Seq method'] || '';
      var region = item.Region || '';
      var disease = item['Donor status']|| '';
      var devstage = item['Developmental stage'] || '';
      
      filterData.year[year] = (filterData.year[year] || 0) + 1;
      
      if (seqtech) {
        filterData.seqtech[seqtech] = (filterData.seqtech[seqtech] || 0) + 1;
      }
      
      if (seqmethod) {
        filterData.seqmethod[seqmethod] = (filterData.seqmethod[seqmethod] || 0) + 1;
      }
      
      if (region) {
        filterData.region[region] = (filterData.region[region] || 0) + 1;
      }
      
      if (disease) {
        filterData.disease[disease] = (filterData.disease[disease] || 0) + 1;
      }
      
      filterData.devstage[devstage] = (filterData.devstage[devstage] || 0) + 1;
    });
    
    // 重置每个筛选器的统计值
    updateFilterGroupCounts('year', filterData.year);
    updateFilterGroupCounts('seqtech', filterData.seqtech);
    updateFilterGroupCounts('seqmethod', filterData.seqmethod);
    updateFilterGroupCounts('region', filterData.region);
    updateFilterGroupCounts('disease', filterData.disease);
    updateFilterGroupCounts('devstage', filterData.devstage);
    
    // 移除所有灰色样式
    $('.filter-option').css('opacity', '1');
  }
  
  // 获取当前表格中可见的行数据（考虑搜索和筛选）
  function getVisibleRowsData() {
    var visibleData = [];
    dataTable.rows({ search: 'applied' }).every(function() {
      var $row = $(this.node());
      var rowData = {
        'Year': $row.attr('data-year'),
        'Seq technology': $row.attr('data-seqtech'),
        'Seq method': $row.attr('data-seqmethod'),
        'Region': $row.attr('data-region'),
        'Donor status': $row.attr('data-disease'),
        'Disease': $row.attr('data-disease-full'),
        'Developmental stage': $row.attr('data-devstage')
      };
      visibleData.push(rowData);
    });
    return visibleData;
  }
  
  // 搜索后更新筛选器统计值
  function updateFilterCountsAfterSearch() {
    var visibleData = getVisibleRowsData();
    
    var filterData = {
      year: {},
      seqtech: {},
      seqmethod: {},
      region: {},
      disease: {},
      devstage: {}
    };
    
    visibleData.forEach(function(item) {
      var year = item['Year'] || '';
      var seqtech = item['Seq technology'] || '';
      var seqmethod = item['Seq method'] || '';
      var region = item['Region'] || '';
      var disease = item['Donor status'] || item['Disease'] || '';
      var devstage = item['Developmental stage'] || '';
      
      filterData.year[year] = (filterData.year[year] || 0) + 1;
      
      if (seqtech) {
        filterData.seqtech[seqtech] = (filterData.seqtech[seqtech] || 0) + 1;
      }
      
      if (seqmethod) {
        filterData.seqmethod[seqmethod] = (filterData.seqmethod[seqmethod] || 0) + 1;
      }
      
      if (region) {
        filterData.region[region] = (filterData.region[region] || 0) + 1;
      }
      
      if (disease) {
        filterData.disease[disease] = (filterData.disease[disease] || 0) + 1;
      }
      
      filterData.devstage[devstage] = (filterData.devstage[devstage] || 0) + 1;
    });
    
    // 更新每个筛选器的统计值
    updateFilterGroupCounts('year', filterData.year);
    updateFilterGroupCounts('seqtech', filterData.seqtech);
    updateFilterGroupCounts('seqmethod', filterData.seqmethod);
    updateFilterGroupCounts('region', filterData.region);
    updateFilterGroupCounts('disease', filterData.disease);
    updateFilterGroupCounts('devstage', filterData.devstage);
  }
  
  // 搜索后更新图表
  function updateChartsAfterSearch() {
    var visibleData = getVisibleRowsData();
    
    // Year Chart
    var yearData = {};
    visibleData.forEach(function(item) {
      var year = item['Year'] || '';
      if (year) {
        yearData[year] = (yearData[year] || 0) + 1;
      }
    });
    
    var yearChartData = Object.keys(yearData).map(function(key) {
      return {name: key, value: yearData[key]};
    }).sort(function(a, b) {
      return a.name - b.name;
    });
    
    var yearChart = echarts.init(document.getElementById('chart-year'));
    yearChart.setOption({
      tooltip: {
        trigger: 'item',
        formatter: '{b}: {c} ({d}%)'
      },
      legend: {
        orient: 'vertical',
        right: 10,
        top: 'center',
        type: 'scroll'
      },
      series: [{
        type: 'pie',
        radius: '60%',
        center: ['40%', '50%'],
        data: yearChartData,
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }]
    });
    
    // Seq Method Chart
    var methodData = {};
    visibleData.forEach(function(item) {
      var method = item['Seq method'] || '';
      if (method) {
        methodData[method] = (methodData[method] || 0) + 1;
      }
    });
    
    var methodChartData = Object.keys(methodData).map(function(key) {
      return {name: key, value: methodData[key]};
    });
    
    var methodChart = echarts.init(document.getElementById('chart-seqmethod'));
    methodChart.setOption({
      tooltip: {
        trigger: 'item',
        formatter: '{b}: {c} ({d}%)'
      },
      legend: {
        orient: 'vertical',
        right: 10,
        top: 'center',
        type: 'scroll'
      },
      series: [{
        type: 'pie',
        radius: '60%',
        center: ['40%', '50%'],
        data: methodChartData,
        emphasis: {
          itemStyle: {
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          }
        }
      }]
    });
    
    // Region Chart
    var regionData = {};
    visibleData.forEach(function(item) {
      var region = item['Region'] || '';
      if (region) {
        regionData[region] = (regionData[region] || 0) + 1;
      }
    });
    
    var regionSortedData = Object.keys(regionData).map(function(key) {
      return {name: key, value: regionData[key]};
    }).sort(function(a, b) {
      return b.value - a.value;
    }).slice(0, 15);
    
    var regionChart = echarts.init(document.getElementById('chart-region'));
    regionChart.setOption({
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'shadow'
        }
      },
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'category',
        data: regionSortedData.map(function(d) { return d.name; }),
        axisLabel: {
          rotate: 45,
          interval: 0,
          fontSize: 10,
          formatter: function(value) {
            return truncateText(value, 15);
          }
        }
      },
      yAxis: {
        type: 'value'
      },
      series: [{
        type: 'bar',
        data: regionSortedData.map(function(d) { return d.value; }),
        itemStyle: {
          color: '#00528e'
        }
      }]
    });
    
    // Disease Chart
    var diseaseData = {};
    visibleData.forEach(function(item) {
      var disease = item['Donor status'] || item['Disease'] || '';
      if (disease) {
        diseaseData[disease] = (diseaseData[disease] || 0) + 1;
      }
    });
    
    var diseaseSortedData = buildDiseaseChartData(visibleData);
    
    var diseaseChart = echarts.init(document.getElementById('chart-disease'));
    diseaseChart.setOption({
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'shadow'
        },
        formatter: function(params) {
          if (!params.length) return '';
          var data = params[0].data || {};
          return (data.fullName || params[0].name) + ': ' + params[0].value;
        }
      },
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'category',
        data: diseaseSortedData.map(function(d) { return d.name; }),
        axisLabel: {
          rotate: 45,
          interval: 0,
          fontSize: 10,
          formatter: function(value) {
            return truncateText(value, 15);
          }
        }
      },
      yAxis: {
        type: 'value'
      },
      series: [{
        type: 'bar',
        data: diseaseSortedData.map(function(d) {
          return {
            value: d.value,
            fullName: d.fullName
          };
        }),
        itemStyle: {
          color: '#4472C4'
        }
      }]
    });
  }
  
  // 物种筛选功能
  function filterBySpecies(species) {
    // 更新当前物种选择
    currentSpecies = species;
    
    // 更新按钮状态
    $('.species-btn').removeClass('active');
    event.target.classList.add('active');
    
    // 清空所有筛选条件
    selectedFilters = {
      year: [],
      seqtech: [],
      seqmethod: [],
      region: [],
      disease: [],
      devstage: []
    };
    
    // 清空所有复选框
    $('input[type="checkbox"]').prop('checked', false);
    
    // 清空搜索框
    $('#searchBox').val('');
    
    // 清空左侧筛选器内容
    $('#filter-year').empty();
    $('#filter-seqtech').empty();
    $('#filter-seqmethod').empty();
    $('#filter-region').empty();
    $('#filter-disease').empty();
    $('#filter-devstage').empty();
    
    // 重新初始化筛选器（基于新的物种数据）
    initializeFilters();
    
    // 更新表格显示
    updateTableDisplay();
    
    // 更新图表（基于新的物种数据）
    updateCharts();
  }
  </script> 
       
