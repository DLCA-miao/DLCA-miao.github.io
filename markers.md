---
title: "Ribo centre - Markers"
layout: homelay
excerpt: "Ribo centre -- Markers"
permalink: /markers_b/
---
<head>
	<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/jquery.dataTables.min.css">
	<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/2.2.3/css/buttons.dataTables.min.css">
</head>
<script type="text/javascript"  src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
<script type="text/javascript"  src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
<script type="text/javascript"  src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>


<div class="container">
<b style="font-size: 24px;">
ATLAS
</b>
<div class="shadow p-3 mb-5 bg-white rounded row">

<div class="col-lg-3 text-center">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Adult',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/nose-pharynx.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px;">
ADULT BRAIN
</b>
</p>
</div>
</div>

<div class="col-lg-3 text-center">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Fetal',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/airway.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px;">
FETAL BRAIN
</b>
</p>
</div>
</div>


<div class="col-lg-3 text-center">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Organoid',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/lung.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px;">
TUMOR
</b>
</p>
</div>
</div>


<div class="col-lg-3 text-center">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Tumour',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/airway.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px;">
ORGANOID
</b>
</p>
</div>
</div>

</div>
</div>
<br/>
<div class="container">
  <button id="buttonA" onclick="changeOrder('A')">By Region</button>
  <button id="buttonB" onclick="changeOrder('B')">By CellType</button>
  <br/>
  <p id="sentence"></p>
  <br/>
  <label for="sel1">单选下拉菜单:</label>
  <select id="selectBox1" onchange="handleSelectChange()"></select>
  <select id="selectBox2" onchange="handleSelectChange()"></select>
  <button type="button" class="btn btn-primary btn-sm" onclick="toggleContent();displaySelectedImage();displaySelectedTable();">Markers</button>
</div>
<br/>
<div id="contentContainer" style="display: none;">
<div class="container">
<div class="image-container">
VOLCANO PLOT
<img id="selectedImage" src="" alt="Selected Image">
</div>
</div>
<br/>
<div class="container">
<div id="csvTableContainer"></div>
</div>
</div>

<div class="container">
<p id="clickMessageContainer" style="display: block;">Please click</p>
</div>



