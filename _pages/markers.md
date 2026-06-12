---
title: "Developmental Lung Cell Atlas - Markers"
layout: homelay
excerpt: "Developmental Lung Cell Atlas -- Markers"
permalink: /markers/
---
<html>
<head>
	<meta http-equiv="Content-type" content="text/html; charset=utf-8">
	<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
	<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/jquery.dataTables.min.css">
	<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/2.2.3/css/buttons.dataTables.min.css">
</head>
<body>
  <script type="text/javascript"  src="https://code.jquery.com/jquery-3.5.1.js"></script>
	<script type="text/javascript"  src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
	<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
	<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
	<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
	<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
	<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
	<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>

    <style>
		th {
        background-color: #00528e;
        background-color: #00528e;
        background-color: #00528e;
        color: rgba(255,255,255,0.9);
		    cursor: pointer;
        }
	</style>

<!-- <p class="text-center" style="color:#00528e; font-size:20px; "> (This page shows the differentially expressed genes (DEGs) according to the regions/cell types)</p> -->
<!-- <div class="container">
<p><b>Step1</b> Click below to select a target dataset for analysis.</p>
<div class="row" style="display: flex; justify-content: space-between;">
<div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Adult',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/adult-brain.png" class="rounded-circle" />
</div> -->
<!-- <div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #00528e;">
ADULT BRAIN
</b>
</p>
</div> -->
<!-- </div> -->

<!-- <div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Fetal',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/fetal-brain.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #00528e;">
FETAL BRAIN
</b>
</p>
</div> -->
<!-- </div> -->


<!-- <div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Tumour',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/tumour-brain.png" class="rounded-circle" />
</div> -->
<!-- <div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #00528e;">
TUMOR
</b>
</p>
</div> -->
<!-- </div> -->

<!-- <div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Organoid',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/drganoid-brain.png" class="rounded-circle" />
</div> -->
<!-- <div> -->
<!-- <p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #00528e;">
ORGANOID
</b>
</p>
</div> -->
<!-- </div>
</div>
</div> -->
<div class="markers-description container markers-panel">
The section shows the differentially expressed genes (DEGs) of the target region or the target Cell type.
</div>
<br/>
<div class="container markers-panel">
<p><b>Step1</b> Click the buttons to show the differentially expressed genes (DEGs) of the target region or the target Cell type.</p>
  <div class="markers-button-row">
    <button id="buttonA" onclick="changeOrder('A')">By Region</button>
    <button id="buttonB" onclick="changeOrder('B')">By Cell type</button>
  </div>
</div>
  <br/>

<div class="container markers-panel">
<p><b>Step2</b> Select the target Cell type/Region to show the DEGs.</p>
  <p id="sentence"></p>
  
  <!-- Region Selection Cards -->
  <div id="regionSelectionContainer" class="selection-container">
    <div class="selection-label-row">
      <p class="selection-label">Select Region:</p>
      <button type="button" id="allRegionButton" class="all-region-button" onclick="selectAllRegion()">All</button>
    </div>
    <div id="regionCards" class="card-grid"></div>
  </div>
  
  <!-- Cell Type Selection Cards -->
  <div id="cellTypeSelectionContainer" class="selection-container">
    <div class="selection-label-row">
      <p class="selection-label">Select Cell Type:</p>
      <button type="button" id="allCellTypeButton" class="all-region-button" onclick="selectAllCellType()" style="display: none;">All</button>
    </div>
    <div id="cellTypeCards" class="card-grid-celltype"></div>
  </div>
  
  <button type="button" class="btn btn-primary btn-sm" style="text-transform: capitalize;" onclick="showResults();">Markers</button>
</div>
<br/>
<div id="contentContainer" style="display: none;">
<!-- Volcano Plot Section -->
<div class="container markers-panel">
<div class="result-selection-bar" id="volcanoSelectionSummary" style="display: none;">
  <span class="selection-summary-title">Search by</span>
  <span class="selection-summary-item">Region :</span>
  <span class="selection-pill" id="selectedRegionPillTop"></span>
  <span class="selection-summary-item">Cell type :</span>
  <span class="selection-pill" id="selectedCellTypePillTop"></span>
</div>
<div class="image-container">
<b>Result</b> Volcano Plot.
<!-- Volcano Plot Loading Indicator -->
<div id="volcanoLoadingIndicator" style="display: none; text-align: center; padding: 20px;">
  <div class="spinner"></div>
  <p>Loading volcano plot...</p>
</div>
<img id="selectedImage" src="" alt="Selected Image" style="display: none;">
</div>
</div>
<br/>
<!-- Table Section -->
<div class="container markers-panel">
<div class="result-selection-bar" id="tableSelectionSummary" style="display: none;">
  <span class="selection-summary-title">Search by</span>
  <span class="selection-summary-item">Region :</span>
  <span class="selection-pill" id="selectedRegionPillBottom"></span>
  <span class="selection-summary-item">Cell type :</span>
  <span class="selection-pill" id="selectedCellTypePillBottom"></span>
</div>
<b>Result</b> The table of DEGs.
<!-- Table Loading Indicator -->
<div id="tableLoadingIndicator" style="display: none; text-align: center; padding: 20px;">
  <div class="spinner"></div>
  <p>Loading table data...</p>
</div>
<div id="csvTableContainer" style="overflow-x: auto; box-shadow: 0 0 2px;"></div>
</div>
</div>
<div class="container markers-panel">
<p id="clickMessageContainer" style="display: block;">Please click on the <b>Markers</b> button above.</p>
</div>


<style>
    .custom-column {
        margin: 0 50px; /* 设置列之间的间距 */
    }
</style>
<style>
  #csvTableContainer {
    overflow-x: auto;
  }

  /* 将表格头部固定 */
  #csvTableContainer thead {
    position: static;
  }
</style>







