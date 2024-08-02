---
title: "Ribo centre - Portrait"
layout: piclay
excerpt: "Ribo centre -- Portrait"
permalink: /portrait_test/
---
<div class="image-gallery">
<div class="main-image">
<img src="../assets/lung/全景图.png" alt="Main Image" id="mainImage">
</div>
<div class="thumbnails">
<div class="thumbnail" onclick="highlightImage(1)">
<img src="../assets/lung/nostrils.png" alt="Thumbnail 1">
<div class="caption">Thumbnail 1</div>
</div>
<div class="thumbnail" onclick="highlightImage(2)">
<img src="../assets/lung/lung.png"" alt="Thumbnail 2">
<div class="caption">Thumbnail 2</div>
</div>
    <!-- 更多缩略图 -->
</div>
</div>

<style>
.image-gallery {
display: flex;
}
.main-image img {
max-width: 100%;
}
.thumbnail {
cursor: pointer;
}
.thumbnail img {
width: 100px; /* 小图片的宽度 */
height: auto; /* 自动调整高度 */
}
.thumbnail .caption {
display: none; /* 注释默认隐藏 */
}
.thumbnail.active img {
opacity: 1; /* 激活的小图片不透明 */
}
.thumbnail:hover .caption {
display: block; /* 鼠标悬停时显示注释 */
}
</style>

<script>
function highlightImage(index) {
const thumbnails = document.querySelectorAll('.thumbnail');
thumbnails.forEach(thumbnail => thumbnail.classList.remove('active'));
thumbnails[index - 1].classList.add('active');
const mainImage = document.getElementById('mainImage');
mainImage.src = `large_image${index}.jpg`;
}
</script>



linkTo(a) {const t = `../cirro/index.html#q={"dataset":"scVI","embeddings":[{"name":"X_umap","dimensions":2}],"layers":[],"activeFeature":{"name":"organ","type":"obsCat","embeddingKey":"organ_X_umap"},"q":[{"id":"organ","type":"obsCat"}],"datasetFilter":{"organ":{"value":["${a}"],"operation":"in"}},"embeddingLabels":["celltype"]}`; window.location.href = t;}

function linkTo(a) {const targetUrl = `../cirro/index.html#q={"dataset":"scVI","embeddings":[{"name":"X_umap","dimensions":2}],"layers":[],"activeFeature":{"name":"organ","type":"obsCat","embeddingKey":"organ_X_umap"},"q":[{"id":"organ","type":"obsCat"}],"datasetFilter":{"organ":{"value":["${a}"],"operation":"in"}},"embeddingLabels":["celltype"]}`;const iframe = document.querySelector('.rounded-iframe');iframe.src = targetUrl;}