<style>
   /* 设置固定宽度 */
  #selectBox1, #selectBox2 {
    width: 400px; /* 这里可以根据需要调整宽度 */
  }
  .active {
    background-color: #EC7102; 
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

<script>
  var selectedImageId = null;
  var selectedOptions = [];
  var selectedButton = null;
  var selectBox1 = document.getElementById('selectBox1');
  var selectBox2 = document.getElementById('selectBox2');
  var originalOrder = true;
  var clickedCard = null;
  document.addEventListener('DOMContentLoaded', function() {
    var adultButton = document.querySelector('.col-lg-3:nth-child(1) .card-clickable');
    adultButton.click();
  });

  function handleClick(imageId,card) {
    if (clickedCard !== null) {
    clickedCard.classList.remove("clicked");
  }
    card.classList.add("clicked");
    clickedCard = card;
    selectedImageId = imageId;
    selectedOptions = [];

    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/RegionDEG.json')
      .then(response => response.json())
      .then(data => {
        var options = data[imageId];
        updateSelectBoxOptions('selectBox1', options);
      })
      .catch(error => {
        console.error('Error:', error);
      });

    fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/CellTypeDEG.json')
      .then(response => response.json())
      .then(data => {
        var options = data[imageId];
        updateSelectBoxOptions('selectBox2', options);
      })
      .catch(error => {
        console.error('Error:', error);
      });
  }

  function handleSelectChange() {
    var selectBox1 = document.getElementById('selectBox1');
    var selectBox2 = document.getElementById('selectBox2');

    var option1 = selectBox1.options[selectBox1.selectedIndex].value;
    var option2 = selectBox2.options[selectBox2.selectedIndex].value;

    selectedOptions = [option1, option2];
  }

function displaySelectedImage() {
  if (selectedImageId !== null && selectedOptions.length === 2) {
    var imageName;
    if (selectedButton === 'A') {
      imageName = selectedImageId + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '.png';
    var imagePath = 'https://data.braincellatlas.org/volcano/VolcanoByRegion/' + imageName;
    } else if (selectedButton === 'B') {
      imageName = selectedImageId + '_' + encodeURIComponent(selectedOptions[1]) + '_' + encodeURIComponent(selectedOptions[0]) + '.png';
    var imagePath = 'https://data.braincellatlas.org/volcano/VolcanoByCellType/' + imageName;
    }
    /* var imagePath = '{{ site.url }}{{ site.baseurl }}/images/markerPage/volcano/' + imageName; */
    // 在此处显示照片，例如：
    var imageElement = document.getElementById('selectedImage');
    imageElement.src = imagePath;
    console.log('Selected Image:', imagePath);
  } else {
    console.log('Please select an image and options.');
  }
}

function sortTable(columnIndex) {
    // TODO: Add sorting logic based on the columnIndex
  }

function displaySelectedTable() {
  if (selectedImageId !== null && selectedOptions.length === 2) {
    var tableName;
    var tablePath;

    if (selectedButton === 'A') {
      tableName = selectedImageId + '_' + encodeURIComponent(selectedOptions[0]) + '_' + encodeURIComponent(selectedOptions[1]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/markersByRegion/' + tableName;
    } else if (selectedButton === 'B') {
      tableName = selectedImageId + '_' + encodeURIComponent(selectedOptions[1]) + '_' + encodeURIComponent(selectedOptions[0]) + '_cell_type.csv';
      tablePath = 'https://data.braincellatlas.org/markersByCellType/' + tableName;
    } else {
      console.log('Please select an image and options.');
      return; // 结束函数的执行
    }

    console.log('Table Path:', tablePath);

    var xhr = new XMLHttpRequest();
    xhr.open('GET', tablePath, true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4 && xhr.status === 200) {
        var csvData = xhr.responseText;
        console.log('CSV Data:', csvData);

        var tableContainer = document.getElementById('csvTableContainer');

        // 解析 CSV 数据
        var rows = csvData.split('\n');
        var tableHtml = '<table id="mytable" class="table table-hover table-striped table-bordered" cellspacing="0" width="100%">';
        var headerHtml = `<thead>
        <tr>
            <th onclick="sortTable(0)">Name</th>
            <th onclick="sortTable(1)">Ligand</th>
            <th onclick="sortTable(2)">Description</th>
            <th onclick="sortTable(3)">Discovery</th>
            <th onclick="sortTable(4)">Rfam-name</th>
            <th onclick="sortTable(5)">Rfam-ID</th>
        </tr>
        </thead>
        <tbody>`;
        tableHtml += headerHtml;
        for (var i = 0; i < rows.length; i++) {
          var cells = rows[i].split(',');
          tableHtml += '<tr>';
          for (var j = 0; j < cells.length; j++) {
              tableHtml += '<td name="td' + j + '">' + cells[j] + '</td>';
          }
          tableHtml += '</tr>';
        }
        tableHtml += '</table>';

        // 将表格插入到页面中
        tableContainer.innerHTML = tableHtml;
      }
    };
    xhr.send();
  } else {
    console.log('Please select an image and options.');
  }
}


  function updateSelectBoxOptions(selectBoxId, options) {
    var selectBox = document.getElementById(selectBoxId);
    selectBox.innerHTML = generateOptionsHtml(options);
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
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEG)</b> of selected cell type compared to others in the selected brain region.';
      selectedButton = button;
      originalOrder = true;
      resetSelectBoxes();
    } else if (button === 'B') {
      buttonA.classList.remove('active');
      buttonB.classList.add('active');
      activeButton = buttonB;
      sentenceElement.innerHTML = 'Search for <b>differentially expressed genes (DEG)</b> of selected brain region compared to others in the selected cell type.';
      selectedButton = button;
      originalOrder = false;
      resetSelectBoxes();
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
  box-shadow: 0 0 15px grey;
  border-radius: 10px; /* 设置边框圆角的半径，可以根据需要进行调整 */
  padding: 10px; /* 可选：添加内边距以增加内容与边框之间的间距 */
}
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
        border-color: #EE993A;
    }
