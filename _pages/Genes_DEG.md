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
<b style="font-size: 24px; color: #00528e">
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
<b style="font-size: 24px; color: #00528e">
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
<b style="font-size: 24px; color: #00528e">
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
<b style="font-size: 24px; color: #00528e">
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
        border-color: #00528e;
    }
</style>

<div class="container genes-deg-panel">
<p class="text-left" style="color:#00528e; font-size:20px; ">The section shows the differentially expressed genes (DEGs) of regions in a cell type.</p>

<p><b> Select the target Cell type.</b></p>
  <b style="font-size: 24px; color: #00528e">Celltype</b>
  <br>
  <select id="selectBox1" class="genes-deg-select" selectedIndex="0"></select>
  <br/>
  <div id="imageContainer"></div> <!-- 新增的div用于展示图片 -->
</div>

<br>
<div class="container genes-deg-panel">
<p class="text-left" style="color:#00528e; font-size:20px; ">The section shows the differentially expressed genes (DEGs) of cell types in a region.</p>

<p><b>Select the target Region.<b></p>
  <b style="font-size: 24px; color: #00528e">Region</b>
  <br>
  <select id="selectBox2" class="genes-deg-select" selectedIndex="0"></select>
  <br/>
  <div id="imageContainer1"></div> <!-- 新增的div用于展示图片 -->
