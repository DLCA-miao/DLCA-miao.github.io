---
title: "Developmental Lung Cell Atlas - DEG"
layout: homelay
excerpt: "Developmental Lung Cell Atlas -- DEG"
permalink: /deg/
---
<!-- <div class="container"> -->
<!--b style="font-size: 24px; color: #BF5701">
ATLAS
</b-->
<!--div class="shadow p-3 mb-5 bg-white rounded row"-->
<!-- <p><b>Step1</b> Click below to select a target dataset for analysis.</p>
<div class="row" style="display: flex; justify-content: space-between;">
<div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Adult',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/adult-brain.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #587B39">
ADULT BRAIN
</b>
</p>
</div>
</div> -->

<!-- <div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Fetal',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/fetal-brain.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #587B39">
FETAL BRAIN
</b>
</p>
</div>
</div>
<div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Tumour',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/tumour-brain.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #587B39">
TUMOR
</b>
</p>
</div>
</div>
<div class="col-lg-3 text-center custom-column">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Organoid',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/drganoid-brain.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #587B39">
ORGANOID
</b>
</p>
</div>
</div> -->


<!--div class="col-lg-3 text-center">
<div class="img-circle card photo-card card-clickable" onclick="handleClick('Tumour',this)">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/airway.png" class="rounded-circle" />
</div>
<div>
<p class="text-center" style="margin-top: 16px;">
<b style="font-size: 24px; color: #BF5701">
ORGANOID
</b>
</p>
</div>
</div-->
<!-- 
</div>
</div> -->


<style>
    .custom-column {
        margin: 0 50px; /* 设置列之间的间距 */
    }
</style>

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
    .photo-card {
        border: 10px solid #ccc; 
        overflow: hidden;
        border-radius: 50%;
        position: relative;
        background-size: cover;
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

<div class="container" style>
<p class="text-left" style="color:#587B39; font-size:20px; ">The section shows the differentially expressed genes (DEGs) of regions in a cell type.</p>

<p><b> Select the target Cell type.</b></p>
  <b style="font-size: 24px; color: #587B39">Celltype</b>
  <br>
  <select id="selectBox1" style="width: 400px;" onchange="handleSelectChange();displaySelectedImage()" selectedIndex="0"></select>
  <br/>
  <div id="imageContainer"></div> <!-- 新增的div用于展示图片 -->
</div>

<br>
<div class="container">
<p class="text-left" style="color:#587B39; font-size:20px; ">The section shows the differentially expressed genes (DEGs) of cell types in a region.</p>

<p><b>Select the target Region.<b></p>
  <b style="font-size: 24px; color: #587B39">Region</b>
  <br>
  <select id="selectBox2" style="width: 400px;" onchange="handleSelectChange();displaySelectedImage()" selectedIndex="0"></select>
  <br/>
  <div id="imageContainer1"></div> <!-- 新增的div用于展示图片 -->
</div>
<br/>
<!-- <div id="imageIdContainer"></div> -->
<style>
  /* 设置固定宽度 */
  #selectBox1 {
    width: 400px; /* 这里可以根据需要调整宽度 */
    height: 38px
  }
  #selectBox2 {
    width: 400px; /* 这里可以根据需要调整宽度 */
    height: 38px
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
  .container {
  /* background-color: #f0f0f0; */ /* 设置背景颜色为您想要的颜色值 */
  box-shadow: 0 0 2px;
  border-radius: 10px; /* 设置边框圆角的半径，可以根据需要进行调整 */
  padding: 10px; /* 可选：添加内边距以增加内容与边框之间的间距 */
  border: 0px;
}
  .imageIdContainer{
    box-shadow: 0 0 15px grey;
    border-radius: 10px; 
    padding: 10px; 
  }
  .imageIdContainer1{
    box-shadow: 0 0 15px grey;
    border-radius: 10px; 
    padding: 10px; 
  }
</style>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    setupImageSelection('selectBox1', 'imageContainer', 'CellTypeDEG.json', 'ByCellType', 'imageIdContainer', '500px', '100%');
    setupImageSelection('selectBox2', 'imageContainer1', 'RegionDEG.json', 'ByRegion', 'imageIdContainer1', '800px', 'auto');

    function setupImageSelection(selectBoxId, imageContainerId, dataFile, imageFolder, imageIdContainerId, width, height) {
      var selectBox = document.getElementById(selectBoxId);
      var imageContainer = document.getElementById(imageContainerId);
      var imageElement = document.createElement('img');
      imageContainer.appendChild(imageElement);

      selectBox.addEventListener('change', function() {
        handleSelectChange(selectBox, imageElement, imageFolder, width, height);
      });

      loadInitialData(dataFile, selectBox, imageElement, imageFolder, imageIdContainerId, width, height);
    }

    function loadInitialData(dataFile, selectBox, imageElement, imageFolder, imageIdContainerId, width, height) {
      fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/' + dataFile)
        .then(response => response.json())
        .then(data => {
          var firstKey = Object.keys(data)[0];
          var options = data[firstKey] || [];

          updateSelectBoxOptions(selectBox, options);

          if (options.length > 0) {
            selectBox.selectedIndex = 0;
            document.getElementById(imageIdContainerId).textContent = 'Atlas: ' + firstKey;
            handleSelectChange(selectBox, imageElement, imageFolder, width, height);
          }
        })
        .catch(error => {
          console.error('Error loading ' + dataFile + ':', error);
        });
    }

    function handleSelectChange(selectBox, imageElement, imageFolder, width, height) {
      var selectedOption = selectBox.options[selectBox.selectedIndex].value;
      displaySelectedImage(selectedOption, imageElement, imageFolder, width, height);
    }

    function displaySelectedImage(optionValue, imageElement, imageFolder, width, height) {
      if (optionValue) {
        var encodedOption = encodeURIComponent(optionValue);
        var imageName = 'Atlas_' + encodedOption + '.png';
        var imagePath = 'https://data.braincellatlas.org/mock/volcano/figures/stacked_violin_/' + imageFolder + '/' + imageName;

        if (imageElement) {
          imageElement.src = imagePath;
          imageElement.style.width = width;
          imageElement.style.height = height;
          imageElement.style.display = 'block';
          imageElement.style.margin = '0 auto';
          console.log('Selected Image:', imagePath);
        }
      } else {
        console.log('Please select an image option.');
      }
    }

    function updateSelectBoxOptions(selectBox, options) {
      if (selectBox) {
        selectBox.innerHTML = generateOptionsHtml(options);
      }
    }

    function generateOptionsHtml(options) {
      var optionsHtml = '';
      for (var i = 0; i < options.length; i++) {
        optionsHtml += '<option value="' + options[i] + '">' + options[i] + '</option>';
      }
      return optionsHtml;
    }
  });
</script>