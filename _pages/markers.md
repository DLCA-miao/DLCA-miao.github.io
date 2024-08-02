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
        background-color: #587B39;
        background-color: #587B39;
        background-color: #587B39;
        color: rgba(255,255,255,0.9);
		    cursor: pointer;
        }
	</style>

<!-- <p class="text-center" style="color:#587B39; font-size:20px; "> (This page shows the differentially expressed genes (DEGs) according to the regions/cell types)</p> -->
<!-- <div class="container">
<p><b>Step1</b> Click below to select a target dataset for analysis.</p>
<div class="row" style="display: flex; justify-content: space-between;">
<div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Adult',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/adult-brain.png" class="rounded-circle" />
</div> -->
<!-- <div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #587B39;">
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
<b style="font-size: 24px; color: #587B39;">
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
<b style="font-size: 24px; color: #587B39;">
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
<b style="font-size: 24px; color: #587B39;">
ORGANOID
</b>
</p>
</div> -->
<!-- </div>
</div>
</div> -->
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
  <select id="selectBox1" style="width: 200px; margin: 0 10px" onchange="handleSelectChange()"></select>
  <select id="selectBox2" style="width: 200px; margin: 5px" onchange="handleSelectChange()"></select>
  <!-- <button type="button" class="btn btn-primary btn-sm" onclick="toggleContent();displaySelectedImage();displaySelectedTable();">Markers</button> -->
  <button type="button" class="btn btn-primary btn-sm" style="text-transform: capitalize;" onclick="toggleContent();displaySelectedImage();displaySelectedTable();">Markers</button>
</div>
<br/>
<div id="contentContainer" style="display: none;">
<div class="container" style="box-shadow: 0 0 2px;">
<div class="image-container">
<b>Result</b> Volcano Plot.
<img id="selectedImage" src="" alt="Selected Image">
</div>
</div>
<br/>
<div class="container">
<b>Result</b> The table of DEGs.
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
<p id="clickMessageContainer" style="display: block;">Please click</p>
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
    background-color: #587B39; 
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
/*   .table-container {
    max-height: 500px; 
    overflow-y: auto;
  } */
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
  var selectBox1 = document.getElementById('selectBox1');
  var selectBox2 = document.getElementById('selectBox2');
  document.addEventListener('DOMContentLoaded', function() {
    loadInitialData();
  });
  function loadInitialData() {
    // 加载 RegionDEG.json 并填充 selectBox1
    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/RegionDEG.json')
      .then(response => response.json())
      .then(data => {
        // 假设我们只关心第一个键的值
        var firstKey = Object.keys(data)[0];
        var options = data[firstKey] || []; // 使用空数组如果 data[firstKey] 未定义
        updateSelectBoxOptions('selectBox1', options);
        handleSelectChange(); // 确保选中第一个选项
      })
      .catch(error => {
        console.error('Error loading RegionDEG.json:', error);
      });
    // 加载 CellTypeDEG.json 并填充 selectBox2
    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/CellTypeDEG.json')
      .then(response => response.json())
      .then(data => {
        // 假设我们只关心第一个键的值
        var firstKey = Object.keys(data)[0];
        var options = data[firstKey] || []; // 使用空数组如果 data[firstKey] 未定义
        updateSelectBoxOptions('selectBox2', options);
        handleSelectChange(); // 确保选中第一个选项
      })
      .catch(error => {
        console.error('Error loading CellTypeDEG.json:', error);
      });
    displaySelectedImage();
  }
  function handleSelectChange() {
    var selectBox1 = document.getElementById('selectBox1');
    var selectBox2 = document.getElementById('selectBox2');
    var option1 = selectBox1.options[selectBox1.selectedIndex].value;
    var option2 = selectBox2.options[selectBox2.selectedIndex].value;
    selectedOptions = [option1, option2];
    resetDisplay();
    displaySelectedImage();
    displaySelectedTable();
  }
  function resetDisplay() {
      var contentContainer = document.getElementById('contentContainer');
      var clickMessageContainer = document.getElementById('clickMessageContainer');
      contentContainer.style.display = 'none';
      clickMessageContainer.style.display = 'block';
    }