<style>
   /* 设置固定宽度 */
  #selectBox1, #selectBox2 {
    width: 400px; /* 这里可以根据需要调整宽度 */
    height: 38px
  }
  .active {
    background-color: #00528e; 
    color: white;
  }
  .image-container {
    max-width: 100%;
    max-height: 100%;
    background-color: none;
    justify-content: center;
    align-items: center;
    box-shadow: none;
  }
  
  .image-container img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
  
  /* Card Selection Styles */
  .selection-container {
    margin: 20px 0;
  }
  
  .selection-label {
    font-weight: bold;
    margin-bottom: 10px;
    font-size: 16px;
  }

  .selection-label-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 10px;
  }

  .selection-label-row .selection-label {
    margin-bottom: 0;
  }

  .all-region-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 56px;
    height: 32px;
    padding: 0 14px;
    border: 1px solid #d8e6f5;
    border-radius: 999px;
    background: #ffffff;
    color: #00528e;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .all-region-button.is-selected {
    background: #00528e;
    border-color: #00528e;
    color: #ffffff;
    box-shadow: 0 4px 12px rgba(0, 82, 142, 0.18);
  }

  .markers-button-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .result-selection-bar {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 8px;
    margin-bottom: 16px;
    color: #4d5f75;
    font-size: 14px;
  }

  .selection-summary-title {
    color: #00528e;
    font-weight: 700;
  }

  .selection-summary-item {
    color: #5f6f82;
  }

  .selection-pill {
    display: inline-flex;
    align-items: center;
    min-height: 28px;
    padding: 4px 12px;
    border: 1px solid #d8e6f5;
    border-radius: 999px;
    background: #eef5fc;
    color: #4d6f92;
    font-size: 13px;
    line-height: 1.2;
  }

  #csvTableContainer .column-filters input {
    width: 100%;
    min-width: 90px;
    padding: 4px 6px;
    border: 1px solid #d5dce6;
    border-radius: 4px;
    font-size: 12px;
    box-sizing: border-box;
    color: #1f2d3d;
    background-color: #ffffff;
    caret-color: #1f2d3d;
    opacity: 1;
  }

  #csvTableContainer .column-filters input::placeholder {
    color: #7a8796;
    opacity: 1;
  }

  #csvTableContainer .column-filters th.markers-text-filter-cell {
    vertical-align: middle;
    text-align: center;
  }

  #csvTableContainer .column-filters th.markers-text-filter-cell input {
    display: inline-block;
    width: auto;
    min-width: 90px;
    max-width: 100%;
    margin: 0 auto;
  }

  #csvTableContainer .column-filters th.markers-numeric-filter-cell {
    vertical-align: middle;
    text-align: center;
    padding: 6px 4px;
  }

  #csvTableContainer .markers-numeric-filter {
    position: relative;
    display: inline-flex;
    flex-direction: column;
    align-items: stretch;
    gap: 5px;
    width: fit-content;
    margin: 0 auto;
    padding: 2px 18px 2px 2px;
  }

  #csvTableContainer .markers-numeric-filter-row {
    display: inline-flex;
    align-items: stretch;
    overflow: hidden;
    border: 1px solid #c8d6e6;
    border-radius: 6px;
    background: #ffffff;
    box-shadow: 0 1px 2px rgba(15, 35, 60, 0.06);
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  #csvTableContainer .markers-numeric-filter.is-active .markers-numeric-filter-row.is-bound-active {
    border-color: #7eb0d8;
    box-shadow: 0 0 0 2px rgba(126, 176, 216, 0.18);
  }

  #csvTableContainer .markers-numeric-filter select,
  #csvTableContainer .markers-numeric-filter input {
    height: 26px;
    margin: 0;
    border: none;
    border-radius: 0;
    font-size: 12px;
    color: #1f2d3d;
    background: #ffffff;
    box-sizing: border-box;
  }

  #csvTableContainer .markers-numeric-filter select {
    width: 46px;
    flex: 0 0 46px;
    padding: 0 2px;
    border-right: 1px solid #e4ebf3;
    cursor: pointer;
    text-align: center;
    color: #00528e;
    font-weight: 600;
    background: #f8fbfe;
  }

  #csvTableContainer .markers-numeric-filter input {
    flex: 0 0 68px;
    width: 68px;
    min-width: 68px;
    max-width: 68px;
    padding: 0 8px;
    text-align: center;
  }

  #csvTableContainer .markers-numeric-filter input::placeholder {
    color: #9aa8b8;
    font-size: 11px;
  }

  #csvTableContainer .markers-numeric-filter-clear {
    position: absolute;
    top: 0;
    right: 0;
    width: 16px;
    height: 16px;
    padding: 0;
    border: none;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.92);
    color: #6b7c90;
    font-size: 12px;
    line-height: 16px;
    text-align: center;
    cursor: pointer;
    box-shadow: 0 1px 2px rgba(15, 35, 60, 0.12);
    visibility: hidden;
  }

  #csvTableContainer .markers-numeric-filter.is-active .markers-numeric-filter-clear {
    visibility: visible;
  }

  #csvTableContainer .markers-numeric-filter-clear:hover {
    background: #ffffff;
    color: #00528e;
  }

  #csvTableContainer .dt-buttons {
    margin-bottom: 8px;
  }

  #csvTableContainer .dt-button {
    padding: 4px 10px;
    border-radius: 4px;
  }

  .table-progress {
    margin: 8px 0 12px;
    color: #5f6f82;
    font-size: 13px;
  }

  #csvTableContainer .markers-table-toolbar,
  #csvTableContainer .markers-table-footer {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 12px;
    margin: 10px 0;
  }

  #csvTableContainer .markers-table-footer {
    justify-content: space-between;
  }

  #csvTableContainer .dataTables_paginate,
  #csvTableContainer .dataTables_info,
  #csvTableContainer .dataTables_length,
  #csvTableContainer .dataTables_filter {
    display: block !important;
  }

  #csvTableContainer .dataTables_paginate {
    margin-left: auto;
  }

  .markers-custom-toolbar,
  .markers-custom-footer {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 12px;
    margin: 10px 0;
  }

  .markers-custom-footer {
    justify-content: space-between;
  }

  .markers-download-link,
  .markers-page-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 36px;
    height: 32px;
    padding: 0 10px;
    border: 1px solid #d5dce6;
    border-radius: 4px;
    background: #fff;
    color: #00528e;
    text-decoration: none;
    cursor: pointer;
  }

  .markers-page-btn.is-active {
    background: #00528e;
    border-color: #00528e;
    color: #fff;
  }

  .markers-page-btn[disabled] {
    cursor: not-allowed;
    opacity: 0.5;
  }

  .markers-page-size {
    height: 32px;
    padding: 0 8px;
    border: 1px solid #d5dce6;
    border-radius: 4px;
    background: #fff;
  }

  .markers-sortable {
    cursor: pointer;
    position: relative;
    padding-right: 28px !important;
    user-select: none;
  }

  .markers-sortable::before,
  .markers-sortable::after {
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

  .markers-sortable::before {
    top: calc(50% - 7px);
    border-bottom: 5px solid #ffffff;
  }

  .markers-sortable::after {
    top: calc(50% + 2px);
    border-top: 5px solid #ffffff;
  }

  .markers-sortable:hover::before,
  .markers-sortable:hover::after {
    opacity: 0.72;
  }

  .markers-sortable.sort-asc::before,
  .markers-sortable.sort-desc::after {
    opacity: 1;
  }
  
  .card-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-bottom: 20px;
    max-height: 400px;
    overflow-y: auto;
    overflow-x: hidden;
    padding: 10px;
    border: 1px solid #e0e0e0;
    border-radius: 8px;
  }
  
  /* 自定义滚动条样式 - region */
  .card-grid::-webkit-scrollbar {
    width: 8px;
  }
  
  .card-grid::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 4px;
  }
  
  .card-grid::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 4px;
  }
  
  .card-grid::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
  
  .region-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
    border: 2px solid #ddd;
    border-radius: 10px;
    background-color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    width: 140px;
    text-align: center;
  }
  
  .region-card:hover {
    border-color: #00528e;
    background-color: #f5f5f5;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  
  .region-card.selected {
    border-color: #00528e;
    background-color: #00528e;
    color: white;
  }
  
  .region-card .region-name {
    font-size: 12px;
    line-height: 1.3;
    word-wrap: break-word;
  }
  
  .card-grid-celltype {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-bottom: 20px;
    max-height: 400px;
    overflow-y: auto;
    overflow-x: hidden;
    padding: 10px;
    border: 1px solid #e0e0e0;
    border-radius: 8px;
  }
  
  /* 自定义滚动条样式 */
  .card-grid-celltype::-webkit-scrollbar {
    width: 8px;
  }
  
  .card-grid-celltype::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 4px;
  }
  
  .card-grid-celltype::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 4px;
  }
  
  .card-grid-celltype::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
  
  .celltype-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
    border: 2px solid #ddd;
    border-radius: 10px;
    background-color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    width: 140px;
    text-align: center;
  }
  
  .celltype-card:hover {
    border-color: #00528e;
    background-color: #f5f5f5;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  
  .celltype-card.selected {
    border-color: #00528e;
    background-color: #00528e;
    color: white;
  }
  
  .celltype-card img {
    width: 60px;
    height: 60px;
    margin-bottom: 10px;
    object-fit: contain;
  }
  
  .celltype-card .celltype-name {
    font-size: 12px;
    line-height: 1.3;
    word-wrap: break-word;
  }
  
  /* Loading Spinner */
  .spinner {
    border: 4px solid #f3f3f3;
    border-top: 4px solid #00528e;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
    margin: 0 auto;
  }
  
  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }

  @media (max-width: 767px) {
    .markers-panel {
      padding: 12px;
    }

    .markers-description {
      font-size: 14px;
      line-height: 1.6;
    }

    .markers-button-row {
      flex-direction: column;
    }

    #buttonA, #buttonB {
      width: 100%;
      max-width: none;
    }

    .selection-label {
      font-size: 15px;
    }

    .result-selection-bar {
      gap: 6px;
      font-size: 13px;
    }

    .selection-pill {
      max-width: 100%;
      word-break: break-word;
    }

    .card-grid,
    .card-grid-celltype {
      gap: 10px;
      max-height: 320px;
      padding: 8px;
    }

    .region-card,
    .celltype-card {
      width: calc(50% - 5px);
      min-height: 110px;
      padding: 12px 8px;
    }

    .celltype-card img {
      width: 44px;
      height: 44px;
    }

    #csvTableContainer {
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
    }

    #csvTableContainer table {
      min-width: 720px;
    }
  }
