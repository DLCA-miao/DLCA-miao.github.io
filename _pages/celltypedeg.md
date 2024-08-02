---
title: "Brain Cell Atlas - CellTypeDEG"
layout: homelay
excerpt: "Brain Cell Atlas -- CellTypeDEG"
permalink: /celltypedeg1/
---
<p class="text-center" style="color:#587B39; font-size:20px; ">The page shows the differentially expressed genes (DEGs) of regions in a cell type.</p>
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

<div class="container" style="width: 800px">
<p><b>Step1</b> Select the target Cell type.</p>
  <b style="font-size: 24px; color: #587B39">Expression</b>
  <div id="imageIdContainer"></div>
  <br/>
  <b style="font-size: 24px; color: #587B39">Celltype</b>
  <br>
  <select id="selectBox1" style="width: 400px;" onchange="handleSelectChange();displaySelectedImage()" selectedIndex="0"></select>
  <br/>
  <div id="imageContainer"></div> <!-- 新增的div用于展示图片 -->
</div>
<br/>

<!-- <div id="imageIdContainer"></div> -->
<style>
  /* 设置固定宽度 */
  #selectBox1 {
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
  box-shadow: 0 0 15px grey;
  border-radius: 10px; /* 设置边框圆角的半径，可以根据需要进行调整 */
  padding: 10px; /* 可选：添加内边距以增加内容与边框之间的间距 */
}
  .imageIdContainer{
    box-shadow: 0 0 15px grey;
    border-radius: 10px; 
    padding: 10px; 
  }
</style>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    var selectBox1 = document.getElementById('selectBox1');
    var imageContainer = document.getElementById('imageContainer');
    var imageElement = document.createElement('img');
    imageContainer.appendChild(imageElement);  // 将图片元素添加到指定的div

    // 确保选择框变化时触发 handleSelectChange 函数
    selectBox1.addEventListener('change', function() {
      handleSelectChange();
      displaySelectedImage(selectBox1.value);
    });

    loadInitialData();

    function loadInitialData() {
      fetch('{{ site.url }}{{ site.baseurl }}/js/genepage/CellTypeDEG.json')
        .then(response => response.json())
        .then(data => {
          // 获取数据中的第一个键
          var firstKey = Object.keys(data)[0];
          var options = data[firstKey] || []; // 使用空数组如果 data[firstKey] 未定义

          // 更新 selectBox1 的选项
          updateSelectBoxOptions(selectBox1, options);

          if (options.length > 0) {
            selectBox1.selectedIndex = 0;
            document.getElementById('imageIdContainer').textContent = 'Atlas: ' + firstKey;
            handleSelectChange(); // 默认选中第一个选项并显示图片
            displaySelectedImage(selectBox1.options[0].value); // 默认选中第一个选项并显示图片
          }
        })
        .catch(error => {
          console.error('Error loading CellTypeDEG.json:', error);
        });
    }

    function handleSelectChange() {
      var option1 = selectBox1.options[selectBox1.selectedIndex].value;
      displaySelectedImage(option1);
    }

    function displaySelectedImage(optionValue) {
      if (optionValue) {
        var encodedOption = encodeURIComponent(optionValue);
        var imageName = 'Atlas'+'_'+encodedOption + '.png'; // 假设图片名仅由选项值组成
        var imagePath = '{{ site.url }}{{ site.baseurl }}/images/markerPage/volcano/figures/stacked_violin_/ByCellType/' + imageName;
        
        if (imageElement) {
          imageElement.src = imagePath;
          console.log('Selected Image:', imagePath);
          // 设置图片路径和样式
          imageElement.src = imagePath;
          imageElement.style.width = '500px'; // 设置宽度
          imageElement.style.height = 'auto'; // 高度自动调整
          imageElement.style.display = 'block'; // 设置图片为块级元素
          imageElement.style.margin = '0 auto'; // 图片居中
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