function displaySelectedImage() {
  if (selectedOptions.length === 2) {
    var imageName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '.png';
    var imagePath;
    if (selectedButton === 'A') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByRegion/Volcano/png/' + imageName;
    } else if (selectedButton === 'B') {
      imagePath = 'https://data.braincellatlas.org/mock/volcano/markers/ByCellType/Volcano/png/' + imageName;
    } else {
      console.error('Invalid button selection:', selectedButton);
      return; // 退出函数
    }
    console.log('Image path:', imagePath); // 调试信息
    var imageElement = document.getElementById('selectedImage');
    if (imageElement) {
      // 处理图片加载成功
      imageElement.onload = function() {
        console.log('Image loaded successfully:', imagePath);
        var errorMessage = document.getElementById('errorMessage');
        if (errorMessage) {
          errorMessage.remove();
        }
        imageLoaded = true; // 图片加载成功
      };
      // 处理图片加载错误
      imageElement.onerror = function() {
        console.error('Failed to load image:', imagePath);
        imageElement.src = ''; // 清空src属性
        imageElement.alt = '';
        displayErrorMessage('No region or cell type in this dataset');
        imageLoaded = false; // 图片加载失败
      };
      // 设置图片路径和样式
      imageElement.src = imagePath;
      imageElement.style.width = '500px'; // 设置宽度
      imageElement.style.height = 'auto'; // 高度自动调整
      imageElement.style.display = 'block'; // 设置图片为块级元素
      imageElement.style.margin = '0 auto'; // 图片居中
    } else {
      console.error('Element with id "selectedImage" not found.');
    }
  } else {
    console.log('Please select the necessary options.');
    hideTableAndShowMessage(); // 当没有图片展示时，隐藏表格并显示 "No table" 消息
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
  clearTableAndMessage();
  if (!imageLoaded) {
    console.log('No image to show.');
    hideTableAndShowMessage();
    return;
  }
  if (selectedOptions.length === 2) {
    var tableName;
    var tablePath;
    // 根据 selectedButton 来生成表格文件名和路径
    if (selectedButton === 'A') {
      tableName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/ByRegion/' + tableName;
    } else if (selectedButton === 'B') {
      tableName = 'Atlas' + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/mock/volcano/ByCellType/' + tableName;
    } else {
      console.log('Please select an image and options.');
      hideTableAndShowMessage(); // 结束函数的执行，并显示 "No table" 消息
      return; // 结束函数的执行
    }
    console.log('Table Path:', tablePath);
    var xhr = new XMLHttpRequest();
    xhr.open('GET', tablePath, true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4 && xhr.status === 200) {
        var csvData = xhr.responseText;
        console.log('CSV Data:', csvData);
        // 检查是否有 "No figure to show" 消息
        var errorMessage = document.getElementById('errorMessage');
        if (errorMessage && errorMessage.textContent === 'No the region or cell type in this dataset') {
          hideTableAndShowMessage(); // 隐藏表格并显示 "No table" 消息
          return;
        }
        var tableContainer = document.getElementById('csvTableContainer');
        // 解析 CSV 数据
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
            // 去掉每个单元格内容的引号
            var cellContent = cells[j].replace(/^"(.*)"$/, '$1');
            tableHtml += '<td>' + cellContent + '</td>';
          }
          tableHtml += '</tr>';
        }
        tableHtml += `</tbody>
        </table>`;
        // 清除 "No table" 消息
        var noTableMessage = document.getElementById('noTableMessage');
        if (noTableMessage) {
          noTableMessage.remove();
        }
        tableContainer.innerHTML = tableHtml;
        // 初始化表格并按第二列排序
        initializeDataTable();
      }
    };
    xhr.send();
  } else {
    console.log('Please select the necessary options.');
    hideTableAndShowMessage(); // 隐藏表格并显示 "No table" 消息
  }
}
jQuery( document ).ready(function( $ ) {
        $(document).ready( function () {
        $.noConflict();
        var table = $('#mytable').DataTable();
        });
})
function initializeDataTable() {
  jQuery(document).ready(function($) {
    $.noConflict();
    $('#mytable').DataTable({
      "order": [[1, "asc"]] // 默认按第二列（索引1）升序排序
    });
  });
}
function clearTableAndMessage() {
  // 清除表格内容
  var tableContainer = document.getElementById('csvTableContainer');
  tableContainer.innerHTML = '';
  // 显示 "No table" 消息
  var noTableMessage = document.getElementById('noTableMessage');
  if (!noTableMessage) {
    noTableMessage = document.createElement('div');
    noTableMessage.id = 'noTableMessage';
    noTableMessage.textContent = 'No the region or cell type in this dataset';
    noTableMessage.style.textAlign = 'center';
    tableContainer.appendChild(noTableMessage);
  }
}
function updateSelectBoxOptions(selectBoxId, options) {
    var selectBox = document.getElementById(selectBoxId);
    selectBox.innerHTML = generateOptionsHtml(options);
    if (options.length > 0) {
        selectBox.value = options[0]; // 默认选中第一个选项
    }
  }
  function generateOptionsHtml(options) {
    var optionsHtml = '';
    for (var i = 0; i < options.length; i++) {
      optionsHtml += '<option value="' + options[i] + '">' + options[i] + '</option>';
    }
    return optionsHtml;
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
    if (button === 'A') {
      buttonA.classList.add('active');
      buttonB.classList.remove('active');
      activeButton = buttonA;
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEGs)</b> of selected cell type compared to others in the selected region.';
      selectedButton = button;
      originalOrder = true;
      resetSelectBoxes();
    } else if (button === 'B') {
      buttonA.classList.remove('active');
      buttonB.classList.add('active');
      activeButton = buttonB;
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEGs)</b> of selected region compared to others in the selected cell type.';
      selectedButton = button;
      originalOrder = false;
      resetSelectBoxes();
      resetDisplay();
    }
 }   
  function resetSelectBoxes() {
    if (originalOrder) {
      selectBox1.parentNode.insertBefore(selectBox1, selectBox2);
    } else {
      selectBox2.parentNode.insertBefore(selectBox2, selectBox1);
    }
  }
  function toggleContent() {
    var contentContainer = document.getElementById('contentContainer');
    var clickMessageContainer = document.getElementById('clickMessageContainer');
    if (contentContainer.style.display === 'none') {
      contentContainer.style.display = 'block';
      clickMessageContainer.style.display = 'none';
    } else {
      contentContainer.style.display = 'none';
      clickMessageContainer.style.display = 'block';
    }
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
  #buttonA, #buttonB {
      font-size: 17px; /* Increase font size */
      /* padding: 15px 30px; /* Increase padding */
      margin: 5px; /*Add some margin*/
      width: 150px; /*Set button width  */
      height: 38px; /* Set button height */
      /* cursor: pointer;
      border: none;
      background-color: #587B39; /* Change background color */
      /* color: white; Change text color */
      /* border-radius: 5px; Add border radius  */
    }
    /* #buttonA:hover, #buttonB:hover {
      background-color: #587B39; Change background color on hover */
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
        border-color: #587B39;
    }
</style>
</body>
<style>
    .btn-primary {
      font-weight: normal; /* 确保文本不加粗 */
      font-size: 17px;    /* 设置文本字体大小 */
    }
  </style>