</style>

<script>
  var tables = [];
    var currentSheet = 'sheet1';
     $(document).ready(function() {
    $.noConflict();
    tables.push($('#cfttable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));

    tables.push($('#rnadetable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));

    tables.push($('#rnapretable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));
    tables.push($('#smtable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));
    tables.push($('#eletable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));


    
    tables.push($('#amintable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));
    tables.push($('#sugtable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));
    tables.push($('#tboxtable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));
    tables.push($('#othtable').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy', 'csv', 'excel', 'pdf', 'print'
      ]
    }));    
    // Hide the search box for DataTables
      $('#cfttable_filter').css('display', 'none');
      $('#rnadetable_filter').css('display', 'none');
      $('#rnapretable_filter').css('display', 'none');
       $('#smtable_filter').css('display', 'none');
      $('#eletable_filter').css('display', 'none');
      $('#amintable_filter').css('display', 'none');
      $('#sugtable_filter').css('display', 'none');
      $('#tboxtable_filter').css('display', 'none');
      $('#othtable_filter').css('display', 'none');
      
      // Show the initial sheet (sheet1) and hide others
    showSheet('sheet1');
    hideAllSheetsExcept('sheet1');
  });
  function sortTable(columnIndex) {
    // TODO: Add sorting logic based on the columnIndex
  }
function downloadExcel() {
  var selectElement = document.getElementById('downloadOptions');
  var selectedValue = selectElement.value;

  // Check if a valid option was selected
  if (selectedValue !== '') {
    // Create a temporary link element with the download URL
    var link = document.createElement('a');
    link.href = selectedValue;
    link.download = selectedValue.split('/').pop(); // Set the filename to the last part of the URL
    document.body.appendChild(link);

    // Trigger a click event on the link to start the download
    link.click();

    // Remove the link from the DOM
    document.body.removeChild(link);
  }
}
	
	
	function showSheet(sheetId) {
    // Hide the current sheet
    if (currentSheet) {
        var currentSheetElement = document.getElementById(currentSheet);
        currentSheetElement.style.display = 'none';
    }

    // Show the selected sheet
    var sheet = document.getElementById(sheetId);
    sheet.style.display = 'block';

    // Update the current sheet
    currentSheet = sheetId;

    // Get all buttons
    var buttons = document.querySelectorAll('.button');

    // Remove clicked class from all buttons
    buttons.forEach(function(btn) {
        btn.classList.remove('clicked');
    });

    // Add clicked class to the clicked button using event.target
    event.target.classList.add('clicked');
}
    function hideAllSheetsExcept(sheetId) {
    var sheets = document.getElementsByClassName('sheet');
    for (var i = 0; i < sheets.length; i++) {
      var sheet = sheets[i];
      if (sheet.id !== sheetId) {
        sheet.style.display = 'none';
      }
    }
    }
    function showAllSheets() {
      var sheets = document.getElementsByClassName('sheet');
      for (var i = 0; i < sheets.length; i++) {
        sheets[i].style.display = 'block';
      }
    }
    function searchTables() {
      var keyword = $('#searchBox').val().toLowerCase();
      tables.forEach(function(table) {
        table.search(keyword).draw();
      });
      // Filter the sheets based on search results
    filterSheets();
  }

  function filterSheets() {
    var keyword = $('#searchBox').val().toLowerCase();
    var sheets = document.getElementsByClassName('sheet');

    for (var i = 0; i < sheets.length; i++) {
      var sheet = sheets[i];
      var table = tables[i];

      var displaySheet = false;

      table.rows().eq(0).each(function(index) {
        var row = table.row(index);
        var rowData = row.data().join(' ').toLowerCase();
        var display = rowData.includes(keyword) ? '' : 'none';
        row.nodes().to$().css('display', display);

        if (display !== 'none') {
          displaySheet = true;
        }
      });

      if (displaySheet) {
        $('#' + sheet.id).show();
      } else {
        $('#' + sheet.id).hide();
      }
    }
  }  
  </script>      
