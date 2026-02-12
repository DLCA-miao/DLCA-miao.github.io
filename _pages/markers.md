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
<div class="markers-description container" style="">
The section shows the differentially expressed genes (DEGs) of the target region or the target Cell type.
</div>
<br/>
<div class="container" style="box-shadow: 0 0 2px;">
<p><b>Step1</b> Click the buttons to show the differentially expressed genes (DEGs) of the target region or the target Cell type.</p>
  <button id="buttonA" onclick="changeOrder('A')">By Region</button>
  <button id="buttonB" onclick="changeOrder('B')">By Cell type</button>
</div>
  <br/>

<div class="container" style="box-shadow: 0 0 2px;">
<p><b>Step2</b> Select the target Cell type/Region to show the DEGs.</p>
  <p id="sentence"></p>
  
  <!-- Region Selection Cards -->
  <div id="regionSelectionContainer" class="selection-container">
    <p class="selection-label">Select Region:</p>
    <div id="regionCards" class="card-grid"></div>
  </div>
  
  <!-- Cell Type Selection Cards -->
  <div id="cellTypeSelectionContainer" class="selection-container">
    <p class="selection-label">Select Cell Type:</p>
    <div id="cellTypeCards" class="card-grid-celltype"></div>
  </div>
  
  <button type="button" class="btn btn-primary btn-sm" style="text-transform: capitalize;" onclick="showResults();">Markers</button>
</div>
<br/>
<div id="contentContainer" style="display: none;">
<!-- Volcano Plot Section -->
<div class="container" style="box-shadow: 0 0 2px;">
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
<div class="container">
<b>Result</b> The table of DEGs.
<!-- Table Loading Indicator -->
<div id="tableLoadingIndicator" style="display: none; text-align: center; padding: 20px;">
  <div class="spinner"></div>
  <p>Loading table data...</p>
</div>
<div id="csvTableContainer" style="max-height: 500px; overflow-y: auto; box-shadow: 0 0 2px;"></div>
</div>
</div>
<script>
jQuery( document ).ready(function( $ ) {
        $(document).ready( function () {
        $.noConflict();
        var table = $('#mytable').DataTable();
        });
})
</script>

<div class="container" style="box-shadow: 0 0 2px;">
<p id="clickMessageContainer" style="display: block;">Please click on the <b>Markers</b> button above.</p>
</div>


<style>
    .custom-column {
        margin: 0 50px; /* 设置列之间的间距 */
    }
</style>
<style>
  #csvTableContainer {
    max-height: 500px;
    overflow-y: auto;
  }

  /* 将表格头部固定 */
  #csvTableContainer thead {
    position: sticky;
    top: 0;
    background-color: white;
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
</style>
<script type="text/javascript"  src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>
<div id="csvTableContainer"></div>
<script>
  var regionOptions = [];
  var cellTypeOptions = [];
  var selectedRegion = null;
  var selectedCellType = null;
  var selectedOptions = [];
  var imageLoaded = false; // 添加图片加载状态变量
  var selectedButton = 'A'; // 添加选中按钮状态变量
  var originalOrder = true; // 添加顺序状态变量
  
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
    }
  }
  
  function createRegionCards(options) {
    var container = document.getElementById('regionCards');
    container.innerHTML = '';
    
    options.forEach(function(option, index) {
      var card = document.createElement('div');
      card.className = 'region-card';
      if (index === 0) {
        card.classList.add('selected');
        selectedRegion = option;
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
    var imageName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '.png';
    var imagePath;
    if (selectedButton === 'A') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/Volcano/png/' + imageName;
    } else if (selectedButton === 'B') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/Volcano/png/' + imageName;
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
      imageElement.style.width = '500px'; // 设置宽度
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
      tableName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/ByRegion/' + tableName;
    } else if (selectedButton === 'B') {
      tableName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/ByCellType/' + tableName;
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
          
          var rows = csvData.split('\n');
          var tableHtml = '<table id="mytable" class="mytable table table-striped table-bordered" cellspacing="0" width="100%">';
          var headerHtml = `<thead>
        <tr>
            <th>genes</th>
            <th>avg_log2FC</th>
            <th>p_val</th>
            <th>p_val_adj</th>
        </tr>
        </thead>
        <tbody>`;
          tableHtml += headerHtml;
          for (var i = 1; i < rows.length; i++) {
            var cells = rows[i].split(',');
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
jQuery( document ).ready(function( $ ) {
        $(document).ready( function () {
        $.noConflict();
        var table = $('#mytable').DataTable();
        });
})
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
      // Step1切换时隐藏结果
      contentContainer.style.display = 'none';
      clickMessageContainer.style.display = 'block';
    }
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
  }
  
  function showResults() {
    var contentContainer = document.getElementById('contentContainer');
    var clickMessageContainer = document.getElementById('clickMessageContainer');
    
    // Show content container and hide click message
    contentContainer.style.display = 'block';
    clickMessageContainer.style.display = 'none';
    
    // Load image and table (they have their own loading indicators)
    displaySelectedImage();
    displaySelectedTable();
  }
  
  function toggleContent() {
    // This function is now replaced by showResults
    showResults();
  }


</script>

<script>
  $(document).ready( function () {
    $.noConflict();
    var table = $('#mytable').DataTable();
} );
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