</style>
<script type="text/javascript"  src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>
<script>
  var regionOptions = [];
  var cellTypeOptions = [];
  var selectedRegion = null;
  var selectedCellType = null;
  var selectedOptions = [];
  var imageLoaded = false; // 添加图片加载状态变量
  var selectedButton = 'A'; // 添加选中按钮状态变量
  var originalOrder = true; // 添加顺序状态变量
  
  var latestImageRequestId = 0;
  var latestTableRequestId = 0;
  var latestResolvedTableUrl = '';
  var markersTableState = null;

  document.addEventListener('DOMContentLoaded', function() {
    loadInitialData();
  });
  
  function loadInitialData() {
    // 加载 RegionDEG.json
    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/RegionDEG.json')
      .then(response => response.json())
      .then(data => {
        // 假设我们只关心第一个键的值
        var firstKey = Object.keys(data)[0];
        <!-- // 使用空数组如果 data[firstKey] 未定义 -->
        regionOptions = data[firstKey] || [];
        createRegionCards(regionOptions);
        updateSelectedOptions();
      })
      .catch(error => {
        console.error('Error loading RegionDEG.json:', error);
      });
    
    // 加载 CellTypeDEG.json
    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/CellTypeDEG.json')
      .then(response => response.json())
      .then(data => {
        // 假设我们只关心第一个键的值
        var firstKey = Object.keys(data)[0];
        cellTypeOptions = data[firstKey] || [];
        createCellTypeCards(cellTypeOptions);
        updateSelectedOptions();
      })
      .catch(error => {
        console.error('Error loading CellTypeDEG.json:', error);
      });
  }
  
  function updateSelectedOptions() {
    if (selectedRegion && selectedCellType) {
      selectedOptions = [selectedRegion, selectedCellType];
    } else {
      selectedOptions = [];
    }
    updateAllButtonStates();
    updateSelectionSummary();
  }

  function updateSelectionSummary() {
    var regionValue = selectedRegion || 'Not selected';
    var cellTypeValue = selectedCellType || 'Not selected';
    var summaryIds = ['volcanoSelectionSummary', 'tableSelectionSummary'];
    var regionPillIds = ['selectedRegionPillTop', 'selectedRegionPillBottom'];
    var cellTypePillIds = ['selectedCellTypePillTop', 'selectedCellTypePillBottom'];

    summaryIds.forEach(function(id) {
      var summary = document.getElementById(id);
      if (summary) {
        summary.style.display = selectedRegion && selectedCellType ? 'flex' : 'none';
      }
    });

    regionPillIds.forEach(function(id) {
      var pill = document.getElementById(id);
      if (pill) {
        pill.textContent = regionValue;
      }
    });

    cellTypePillIds.forEach(function(id) {
      var pill = document.getElementById(id);
      if (pill) {
        pill.textContent = cellTypeValue;
      }
    });
  }
  
  function createRegionCards(options) {
    var container = document.getElementById('regionCards');
    container.innerHTML = '';
    selectedRegion = options.length ? options[0] : null;
    
    options.forEach(function(option, index) {
      var card = document.createElement('div');
      card.className = 'region-card';
      if (index === 0) {
        card.classList.add('selected');
      }
      
      // Create name element
      var name = document.createElement('div');
      name.className = 'region-name';
      name.textContent = option;
      
      card.appendChild(name);
      card.onclick = function() {
        selectRegionCard(this, option);
      };
      container.appendChild(card);
    });

    updateAllButtonStates();
  }
  
  function createCellTypeCards(options) {
    var container = document.getElementById('cellTypeCards');
    container.innerHTML = '';
    
    // Cell type images mapping (you may need to adjust these paths)
    var cellTypeImages = {
      'Amygdala excitatory': '{{ site.url }}{{ site.baseurl }}/images/celltypes/excitatory.png',
      'Astrocyte': '{{ site.url }}{{ site.baseurl }}/images/celltypes/astrocyte.png',
      'Cerebellar inhibitory': '{{ site.url }}{{ site.baseurl }}/images/celltypes/inhibitory.png',
      'CGE interneuron': '{{ site.url }}{{ site.baseurl }}/images/celltypes/interneuron.png',
      'Committed oligodendrocyte precursor': '{{ site.url }}{{ site.baseurl }}/images/celltypes/oligodendrocyte.png',
      'Deep layer corticothalamic and 6b': '{{ site.url }}{{ site.baseurl }}/images/celltypes/cortical.png',
      'Deep layer near-projecting': '{{ site.url }}{{ site.baseurl }}/images/celltypes/projecting.png',
      'Eccentric medium spiny neuron': '{{ site.url }}{{ site.baseurl }}/images/celltypes/neuron.png',
      'Ependymal': '{{ site.url }}{{ site.baseurl }}/images/celltypes/ependymal.png',
      'Fibroblast': '{{ site.url }}{{ site.baseurl }}/images/celltypes/fibroblast.png',
      'Hippocampal CA1-3': '{{ site.url }}{{ site.baseurl }}/images/celltypes/hippocampal.png',
      'Hippocampal CA4': '{{ site.url }}{{ site.baseurl }}/images/celltypes/hippocampal.png',
      'LAMP5-LHX6 and Chandelier': '{{ site.url }}{{ site.baseurl }}/images/celltypes/lamp5.png'
    };
    
    options.forEach(function(option, index) {
      var card = document.createElement('div');
      card.className = 'celltype-card';
      if (index === 0) {
        card.classList.add('selected');
        selectedCellType = option;
      }
      
      // Add image if available
      var img = document.createElement('img');
      img.src = cellTypeImages[option] || '{{ site.url }}{{ site.baseurl }}/images/celltypes/default.png';
      img.alt = option;
      img.onerror = function() {
        this.style.display = 'none';
      };
      
      var name = document.createElement('div');
      name.className = 'celltype-name';
      name.textContent = option;
      
      card.appendChild(img);
      card.appendChild(name);
      card.onclick = function() {
        selectCellTypeCard(this, option);
      };
      container.appendChild(card);
    });
  }
  
  function selectRegionCard(cardElement, value) {
    // Remove selected class from all region cards
    var allCards = document.querySelectorAll('.region-card');
    allCards.forEach(function(card) {
      card.classList.remove('selected');
    });
    
    // Add selected class to clicked card
    cardElement.classList.add('selected');
    selectedRegion = value;
    updateSelectedOptions();
    // 不隐藏结果,保持当前显示状态
  }
  
  function selectAllRegion() {
    var allCards = document.querySelectorAll('.region-card');
    allCards.forEach(function(card) {
      card.classList.remove('selected');
    });

    selectedRegion = 'All';
    updateSelectedOptions();
  }

  function selectAllCellType() {
    var allCards = document.querySelectorAll('.celltype-card');
    allCards.forEach(function(card) {
      card.classList.remove('selected');
    });

    selectedCellType = 'All';
    updateSelectedOptions();
  }

  function updateAllButtonStates() {
    var allRegionButton = document.getElementById('allRegionButton');
    var allCellTypeButton = document.getElementById('allCellTypeButton');
    var mode = getActiveMarkerMode();

    if (allRegionButton) {
      var showRegionAll = mode === 'A';
      allRegionButton.style.display = showRegionAll ? '' : 'none';
      var isRegionAllSelected = showRegionAll && selectedRegion === 'All';
      allRegionButton.classList.toggle('is-selected', isRegionAllSelected);
      allRegionButton.setAttribute('aria-pressed', isRegionAllSelected ? 'true' : 'false');
    }

    if (allCellTypeButton) {
      var showCellTypeAll = mode === 'B';
      allCellTypeButton.style.display = showCellTypeAll ? '' : 'none';
      var isCellTypeAllSelected = showCellTypeAll && selectedCellType === 'All';
      allCellTypeButton.classList.toggle('is-selected', isCellTypeAllSelected);
      allCellTypeButton.setAttribute('aria-pressed', isCellTypeAllSelected ? 'true' : 'false');
    }
  }

  function selectCellTypeCard(cardElement, value) {
    // Remove selected class from all celltype cards
    var allCards = document.querySelectorAll('.celltype-card');
    allCards.forEach(function(card) {
      card.classList.remove('selected');
    });
    
    // Add selected class to clicked card
    cardElement.classList.add('selected');
    selectedCellType = value;
    updateSelectedOptions();
    // 不隐藏结果,保持当前显示状态
  }
function displaySelectedImage() {
  // 显示 volcano plot loading
  var volcanoLoading = document.getElementById('volcanoLoadingIndicator');
  var imageElement = document.getElementById('selectedImage');
  
  if (volcanoLoading) {
    volcanoLoading.style.display = 'block';
  }
  if (imageElement) {
    imageElement.style.display = 'none';
  }
  
  if (selectedOptions.length === 2) {
    var imageName = encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '.png';
    var imageName2 = encodeURIComponent(selectedOptions[1]) + '_' + encodeURIComponent(selectedOptions[0]) + '.png';
    var imagePath;
    if (selectedButton === 'A') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/Volcano/png/' + imageName;
    } else if (selectedButton === 'B') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/Volcano/png/' + imageName2;
    } else {
      console.error('Invalid button selection:', selectedButton);
      hideVolcanoLoading();
      return;
    }
    console.log('Image path:', imagePath); // 调试信息
    
    if (imageElement) {
      // 处理图片加载成功
      imageElement.onload = function() {
        console.log('Image loaded successfully:', imagePath);
        var errorMessage = document.getElementById('errorMessage');
        if (errorMessage) {
          errorMessage.remove();
        }
        imageLoaded = true;
        hideVolcanoLoading();
        imageElement.style.display = 'block';
      };
      // 处理图片加载错误
      imageElement.onerror = function() {
        console.error('Failed to load image:', imagePath);
        imageElement.src = '';
        imageElement.alt = '';
        displayErrorMessage('No region or cell type in this dataset');
        imageLoaded = false;
        hideVolcanoLoading();
      };
      // 设置图片路径和样式
      imageElement.src = imagePath;
      imageElement.style.width = '100%'; // 设置宽度
      imageElement.style.maxWidth = '500px';
      imageElement.style.height = 'auto'; // 高度自动调整
      imageElement.style.margin = '0 auto'; // 图片居中
    } else {
      console.error('Element with id "selectedImage" not found.');
      hideVolcanoLoading();
    }
  } else {
    console.log('Please select the necessary options.');
    hideVolcanoLoading();
  }
}

function hideVolcanoLoading() {
  var volcanoLoading = document.getElementById('volcanoLoadingIndicator');
  if (volcanoLoading) {
    volcanoLoading.style.display = 'none';
  }
}