</div>
<br/>
<!-- lightbox 由 JS 动态创建，避免 Markdown 将 img/button 转义为代码块 -->
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
  #imageContainer,
  #imageContainer1 {
    cursor: zoom-in;
  }
  #imageContainer img,
  #imageContainer1 img {
    cursor: zoom-in;
    pointer-events: auto;
  }
  .deg-image-lightbox {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 9999;
    overflow: hidden;
  }
  .deg-image-lightbox.active {
    display: block;
  }
  .deg-lightbox-backdrop {
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.92);
  }
  .deg-lightbox-viewport {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    cursor: grab;
    z-index: 1;
  }
  .deg-lightbox-viewport.is-dragging {
    cursor: grabbing;
  }
  .deg-lightbox-viewport img {
    max-width: 100vw;
    max-height: 100vh;
    width: auto;
    height: auto;
    object-fit: contain;
    border-radius: 0;
    box-shadow: none;
    transform-origin: center center;
    user-select: none;
    -webkit-user-drag: none;
    pointer-events: none;
  }
  .deg-lightbox-toolbar {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
    display: flex;
    gap: 8px;
    background: rgba(0, 0, 0, 0.65);
    padding: 6px 10px;
  }
  .deg-lightbox-toolbar button {
    color: #fff;
    background: transparent;
    border: 1px solid rgba(255, 255, 255, 0.45);
    min-width: 40px;
    height: 32px;
    padding: 0 10px;
    cursor: pointer;
    font-size: 18px;
    line-height: 1;
    border-radius: 0;
  }
  .deg-lightbox-toolbar button:hover {
    background: rgba(255, 255, 255, 0.12);
  }
  .deg-image-lightbox-close {
    position: absolute;
    top: 12px;
    right: 20px;
    z-index: 2;
    color: #fff;
    font-size: 36px;
    line-height: 1;
    cursor: pointer;
    user-select: none;
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

  .genes-deg-panel {
    width: 100%;
  }

  .genes-deg-select {
    width: min(100%, 400px) !important;
    max-width: 100%;
  }

  @media (max-width: 767px) {
    .genes-deg-panel {
      padding: 12px;
    }

    .genes-deg-select {
      width: 100% !important;
    }

    .genes-deg-panel p[style*="font-size:20px"] {
      font-size: 16px !important;
      line-height: 1.6;
    }
  }
</style>

<script>
  var degZoomState = { scale: 1, x: 0, y: 0, minScale: 0.5, maxScale: 6 };
  var degDragState = { active: false, startX: 0, startY: 0, originX: 0, originY: 0 };
  var degLightboxInitialized = false;

  function applyDegZoom() {
    var lightboxImage = document.getElementById('degLightboxImage');
    if (!lightboxImage) return;
    lightboxImage.style.transform = 'translate(' + degZoomState.x + 'px, ' + degZoomState.y + 'px) scale(' + degZoomState.scale + ')';
  }

  function resetDegZoom() {
    degZoomState.scale = 1;
    degZoomState.x = 0;
    degZoomState.y = 0;
    applyDegZoom();
  }

  function degZoomAt(clientX, clientY, newScale) {
    var viewport = document.getElementById('degLightboxViewport');
    if (!viewport) return;
    newScale = Math.min(degZoomState.maxScale, Math.max(degZoomState.minScale, newScale));
    var rect = viewport.getBoundingClientRect();
    var cx = clientX - rect.left - rect.width / 2;
    var cy = clientY - rect.top - rect.height / 2;
    var ratio = newScale / degZoomState.scale;
    degZoomState.x = cx - (cx - degZoomState.x) * ratio;
    degZoomState.y = cy - (cy - degZoomState.y) * ratio;
    degZoomState.scale = newScale;
    applyDegZoom();
  }

  function degZoomIn(e) {
    if (e) e.stopPropagation();
    var viewport = document.getElementById('degLightboxViewport');
    if (!viewport) return;
    var rect = viewport.getBoundingClientRect();
    degZoomAt(rect.left + rect.width / 2, rect.top + rect.height / 2, degZoomState.scale + 0.25);
  }

  function degZoomOut(e) {
    if (e) e.stopPropagation();
    var viewport = document.getElementById('degLightboxViewport');
    if (!viewport) return;
    var rect = viewport.getBoundingClientRect();
    degZoomAt(rect.left + rect.width / 2, rect.top + rect.height / 2, degZoomState.scale - 0.25);
  }

  function degZoomReset(e) {
    if (e) e.stopPropagation();
    resetDegZoom();
  }

  function createDegLightbox() {
    if (document.getElementById('degImageLightbox')) return;

    var lightbox = document.createElement('div');
    lightbox.id = 'degImageLightbox';
    lightbox.className = 'deg-image-lightbox';

    var backdrop = document.createElement('div');
    backdrop.className = 'deg-lightbox-backdrop';
    backdrop.addEventListener('click', closeDegImageLightbox);

    var closeBtn = document.createElement('span');
    closeBtn.className = 'deg-image-lightbox-close';
    closeBtn.innerHTML = '&times;';
    closeBtn.addEventListener('click', closeDegImageLightbox);

    var toolbar = document.createElement('div');
    toolbar.className = 'deg-lightbox-toolbar';

    var zoomOutBtn = document.createElement('button');
    zoomOutBtn.type = 'button';
    zoomOutBtn.title = '缩小';
    zoomOutBtn.textContent = '−';
    zoomOutBtn.addEventListener('click', degZoomOut);

    var zoomResetBtn = document.createElement('button');
    zoomResetBtn.type = 'button';
    zoomResetBtn.title = '重置';
    zoomResetBtn.textContent = '100%';
    zoomResetBtn.addEventListener('click', degZoomReset);

    var zoomInBtn = document.createElement('button');
    zoomInBtn.type = 'button';
    zoomInBtn.title = '放大';
    zoomInBtn.textContent = '+';
    zoomInBtn.addEventListener('click', degZoomIn);

    toolbar.appendChild(zoomOutBtn);
    toolbar.appendChild(zoomResetBtn);
    toolbar.appendChild(zoomInBtn);

    var viewport = document.createElement('div');
    viewport.id = 'degLightboxViewport';
    viewport.className = 'deg-lightbox-viewport';

    var lightboxImage = document.createElement('img');
    lightboxImage.id = 'degLightboxImage';
    lightboxImage.alt = '';
    lightboxImage.draggable = false;
    viewport.appendChild(lightboxImage);

    lightbox.appendChild(backdrop);
    lightbox.appendChild(closeBtn);
    lightbox.appendChild(toolbar);
    lightbox.appendChild(viewport);
    document.body.appendChild(lightbox);
  }

  function initDegLightboxInteractions() {
    if (degLightboxInitialized) return;
    var viewport = document.getElementById('degLightboxViewport');
    if (!viewport) return;
    degLightboxInitialized = true;

    viewport.addEventListener('wheel', function(e) {
      e.preventDefault();
      var delta = e.deltaY > 0 ? -0.15 : 0.15;
      degZoomAt(e.clientX, e.clientY, degZoomState.scale + delta);
    }, { passive: false });

    viewport.addEventListener('mousedown', function(e) {
      if (e.button !== 0) return;
      e.preventDefault();
      degDragState.active = true;
      degDragState.startX = e.clientX;
      degDragState.startY = e.clientY;
      degDragState.originX = degZoomState.x;
      degDragState.originY = degZoomState.y;
      viewport.classList.add('is-dragging');
    });

    document.addEventListener('mousemove', function(e) {
      if (!degDragState.active) return;
      degZoomState.x = degDragState.originX + (e.clientX - degDragState.startX);
      degZoomState.y = degDragState.originY + (e.clientY - degDragState.startY);
      applyDegZoom();
    });

    document.addEventListener('mouseup', function() {
      if (!degDragState.active) return;
      degDragState.active = false;
      viewport.classList.remove('is-dragging');
    });

    viewport.addEventListener('dblclick', function(e) {
      e.preventDefault();
      if (degZoomState.scale > 1) {
        resetDegZoom();
      } else {
        degZoomAt(e.clientX, e.clientY, 2);
      }
    });
  }

  function openDegImageLightbox(src) {
    var lightbox = document.getElementById('degImageLightbox');
    var lightboxImage = document.getElementById('degLightboxImage');
    if (!lightbox || !lightboxImage || !src) return;
    initDegLightboxInteractions();
    lightboxImage.src = src;
    resetDegZoom();
    lightbox.classList.add('active');
    document.body.style.overflow = 'hidden';
  }

  function closeDegImageLightbox() {
    var lightbox = document.getElementById('degImageLightbox');
    var lightboxImage = document.getElementById('degLightboxImage');
    if (!lightbox || !lightboxImage) return;
    lightbox.classList.remove('active');
    lightboxImage.src = '';
    resetDegZoom();
    degDragState.active = false;
    document.body.style.overflow = '';
  }

  document.addEventListener('keydown', function(e) {
    var lightbox = document.getElementById('degImageLightbox');
    if (!lightbox || !lightbox.classList.contains('active')) return;
    if (e.key === 'Escape') {
      closeDegImageLightbox();
    } else if (e.key === '+' || e.key === '=') {
      degZoomIn();
    } else if (e.key === '-') {
      degZoomOut();
    } else if (e.key === '0') {
      degZoomReset();
    }
  });

  function bindDegImagePreviewClick(imageContainer) {
    if (!imageContainer || imageContainer.dataset.degClickBound === 'true') return;
    imageContainer.dataset.degClickBound = 'true';
    imageContainer.addEventListener('click', function(e) {
      var img = e.target && e.target.tagName === 'IMG' ? e.target : imageContainer.querySelector('img');
      if (img && img.src) {
        openDegImageLightbox(img.src);
      }
    });
  }

  document.addEventListener('DOMContentLoaded', function() {
    createDegLightbox();
    initDegLightboxInteractions();

    setupImageSelection('selectBox1', 'imageContainer', 'CellTypeDEG.json', 'ByCellType', 'imageIdContainer', '80%', '100%');
    setupImageSelection('selectBox2', 'imageContainer1', 'RegionDEG.json', 'ByRegion', 'imageIdContainer1', '80%', '100%');

    function setupImageSelection(selectBoxId, imageContainerId, dataFile, imageFolder, imageIdContainerId, width, height) {
      var selectBox = document.getElementById(selectBoxId);
      var imageContainer = document.getElementById(imageContainerId);
      var imageElement = document.createElement('img');
      imageContainer.appendChild(imageElement);
      bindDegImagePreviewClick(imageContainer);

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
            // document.getElementById(imageIdContainerId).textContent = 'Atlas: ' + firstKey;
             var idContainer = document.getElementById(imageIdContainerId);
            if (idContainer) {
              idContainer.textContent = 'Atlas: ' + firstKey;
            }
            handleSelectChange(selectBox, imageElement, imageFolder, width, height);
          }
        })
        .catch(error => {
          console.error('Error loading ' + dataFile + ':', error);
        });
    }

    function handleSelectChange(selectBox, imageElement, imageFolder, width, height) {
      console.log('Selected option:', imageElement);
      var selectedOption = selectBox.options[selectBox.selectedIndex].value;
      displaySelectedImage(selectedOption, imageElement, imageFolder, width, height);
    }

    function displaySelectedImage(optionValue, imageElement, imageFolder, width, height) {
      if (optionValue) {
        var encodedOption = encodeURIComponent(optionValue);
        var imageName = encodedOption + '.png';
        var imagePath = 'https://data.braincellatlas.org/mock/volcano/figures/stacked_violin_/' + imageFolder + '/' + imageName;

        if (imageElement) {
          imageElement.src = imagePath;
          imageElement.style.width = '100%';
          imageElement.style.maxWidth = width;
          imageElement.style.height = height;
          imageElement.style.display = 'block';
          imageElement.style.margin = '0 auto';
          imageElement.title = '点击查看大图，滚轮缩放，拖拽平移';
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