function displayErrorMessage(message) {
  var imageElement = document.getElementById('selectedImage');
  var errorMessage = document.getElementById('errorMessage');
  if (!errorMessage) {
    errorMessage = document.createElement('div');
    errorMessage.id = 'errorMessage';
    errorMessage.textContent = message;
    errorMessage.style.textAlign = 'center';
    imageElement.parentNode.insertBefore(errorMessage, imageElement.nextSibling);
  } else {
    errorMessage.textContent = message;
  }
}
function hideTableAndShowMessage() {
  var tableContainer = document.getElementById('csvTableContainer');
  tableContainer.innerHTML = ''; // 清空表格内容
  // 显示 "No table" 消息
  var noTableMessage = document.getElementById('noTableMessage');
  if (!noTableMessage) {
    noTableMessage = document.createElement('div');
    noTableMessage.id = 'noTableMessage';
    noTableMessage.textContent = 'No the region or cell type in this dataset';
    noTableMessage.style.textAlign = 'center';
    tableContainer.appendChild(noTableMessage);
  }
  // 确保隐藏 table loading
  hideTableLoading();
}
// function sortTable(columnIndex) {
//     var table = document.getElementById("your-table-id"); // 替换为你的表格的ID
//     var rows = Array.from(table.rows).slice(1); // 去掉表头，获取行数组 
//     // 根据指定的列索引进行排序
//     rows.sort(function(rowA, rowB) {
//         var cellA = rowA.cells[columnIndex].textContent.trim();
//         var cellB = rowB.cells[columnIndex].textContent.trim();
//         return cellA.localeCompare(cellB, "zh");
//     });
//     // 将排序后的行重新添加到表格中
//     rows.forEach(function(row) {
//         table.appendChild(row);
//     });
// }
// jQuery( document ).ready(function( $ ) {
//         $(document).ready( function () {
//         $.noConflict();
//         var table = $('#mytable').DataTable();
//         });
// })
function displaySelectedTable() {
  // 显示表格 loading
  var tableLoading = document.getElementById('tableLoadingIndicator');
  var tableContainer = document.getElementById('csvTableContainer');
  
  if (tableLoading) {
    tableLoading.style.display = 'block';
  }
  
  clearTableAndMessage();
  
  if (selectedOptions.length === 2) {
    var tableName;
    var tablePath;
    if (selectedButton === 'A') {
      tableName =  encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/' + tableName;
    } else if (selectedButton === 'B') {
      tableName = encodeURIComponent(selectedOptions[1]) + '_' + encodeURIComponent(selectedOptions[0]) + '.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/' + tableName;
    } else {
      console.log('Please select an image and options.');
      hideTableAndShowMessage();
      hideTableLoading();
      return;
    }
    
    var xhr = new XMLHttpRequest();
    xhr.open('GET', tablePath, true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          var csvData = xhr.responseText;
          
          var rows = csvData.split(/\r?\n/).filter(function(row) {
            return row.trim() !== '';
          });
          if (!rows.length) {
            hideTableAndShowMessage();
            hideTableLoading();
            return;
          }

          var headers = rows[0].split(',').map(function(header) {
            return header.replace(/^"(.*)"$/, '$1').trim();
          });
          var tableHtml = '<table id="mytable" class="mytable table table-striped table-bordered" cellspacing="0" width="100%">';
          var headerHtml = '<thead><tr>';
          headers.forEach(function(header) {
            headerHtml += '<th>' + header + '</th>';
          });
          headerHtml += '</tr><tr class="column-filters">';
          headers.forEach(function(header) {
            headerHtml += '<th><input type="text" placeholder="filter" aria-label="filter ' + header + '" /></th>';
          });
          headerHtml += '</tr></thead><tbody>';
          tableHtml += headerHtml;
          for (var i = 1; i < rows.length; i++) {
            var cells = rows[i].split(',');
            if (!cells.length || (cells.length === 1 && cells[0].trim() === '')) {
              continue;
            }
            tableHtml += '<tr>';
            for (var j = 0; j < cells.length; j++) {
              var cellContent = cells[j].replace(/^"(.*)"$/, '$1');
              tableHtml += '<td>' + cellContent + '</td>';
            }
            tableHtml += '</tr>';
          }
          tableHtml += `</tbody>
        </table>`;
          var noTableMessage = document.getElementById('noTableMessage');
          if (noTableMessage) {
            noTableMessage.remove();
          }
          tableContainer.innerHTML = tableHtml;
          
          // 表格 HTML 已插入，立即隐藏 loading
          hideTableLoading();
          
          // 然后初始化 DataTable（不影响 loading 显示）
          initializeDataTable();
        } else {
          hideTableAndShowMessage();
          hideTableLoading();
        }
      }
    };
    xhr.send();
  } else {
    console.log('Please select the necessary options.');
    hideTableAndShowMessage();
    hideTableLoading();
  }
}

function hideTableLoading() {
  var tableLoading = document.getElementById('tableLoadingIndicator');
  if (tableLoading) {
    tableLoading.style.display = 'none';
  }
}
function initializeDataTable(callback) {
  // 使用 setTimeout 确保 DOM 已更新
  setTimeout(function() {
    try {
      var $ = jQuery.noConflict();
      // 销毁已存在的 DataTable 实例
      if ($.fn.DataTable.isDataTable('#mytable')) {
        $('#mytable').DataTable().destroy();
      }
      // 初始化新的 DataTable
      $('#mytable').DataTable({
        "order": [[1, "asc"]], // 默认按第二列（索引1）升序排序
        "initComplete": function(settings, json) {
          // DataTable 初始化完成后执行回调
          console.log('DataTable initialized');
          if (callback && typeof callback === 'function') {
            callback();
          }
        }
      });
    } catch (error) {
      console.error('Error initializing DataTable:', error);
      // 如果初始化失败，也要隐藏 loading
      if (callback && typeof callback === 'function') {
        callback();
      }
    }
  }, 100);
}
function clearTableAndMessage() {
  // 清除表格内容和错误消息
  var tableContainer = document.getElementById('csvTableContainer');
  tableContainer.innerHTML = '';
  
  // 移除可能存在的错误消息
  var noTableMessage = document.getElementById('noTableMessage');
  if (noTableMessage) {
    noTableMessage.remove();
  }
}
function buildDownloadFileName() {
  var parts = ['markers'];
  if (selectedRegion) {
    parts.push(selectedRegion.replace(/\s+/g, '_'));
  }
  if (selectedCellType) {
    parts.push(selectedCellType.replace(/\s+/g, '_'));
  }
  return parts.join('_');
}

function buildRemoteFileCandidates(baseUrl, firstValue, secondValue, extension) {
  var rawName = firstValue + '_' + secondValue + '.' + extension;
  var encodedPartName = encodeURIComponent(firstValue) + '_' + encodeURIComponent(secondValue) + '.' + extension;
  var encodedWholeName = encodeURI(rawName);
  var spaceAsUnderscoreName = firstValue.replace(/\s+/g, '_') + '_' + secondValue.replace(/\s+/g, '_') + '.' + extension;
  var plusAsTextName = firstValue.replace(/\+/g, 'plus') + '_' + secondValue.replace(/\+/g, 'plus') + '.' + extension;

  return Array.from(new Set([
    baseUrl + rawName,
    baseUrl + encodedPartName,
    baseUrl + encodedWholeName,
    baseUrl + spaceAsUnderscoreName,
    baseUrl + encodeURI(spaceAsUnderscoreName),
    baseUrl + plusAsTextName,
    baseUrl + encodeURI(plusAsTextName)
  ]));
}

function getActiveMarkerMode() {
  var buttonB = document.getElementById('buttonB');
  if (buttonB && buttonB.classList.contains('active')) {
    return 'B';
  }
  return selectedButton === 'B' ? 'B' : 'A';
}

function buildMarkerRequestCandidates(kind, extension) {
  if (selectedOptions.length !== 2) {
    return [];
  }

  var mode = getActiveMarkerMode();
  var baseUrl;
  var firstValue;
  var secondValue;

  if (mode === 'A' && selectedRegion === 'All') {
    baseUrl = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/' + (kind === 'image' ? 'Volcano/png/' : '');
    firstValue = selectedRegion;
    secondValue = selectedCellType;
  } else if (mode === 'B' && selectedCellType === 'All') {
    baseUrl = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/' + (kind === 'image' ? 'Volcano/png/' : '');
    firstValue = selectedCellType;
    secondValue = selectedRegion;
  } else if (mode === 'B') {
    baseUrl = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/' + (kind === 'image' ? 'Volcano/png/' : '');
    firstValue = selectedCellType;
    secondValue = selectedRegion;
  } else {
    baseUrl = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/' + (kind === 'image' ? 'Volcano/png/' : '');
    firstValue = selectedRegion;
    secondValue = selectedCellType;
  }

  if (!firstValue || !secondValue) {
    return [];
  }

  return buildRemoteFileCandidates(baseUrl, firstValue, secondValue, extension);
}

function loadImageWithFallback(imageElement, candidates, onSuccess, onFailure) {
  var index = 0;

  function tryNext() {
    if (index >= candidates.length) {
      imageElement.onload = null;
      imageElement.onerror = null;
      if (onFailure) {
        onFailure();
      }
      return;
    }

    var candidate = candidates[index++];
    imageElement.onload = function() {
      imageElement.onload = null;
      imageElement.onerror = null;
      if (onSuccess) {
        onSuccess(candidate);
      }
    };
    imageElement.onerror = function() {
      tryNext();
    };
    imageElement.src = candidate;
  }

  tryNext();
}

function requestTextWithFallback(candidates, onSuccess, onFailure) {
  var index = 0;

  function tryNext() {
    if (index >= candidates.length) {
      if (onFailure) {
        onFailure();
      }
      return;
    }

    var candidate = candidates[index++];
    var xhr = new XMLHttpRequest();
    xhr.open('GET', candidate, true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState !== 4) {
        return;
      }
      if (xhr.status === 200) {
        onSuccess(xhr.responseText, candidate);
      } else {
        tryNext();
      }
    };
    xhr.onerror = tryNext;
    xhr.send();
  }

  tryNext();
}

function escapeHtml(value) {
  return String(value)
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/"/g, '&quot;')
    .replace(/'/g, '&#39;');
}

function renderTableRowsInBatches(tableBody, dataRows, requestId, done) {
  var batchSize = 200;
  var index = 0;
  var progressElement = document.getElementById('tableProgress');

  function renderNextBatch() {
    if (requestId !== latestTableRequestId) {
      return;
    }

    var fragment = document.createDocumentFragment();
    var end = Math.min(index + batchSize, dataRows.length);

    for (; index < end; index++) {
      var row = dataRows[index];
      if (!row.length || (row.length === 1 && row[0].trim() === '')) {
        continue;
      }

      var tr = document.createElement('tr');
      for (var j = 0; j < row.length; j++) {
        var td = document.createElement('td');
        td.textContent = row[j].replace(/^"(.*)"$/, '$1');
        tr.appendChild(td);
      }
      fragment.appendChild(tr);
    }

    tableBody.appendChild(fragment);

    if (progressElement) {
      progressElement.textContent = 'Rendering rows: ' + Math.min(index, dataRows.length) + ' / ' + dataRows.length;
    }

    if (index < dataRows.length) {
      setTimeout(renderNextBatch, 0);
      return;
    }

    if (progressElement) {
      progressElement.remove();
    }

    done();
  }

  renderNextBatch();
}

function displaySelectedImage() {
  var volcanoLoading = document.getElementById('volcanoLoadingIndicator');
  var imageElement = document.getElementById('selectedImage');
  var requestId = ++latestImageRequestId;
  var errorMessage = document.getElementById('errorMessage');

  if (volcanoLoading) {
    volcanoLoading.style.display = 'block';
  }
  if (imageElement) {
    imageElement.style.display = 'none';
  }
  if (errorMessage) {
    errorMessage.remove();
  }

  if (selectedOptions.length !== 2) {
    hideVolcanoLoading();
    return;
  }

  var imageCandidates = buildMarkerRequestCandidates('image', 'png');
  if (!imageCandidates.length) {
    hideVolcanoLoading();
    return;
  }

  if (!imageElement) {
    hideVolcanoLoading();
    return;
  }

  loadImageWithFallback(imageElement, imageCandidates, function(imagePath) {
    if (requestId !== latestImageRequestId) {
      return;
    }
    imageElement.onload = null;
    imageElement.onerror = null;
    imageLoaded = true;
    hideVolcanoLoading();
    imageElement.style.display = 'block';
    console.log('Image loaded successfully:', imagePath);
  }, function() {
    if (requestId !== latestImageRequestId) {
      return;
    }
    imageElement.onload = null;
    imageElement.onerror = null;
    imageElement.src = '';
    imageElement.alt = '';
    imageLoaded = false;
    hideVolcanoLoading();
    displayErrorMessage('No region or cell type in this dataset');
    console.error('Failed to load image from all candidates:', imageCandidates);
  });

  imageElement.style.width = '100%';
  imageElement.style.maxWidth = '500px';
  imageElement.style.height = 'auto';
  imageElement.style.margin = '0 auto';
}

function displaySelectedTable() {
  var tableLoading = document.getElementById('tableLoadingIndicator');
  var tableContainer = document.getElementById('csvTableContainer');
  var requestId = ++latestTableRequestId;

  if (tableLoading) {
    tableLoading.style.display = 'block';
  }

  clearTableAndMessage();

  if (selectedOptions.length !== 2) {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  var tableCandidates = buildMarkerRequestCandidates('table', 'csv');
  if (!tableCandidates.length) {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  requestTextWithFallback(tableCandidates, function(csvData, resolvedUrl) {
    if (requestId !== latestTableRequestId) {
      return;
    }
    latestResolvedTableUrl = resolvedUrl || '';
    var rows = csvData.split(/\r?\n/).filter(function(row) {
      return row.trim() !== '';
    });
    if (!rows.length) {
      hideTableAndShowMessage();
      hideTableLoading();
      return;
    }

    var headers = rows[0].split(',').map(function(header) {
      return header.replace(/^"(.*)"$/, '$1').trim();
    });
    var dataRows = [];
    for (var i = 1; i < rows.length; i++) {
      var cells = rows[i].split(',');
      if (!cells.length || (cells.length === 1 && cells[0].trim() === '')) {
        continue;
      }
      dataRows.push(cells.map(function(cell) {
        return cell.replace(/^"(.*)"$/, '$1');
      }));
    }

    renderDataTable(tableContainer, headers, dataRows, requestId);
  }, function() {
    if (requestId !== latestTableRequestId) {
      return;
    }
    hideTableAndShowMessage();
    hideTableLoading();
    console.error('Failed to load table from all candidates:', tableCandidates);
  });
}

function renderDataTable(tableContainer, headers, dataRows, requestId) {
  var tableHtml = '<table id="mytable" class="mytable table table-striped table-bordered" cellspacing="0" width="100%"><thead><tr>';
  headers.forEach(function(header) {
    tableHtml += '<th>' + escapeHtml(header) + '</th>';
  });
  tableHtml += '</tr><tr class="column-filters">';
  headers.forEach(function(header) {
    tableHtml += '<th><input type="text" placeholder="filter" aria-label="filter ' + escapeHtml(header) + '" /></th>';
  });
  tableHtml += '</tr></thead><tbody>';
  dataRows.forEach(function(row) {
    tableHtml += '<tr>';
    row.forEach(function(cell) {
      tableHtml += '<td>' + escapeHtml(cell) + '</td>';
    });
    tableHtml += '</tr>';
  });
  tableHtml += '</tbody></table>';

  tableContainer.innerHTML = tableHtml;
  hideTableLoading();
  initializeDataTable(requestId);
}

function initializeDataTable(requestId, callback) {
  setTimeout(function() {
    try {
      if (typeof requestId === 'number' && requestId !== latestTableRequestId) {
        return;
      }
      var $ = jQuery.noConflict();
      if ($.fn.DataTable.isDataTable('#mytable')) {
        $('#mytable').DataTable().destroy();
      }
      $('#mytable').DataTable({
        destroy: true,
        deferRender: true,
        orderCellsTop: true,
        pageLength: 10,
        lengthMenu: [[10, 25, 50, 100], [10, 25, 50, 100]],
        order: [[1, 'desc']],
        dom: 'Bfrtip',
        buttons: [
          {
            extend: 'csvHtml5',
            text: 'csv',
            title: null,
            filename: function() {
              return buildDownloadFileName();
            }
          },
          {
            extend: 'pdfHtml5',
            text: 'pdf',
            title: buildDownloadFileName(),
            filename: function() {
              return buildDownloadFileName();
            }
          }
        ],
        paging: true,
        searching: true,
        info: true,
        scrollX: true,
        language: {
          search: 'Search:',
          lengthMenu: 'Show _MENU_',
          info: 'Showing _START_ to _END_ of _TOTAL_ entries',
          infoEmpty: 'Showing 0 to 0 of 0 entries'
        },
        initComplete: function() {
          var api = this.api();
          var headerRows = api.table().header().rows;
          var filterRow = headerRows && headerRows.length > 1 ? headerRows[1] : null;

          if (filterRow) {
            api.columns().every(function(colIdx) {
              var column = this;
              var input = $('input', filterRow.cells[colIdx]);
              input.off('keyup change').on('keyup change', function() {
                if (column.search() !== this.value) {
                  column.search(this.value).draw();
                }
              });
            });
          }

          api.draw(false);
          if (callback && typeof callback === 'function') {
            callback();
          }
        }
      });
    } catch (error) {
      console.error('Error initializing DataTable:', error);
      if (callback && typeof callback === 'function') {
        callback();
      }
    }
  }, 100);
}

function clearTableAndMessage() {
  var tableContainer = document.getElementById('csvTableContainer');

  try {
    var $ = jQuery.noConflict();
    if ($.fn.DataTable && $.fn.DataTable.isDataTable('#mytable')) {
      $('#mytable').DataTable().destroy();
    }
  } catch (error) {
    console.error('Error destroying DataTable:', error);
  }

  tableContainer.innerHTML = '';

  var noTableMessage = document.getElementById('noTableMessage');
  if (noTableMessage) {
    noTableMessage.remove();
  }
}

function isMarkersNumericValue(value) {
  if (value === null || value === undefined || String(value).trim() === '') {
    return false;
  }
  var num = Number(value);
  return !isNaN(num) && isFinite(num);
}

function detectMarkersColumnTypes(headers, rows) {
  return headers.map(function(_, colIndex) {
    var sampleSize = Math.min(rows.length, 100);
    var numericCount = 0;
    var nonEmptyCount = 0;

    for (var i = 0; i < sampleSize; i++) {
      var value = rows[i][colIndex];
      if (value === null || value === undefined || String(value).trim() === '') {
        continue;
      }
      nonEmptyCount++;
      if (isMarkersNumericValue(value)) {
        numericCount++;
      }
    }

    if (nonEmptyCount === 0) {
      return 'string';
    }

    return numericCount / nonEmptyCount >= 0.8 ? 'numeric' : 'string';
  });
}

function createMarkersNumericBound() {
  return { operator: '', value: '' };
}

function createMarkersColumnFilter(columnType) {
  if (columnType === 'numeric') {
    return {
      type: 'numeric',
      lower: createMarkersNumericBound(),
      upper: createMarkersNumericBound()
    };
  }
  return { type: 'text', value: '' };
}

function isMarkersNumericBoundActive(bound) {
  return !!(bound && bound.operator && String(bound.value).trim() !== '' && !isNaN(Number(bound.value)));
}

function isMarkersNumericFilterActive(filter) {
  return isMarkersNumericBoundActive(filter.lower) || isMarkersNumericBoundActive(filter.upper);
}

function matchesMarkersNumericBound(num, bound) {
  if (!isMarkersNumericBoundActive(bound)) {
    return true;
  }

  var threshold = Number(bound.value);
  switch (bound.operator) {
    case '>=':
      return num >= threshold;
    case '<=':
      return num <= threshold;
    case '>':
      return num > threshold;
    case '<':
      return num < threshold;
    default:
      return true;
  }
}

function matchesMarkersNumericFilter(cellValue, filter) {
  if (!isMarkersNumericFilterActive(filter)) {
    return true;
  }

  if (!isMarkersNumericValue(cellValue)) {
    return false;
  }

  var num = Number(cellValue);
  return matchesMarkersNumericBound(num, filter.lower) && matchesMarkersNumericBound(num, filter.upper);
}

function matchesMarkersColumnFilter(cellValue, filter) {
  if (filter.type === 'numeric') {
    return matchesMarkersNumericFilter(cellValue, filter);
  }

  if (!filter.value) {
    return true;
  }

  return String(cellValue || '').toLowerCase().indexOf(filter.value) !== -1;
}

function buildMarkersNumericOperatorOptions(selectedValue) {
  var options = [
    { value: '', label: '—' },
    { value: '>=', label: '&ge;' },
    { value: '<=', label: '&le;' },
    { value: '>', label: '&gt;' },
    { value: '<', label: '&lt;' }
  ];

  return options.map(function(option) {
    var selected = option.value === selectedValue ? ' selected' : '';
    return '<option value="' + option.value + '"' + selected + '>' + option.label + '</option>';
  }).join('');
}

function buildMarkersNumericBoundRow(boundKey, header, bound) {
  return '<div class="markers-numeric-filter-row" data-bound="' + boundKey + '">' +
    '<select data-filter-part="operator" aria-label="operator for ' + escapeHtml(header) + '">' +
    buildMarkersNumericOperatorOptions(bound ? bound.operator : '') +
    '</select>' +
    '<input type="text" data-filter-part="value" inputmode="decimal" placeholder="value" value="' + escapeHtml(bound ? bound.value : '') + '" aria-label="value for ' + escapeHtml(header) + '" />' +
    '</div>';
}

function buildMarkersNumericFilterHtml(index, header) {
  return '<div class="markers-numeric-filter" data-filter-index="' + index + '">' +
    buildMarkersNumericBoundRow('lower', header) +
    buildMarkersNumericBoundRow('upper', header) +
    '<button type="button" class="markers-numeric-filter-clear" data-filter-part="clear" aria-label="clear filter for ' + escapeHtml(header) + '" title="Clear">&times;</button>' +
    '</div>';
}

function readMarkersNumericBoundFromRow(row) {
  if (!row) {
    return createMarkersNumericBound();
  }

  var operatorSelect = row.querySelector('[data-filter-part="operator"]');
  var valueInput = row.querySelector('[data-filter-part="value"]');
  return {
    operator: operatorSelect ? operatorSelect.value : '',
    value: valueInput ? valueInput.value.trim() : ''
  };
}

function syncMarkersNumericBoundRow(row, bound) {
  if (!row || !bound) {
    return;
  }

  var operatorSelect = row.querySelector('[data-filter-part="operator"]');
  var valueInput = row.querySelector('[data-filter-part="value"]');
  if (operatorSelect) {
    operatorSelect.value = bound.operator || '';
  }
  if (valueInput) {
    valueInput.value = bound.value || '';
  }
  row.classList.toggle('is-bound-active', isMarkersNumericBoundActive(bound));
}

function syncMarkersNumericFilterPanel(panel, filter) {
  if (!panel || !filter) {
    return;
  }

  syncMarkersNumericBoundRow(panel.querySelector('[data-bound="lower"]'), filter.lower);
  syncMarkersNumericBoundRow(panel.querySelector('[data-bound="upper"]'), filter.upper);
  panel.classList.toggle('is-active', isMarkersNumericFilterActive(filter));
}

function applyMarkersNumericFilterFromPanel(index, panel) {
  var filter = markersTableState.filters[index];
  filter.lower = readMarkersNumericBoundFromRow(panel.querySelector('[data-bound="lower"]'));
  filter.upper = readMarkersNumericBoundFromRow(panel.querySelector('[data-bound="upper"]'));
  syncMarkersNumericFilterPanel(panel, filter);
  markersTableState.page = 1;
  updateMarkersTableView();
}

function clearMarkersNumericFilter(index, panel) {
  var filter = markersTableState.filters[index];
  filter.lower = createMarkersNumericBound();
  filter.upper = createMarkersNumericBound();
  syncMarkersNumericFilterPanel(panel, filter);
  markersTableState.page = 1;
  updateMarkersTableView();
}

function renderMarkersTableV3() {
  var tableLoading = document.getElementById('tableLoadingIndicator');
  var tableContainer = document.getElementById('csvTableContainer');
  var requestId = ++latestTableRequestId;

  if (tableLoading) {
    tableLoading.style.display = 'block';
  }

  clearTableAndMessage();
  markersTableState = null;

  if (selectedOptions.length !== 2) {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  var tableCandidates = buildMarkerRequestCandidates('table', 'csv');
  if (!tableCandidates.length) {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  requestTextWithFallback(tableCandidates, function(csvData, resolvedUrl) {
    if (requestId !== latestTableRequestId) {
      return;
    }

    latestResolvedTableUrl = resolvedUrl || '';

    var rows = csvData.split(/\r?\n/).filter(function(row) {
      return row.trim() !== '';
    });
    if (!rows.length) {
      hideTableAndShowMessage();
      hideTableLoading();
      return;
    }

    var headers = rows[0].split(',').map(function(header) {
      return header.replace(/^"(.*)"$/, '$1').trim();
    });

    var dataRows = [];
    for (var i = 1; i < rows.length; i++) {
      var cells = rows[i].split(',');
      if (!cells.length || (cells.length === 1 && cells[0].trim() === '')) {
        continue;
      }
      dataRows.push(cells.map(function(cell) {
        return cell.replace(/^"(.*)"$/, '$1');
      }));
    }

    var columnTypes = detectMarkersColumnTypes(headers, dataRows);

    markersTableState = {
      headers: headers,
      rows: dataRows,
      columnTypes: columnTypes,
      filters: columnTypes.map(createMarkersColumnFilter),
      sortColumn: 1,
      sortDirection: 'desc',
      page: 1,
      pageSize: 10,
      requestId: requestId
    };

    renderMarkersTableShell(tableContainer, headers);
    hideTableLoading();
    updateMarkersTableView();
  }, function() {
    if (requestId !== latestTableRequestId) {
      return;
    }
    hideTableAndShowMessage();
    hideTableLoading();
  });
}

function renderMarkersTableShell(tableContainer, headers) {
  var toolbarHtml = '<div class="markers-custom-toolbar">';
  if (latestResolvedTableUrl) {
    toolbarHtml += '<a class="markers-download-link" href="' + escapeHtml(latestResolvedTableUrl) + '" download="' + escapeHtml(buildDownloadFileName()) + '.csv">csv</a>';
  }
  toolbarHtml += '</div>';

  var tableHtml = '<table id="mytable" class="mytable table table-striped table-bordered" cellspacing="0" width="100%"><thead><tr>';
  headers.forEach(function(header, index) {
    tableHtml += '<th class="markers-sortable" data-column-index="' + index + '" role="button" tabindex="0" aria-sort="none" title="Click to sort">' + escapeHtml(header) + '</th>';
  });
  tableHtml += '</tr><tr class="column-filters">';
  headers.forEach(function(header, index) {
    if (markersTableState.columnTypes[index] === 'numeric') {
      tableHtml += '<th class="markers-numeric-filter-cell">' + buildMarkersNumericFilterHtml(index, header) + '</th>';
    } else {
      tableHtml += '<th class="markers-text-filter-cell"><input type="text" data-filter-index="' + index + '" data-filter-type="text" placeholder="filter" aria-label="filter ' + escapeHtml(header) + '" /></th>';
    }
  });
  tableHtml += '</tr></thead><tbody></tbody></table>';
  tableHtml += '<div class="markers-custom-footer"><div id="markersTableInfo"></div><div id="markersTablePagination"></div></div>';

  tableContainer.innerHTML = toolbarHtml + tableHtml;

  var textFilterInputs = tableContainer.querySelectorAll('[data-filter-type="text"]');
  textFilterInputs.forEach(function(input) {
    input.addEventListener('input', function(event) {
      var index = Number(event.target.getAttribute('data-filter-index'));
      markersTableState.filters[index].value = event.target.value.toLowerCase();
      markersTableState.page = 1;
      updateMarkersTableView();
    });
  });

  var numericFilterPanels = tableContainer.querySelectorAll('.markers-numeric-filter');
  numericFilterPanels.forEach(function(panel) {
    var index = Number(panel.getAttribute('data-filter-index'));
    var boundRows = panel.querySelectorAll('[data-bound]');
    var clearButton = panel.querySelector('[data-filter-part="clear"]');

    boundRows.forEach(function(row) {
      var operatorSelect = row.querySelector('[data-filter-part="operator"]');
      var valueInput = row.querySelector('[data-filter-part="value"]');

      if (operatorSelect) {
        operatorSelect.addEventListener('change', function() {
          applyMarkersNumericFilterFromPanel(index, panel);
        });
      }

      if (valueInput) {
        valueInput.addEventListener('input', function() {
          applyMarkersNumericFilterFromPanel(index, panel);
        });
        valueInput.addEventListener('keydown', function(event) {
          if (event.key === 'Enter') {
            event.preventDefault();
            applyMarkersNumericFilterFromPanel(index, panel);
          }
        });
      }
    });

    if (clearButton) {
      clearButton.addEventListener('click', function(event) {
        event.preventDefault();
        clearMarkersNumericFilter(index, panel);
      });
    }

    syncMarkersNumericFilterPanel(panel, markersTableState.filters[index]);
  });

  var sortableHeaders = tableContainer.querySelectorAll('[data-column-index]');
  sortableHeaders.forEach(function(header) {
    function sortByHeader(event) {
      var index = Number(event.currentTarget.getAttribute('data-column-index'));
      if (markersTableState.sortColumn === index) {
        markersTableState.sortDirection = markersTableState.sortDirection === 'asc' ? 'desc' : 'asc';
      } else {
        markersTableState.sortColumn = index;
        markersTableState.sortDirection = 'asc';
      }
      markersTableState.page = 1;
      updateMarkersTableView();
    }

    header.addEventListener('click', sortByHeader);
    header.addEventListener('keydown', function(event) {
      if (event.key === 'Enter' || event.key === ' ') {
        event.preventDefault();
        sortByHeader(event);
      }
    });
  });

  updateMarkersSortIndicators();
}

function updateMarkersTableView() {
  if (!markersTableState || markersTableState.requestId !== latestTableRequestId) {
    return;
  }

  var filteredRows = markersTableState.rows.filter(function(row) {
    return markersTableState.filters.every(function(filterValue, index) {
      return matchesMarkersColumnFilter(row[index], filterValue);
    });
  });

  filteredRows.sort(function(a, b) {
    var col = markersTableState.sortColumn;
    var left = a[col];
    var right = b[col];
    var leftNum = Number(left);
    var rightNum = Number(right);
    var result;

    if (!isNaN(leftNum) && !isNaN(rightNum)) {
      result = leftNum - rightNum;
    } else {
      result = String(left).localeCompare(String(right), 'en', { numeric: true, sensitivity: 'base' });
    }

    return markersTableState.sortDirection === 'asc' ? result : -result;
  });

  var total = filteredRows.length;
  var totalPages = Math.max(1, Math.ceil(total / markersTableState.pageSize));
  if (markersTableState.page > totalPages) {
    markersTableState.page = totalPages;
  }

  var startIndex = (markersTableState.page - 1) * markersTableState.pageSize;
  var endIndex = Math.min(startIndex + markersTableState.pageSize, total);
  var pageRows = filteredRows.slice(startIndex, endIndex);

  renderMarkersTableBody(pageRows);
  renderMarkersTableFooter(total, totalPages, startIndex, endIndex);
  updateMarkersSortIndicators();
}

function updateMarkersSortIndicators() {
  if (!markersTableState) {
    return;
  }

  var headers = document.querySelectorAll('#csvTableContainer .markers-sortable');
  headers.forEach(function(header) {
    var index = Number(header.getAttribute('data-column-index'));
    var isActive = index === markersTableState.sortColumn;
    header.classList.toggle('sort-asc', isActive && markersTableState.sortDirection === 'asc');
    header.classList.toggle('sort-desc', isActive && markersTableState.sortDirection === 'desc');
    header.setAttribute('aria-sort', isActive ? (markersTableState.sortDirection === 'asc' ? 'ascending' : 'descending') : 'none');
  });
}

function renderMarkersTableBody(rows) {
  var tableBody = document.querySelector('#csvTableContainer #mytable tbody');
  if (!tableBody) {
    return;
  }

  var html = '';
  rows.forEach(function(row) {
    html += '<tr>';
    row.forEach(function(cell) {
      html += '<td>' + escapeHtml(cell) + '</td>';
    });
    html += '</tr>';
  });

  tableBody.innerHTML = html || '<tr><td colspan="' + markersTableState.headers.length + '" style="text-align:center;">No matching records</td></tr>';
}

function renderMarkersTableFooter(total, totalPages, startIndex, endIndex) {
  var info = document.getElementById('markersTableInfo');
  var pagination = document.getElementById('markersTablePagination');
  if (!info || !pagination) {
    return;
  }

  info.innerHTML = 'Showing ' + (total ? startIndex + 1 : 0) + ' to ' + endIndex + ' of ' + total + ' entries ' +
    '<select id="markersPageSize" class="markers-page-size">' +
    '<option value="10"' + (markersTableState.pageSize === 10 ? ' selected' : '') + '>10</option>' +
    '<option value="25"' + (markersTableState.pageSize === 25 ? ' selected' : '') + '>25</option>' +
    '<option value="50"' + (markersTableState.pageSize === 50 ? ' selected' : '') + '>50</option>' +
    '<option value="100"' + (markersTableState.pageSize === 100 ? ' selected' : '') + '>100</option>' +
    '</select>';

  var pageSizeSelect = document.getElementById('markersPageSize');
  if (pageSizeSelect) {
    pageSizeSelect.onchange = function(event) {
      markersTableState.pageSize = Number(event.target.value);
      markersTableState.page = 1;
      updateMarkersTableView();
    };
  }

  var html = '';
  html += '<button class="markers-page-btn" ' + (markersTableState.page === 1 ? 'disabled' : '') + ' data-page-action="prev">Prev</button>';
  for (var page = 1; page <= totalPages; page++) {
    if (page === 1 || page === totalPages || Math.abs(page - markersTableState.page) <= 1) {
      html += '<button class="markers-page-btn' + (page === markersTableState.page ? ' is-active' : '') + '" data-page-number="' + page + '">' + page + '</button>';
    } else if (page === 2 && markersTableState.page > 4) {
      html += '<span>...</span>';
    } else if (page === totalPages - 1 && markersTableState.page < totalPages - 3) {
      html += '<span>...</span>';
    }
  }
  html += '<button class="markers-page-btn" ' + (markersTableState.page === totalPages ? 'disabled' : '') + ' data-page-action="next">Next</button>';
  pagination.innerHTML = html;

  pagination.querySelectorAll('[data-page-number]').forEach(function(button) {
    button.onclick = function(event) {
      markersTableState.page = Number(event.currentTarget.getAttribute('data-page-number'));
      updateMarkersTableView();
    };
  });

  pagination.querySelectorAll('[data-page-action]').forEach(function(button) {
    button.onclick = function(event) {
      var action = event.currentTarget.getAttribute('data-page-action');
      if (action === 'prev' && markersTableState.page > 1) {
        markersTableState.page -= 1;
      }
      if (action === 'next' && markersTableState.page < totalPages) {
        markersTableState.page += 1;
      }
      updateMarkersTableView();
    };
  });
}

function renderMarkersTableV2() {
  var tableLoading = document.getElementById('tableLoadingIndicator');
  var tableContainer = document.getElementById('csvTableContainer');
  var requestId = ++latestTableRequestId;

  if (tableLoading) {
    tableLoading.style.display = 'block';
  }

  clearTableAndMessage();

  if (selectedOptions.length !== 2) {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  var tableCandidates;
  if (selectedButton === 'A') {
    tableCandidates = buildRemoteFileCandidates(
      'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/',
      selectedOptions[0],
      selectedOptions[1],
      'csv'
    );
  } else if (selectedButton === 'B') {
    tableCandidates = buildRemoteFileCandidates(
      'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/',
      selectedOptions[1],
      selectedOptions[0],
      'csv'
    );
  } else {
    hideTableAndShowMessage();
    hideTableLoading();
    return;
  }

  requestTextWithFallback(tableCandidates, function(csvData) {
    if (requestId !== latestTableRequestId) {
      return;
    }

    var rows = csvData.split(/\r?\n/).filter(function(row) {
      return row.trim() !== '';
    });
    if (!rows.length) {
      hideTableAndShowMessage();
      hideTableLoading();
      return;
    }

    var headers = rows[0].split(',').map(function(header) {
      return header.replace(/^"(.*)"$/, '$1').trim();
    });

    var dataRows = [];
    for (var i = 1; i < rows.length; i++) {
      var cells = rows[i].split(',');
      if (!cells.length || (cells.length === 1 && cells[0].trim() === '')) {
        continue;
      }
      dataRows.push(cells.map(function(cell) {
        return cell.replace(/^"(.*)"$/, '$1');
      }));
    }

    var tableHtml = '<table id="mytable" class="mytable table table-striped table-bordered" cellspacing="0" width="100%"><thead><tr>';
    headers.forEach(function(header) {
      tableHtml += '<th>' + escapeHtml(header) + '</th>';
    });
    tableHtml += '</tr><tr class="column-filters">';
    headers.forEach(function(header) {
      tableHtml += '<th><input type="text" placeholder="filter" aria-label="filter ' + escapeHtml(header) + '" /></th>';
    });
    tableHtml += '</tr></thead><tbody></tbody></table>';
    tableContainer.innerHTML = tableHtml;
    mountMarkersDataTableV2(headers, dataRows, requestId);
  }, function() {
    if (requestId !== latestTableRequestId) {
      return;
    }
    hideTableAndShowMessage();
    hideTableLoading();
  });
}

function mountMarkersDataTableV2(headers, dataRows, requestId) {
  setTimeout(function() {
    try {
      if (requestId !== latestTableRequestId) {
        return;
      }

      var $ = jQuery.noConflict();
      if (!$.fn.DataTable) {
        return;
      }

      if ($.fn.DataTable.isDataTable('#mytable')) {
        $('#mytable').DataTable().destroy();
      }

      var columnDefs = headers.map(function(header) {
        return { title: header };
      });

      var dataTable = $('#mytable').DataTable({
        destroy: true,
        deferRender: true,
        processing: true,
        orderCellsTop: true,
        autoWidth: false,
        pageLength: 10,
        lengthMenu: [[10, 25, 50, 100], [10, 25, 50, 100]],
        paging: true,
        pagingType: 'simple_numbers',
        searching: true,
        info: true,
        order: [[1, 'desc']],
        dom: '<"markers-table-toolbar"f>rt<"markers-table-footer"lip>',
        data: dataRows,
        columns: columnDefs,
        scrollX: true,
        language: {
          search: 'Search:',
          lengthMenu: 'Show _MENU_',
          info: 'Showing _START_ to _END_ of _TOTAL_ entries',
          infoEmpty: 'Showing 0 to 0 of 0 entries',
          paginate: {
            previous: 'Prev',
            next: 'Next'
          }
        },
        initComplete: function() {
          var api = this.api();
          var headerRows = api.table().header().rows;
          var filterRow = headerRows && headerRows.length > 1 ? headerRows[1] : null;

          if (filterRow) {
            api.columns().every(function(colIdx) {
              var column = this;
              var input = $('input', filterRow.cells[colIdx]);
              input.off('keyup change').on('keyup change', function() {
                if (column.search() !== this.value) {
                  column.search(this.value).draw();
                }
              });
            });
          }

          if ($.fn.dataTable && $.fn.dataTable.Buttons) {
            new $.fn.dataTable.Buttons(dataTable, {
              buttons: [
                {
                  extend: 'csvHtml5',
                  text: 'csv',
                  title: null,
                  filename: function() {
                    return buildDownloadFileName();
                  }
                },
                {
                  extend: 'pdfHtml5',
                  text: 'pdf',
                  title: buildDownloadFileName(),
                  filename: function() {
                    return buildDownloadFileName();
                  }
                }
              ]
            });
            dataTable.buttons().container().prependTo($(dataTable.table().container()).find('.markers-table-toolbar'));
          } else if (latestResolvedTableUrl) {
            $(dataTable.table().container()).find('.markers-table-toolbar').prepend(
              '<a class="dt-button" href="' + escapeHtml(latestResolvedTableUrl) + '" download="' + escapeHtml(buildDownloadFileName()) + '.csv">csv</a>'
            );
          }

          hideTableLoading();
        }
      });

      dataTable.page.len(10).draw(false);
    } catch (error) {
      console.error('Error initializing markers DataTable:', error);
      hideTableLoading();
    }
  }, 50);
}

document.addEventListener('DOMContentLoaded', function() {
    var buttonA = document.getElementById('buttonA');
    var buttonB = document.getElementById('buttonB');
    buttonA.click();
    // 设置按钮 A 为选中状态
    buttonA.classList.add('active');
    buttonB.classList.remove('active');
  });
  var activeButton = null;
  function changeOrder(button) {
    var sentenceElement = document.getElementById("sentence");
    var buttonA = document.getElementById('buttonA');
    var buttonB = document.getElementById('buttonB');
    var contentContainer = document.getElementById('contentContainer');
    var clickMessageContainer = document.getElementById('clickMessageContainer');
    
    if (button === 'A') {
      buttonA.classList.add('active');
      buttonB.classList.remove('active');
      activeButton = buttonA;
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEGs)</b> of selected cell type compared to others in the selected region.';
      selectedButton = button;
      originalOrder = true;
      resetSelectBoxes();
      resetAllSelectionOnModeChange('A');
      // Step1切换时隐藏结果
      contentContainer.style.display = 'none';
      clickMessageContainer.style.display = 'block';
    } else if (button === 'B') {
      buttonA.classList.remove('active');
      buttonB.classList.add('active');
      activeButton = buttonB;
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEGs)</b> of selected region compared to others in the selected cell type.';
      selectedButton = button;
      originalOrder = false;
      resetSelectBoxes();
      resetAllSelectionOnModeChange('B');
      // Step1切换时隐藏结果
      contentContainer.style.display = 'none';
      clickMessageContainer.style.display = 'block';
    }
 }   
  function resetAllSelectionOnModeChange(mode) {
    if (mode === 'A' && selectedCellType === 'All' && cellTypeOptions.length) {
      selectedCellType = cellTypeOptions[0];
      var cellTypeCards = document.querySelectorAll('.celltype-card');
      cellTypeCards.forEach(function(card, index) {
        card.classList.toggle('selected', index === 0);
      });
    } else if (mode === 'B' && selectedRegion === 'All' && regionOptions.length) {
      selectedRegion = regionOptions[0];
      var regionCards = document.querySelectorAll('.region-card');
      regionCards.forEach(function(card, index) {
        card.classList.toggle('selected', index === 0);
      });
    }
    updateAllButtonStates();
    updateSelectedOptions();
  }

  function resetSelectBoxes() {
    var regionContainer = document.getElementById('regionSelectionContainer');
    var cellTypeContainer = document.getElementById('cellTypeSelectionContainer');
    
    if (originalOrder) {
      // By Region: Region first, then Cell Type
      regionContainer.parentNode.insertBefore(regionContainer, cellTypeContainer);
    } else {
      // By Cell Type: Cell Type first, then Region
      cellTypeContainer.parentNode.insertBefore(cellTypeContainer, regionContainer);
    }
    updateAllButtonStates();
  }
  
  function showResults() {
    var contentContainer = document.getElementById('contentContainer');
    var clickMessageContainer = document.getElementById('clickMessageContainer');
    
    // Show content container and hide click message
    contentContainer.style.display = 'block';
    clickMessageContainer.style.display = 'none';
    updateSelectionSummary();
    
    // Load image and table (they have their own loading indicators)
    displaySelectedImage();
    renderMarkersTableV3();
  }
  
  function toggleContent() {
    // This function is now replaced by showResults
    showResults();
  }


</script>

<script>
function showImage0(photoName) {
    var photoElement = document.getElementById('photo');
    photoElement.src = photoName;
    photoElement.alt = photoName;
  }
</script>
<style>
  .image-container {
    max-width: 100%;
    max-height: 100%;
    background-color: none;
    justify-content: center;
    align-items: center;
    box-shadow: none;
  }
  
  .image-container img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
  .container {
  /* background-color: #f0f0f0; */ /* 设置背景颜色为您想要的颜色值 */
  box-shadow: 0 0 2px grey;
  border-radius: 10px; /* 设置边框圆角的半径，可以根据需要进行调整 */
  padding: 10px; /* 可选：添加内边距以增加内容与边框之间的间距 */
}
.markers-description { 
  font-weight: 600;
  box-shadow: 0 0 0px grey;
  padding: 0px;
}
  #buttonA, #buttonB {
      font-size: 17px; /* Increase font size */
      /* padding: 15px 30px; /* Increase padding */
      margin: 5px; /*Add some margin*/
      width: 150px; /*Set button width  */
      height: 38px; /* Set button height */
      /* cursor: pointer;
      border: none;
      background-color: #00528e; /* Change background color */
      /* color: white; Change text color */
      /* border-radius: 5px; Add border radius  */
    }
    /* #buttonA:hover, #buttonB:hover {
      background-color: #00528e; Change background color on hover */
    /* } */
</style>
<style>
    .photo-card {
/*         width: 200px;
        height: 200px; */
        border: 10px solid #ccc; 
        overflow: hidden;
        border-radius: 50%;
        position: relative;
        background-size: cover;
 /*        display: flex;  
        justify-content: right; /* 水平居中对齐 */
        /* align-items: right;  */
    }
    .photo-card:hover img {
        transform: scale(1.1);
    }
    .photo-card img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.3s;
    }
    .photo-card.clicked {
        border-color: #00528e;
    }
</style>
</body>
<style>
    .btn-primary {
      font-weight: normal; /* 确保文本不加粗 */
      font-size: 17px;    /* 设置文本字体大小 */
    }
  </style>
