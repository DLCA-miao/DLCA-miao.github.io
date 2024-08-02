---
title: "Developmental Lung Cell Atlas - Home"
layout: homelay
excerpt: "Developmental Lung Cell Atlas - Developmental Lung Data Centre: Facilitating Developmental Lung Research With Big Data"
sitemap: true
permalink: /
---
<!-- <div class="container"> -->
<br>
<br>
<p class="text-center" style="color:#587B39; font-size:40px;">Developmental Lung Cell Atlas</p>
<p class="text-center" style="font-size:20px;">The database offer a comprehensive lung development atlas that covers all stages from embryonic development to adulthood. The database hope this atlas will contribute to advancements and breakthroughs in the field of lung development research.</p>
<div class="wrapper box_style">
<div class="well" style="border: 0px solid #C9C9C9; background-color: #fff;">
<section class="sectiontitle"> 
<div>
<div markdown="0" id="carousel" class="carousel slide" data-ride="carousel" data-interval="4000" data-pause="hover" >
    <!-- Menu -->
<ol class="carousel-indicators">
<li data-target="#carousel" data-slide-to="0" class="active"></li>
<li data-target="#carousel" data-slide-to="1"></li>
<li data-target="#carousel" data-slide-to="2"></li>
<li data-target="#carousel" data-slide-to="3"></li>
<li data-target="#carousel" data-slide-to="4"></li>
<li data-target="#carousel" data-slide-to="5"></li>        
</ol>

<div class="carousel-inner" markdown="0">
<div class="item active">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure1.svg" alt="Slide 1" style=" width:1150px; height:300px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<div class="item ">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure2.png" alt="Slide 2" style=" width:1150px; height:300px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
 <div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure3.png" alt="Slide 2" style=" width:1000px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<!-- <div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure1.svg" alt="Slide 3" style="width:1000px; object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure1.svg" alt="Slide 4" style=" width:1000px; object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_figure1.svg" alt="Slide 4" style=" width:1000px; object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>  -->
</div>
<a class="left carousel-control" href="#carousel" role="button" data-slide="prev">
<span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
<span class="sr-only">Previous</span>
</a>
<a class="right carousel-control" href="#carousel" role="button" data-slide="next">
<span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
<span class="sr-only">Next</span>
</a>
</div>
<br>
</div>
<!-- style -->
<style>
.wrapper.box_style.line {
border-width: 0;
}
</style>



<br/>
<p class="text-center" style="color:#587B39; font-size:30px;">The UMAP of Developmental Lung Cell Atlas</p>
<div class="container">
<div class="row" >
<div class="image-container">
<img id="photo" src="{{ site.url }}{{ site.baseurl }}/images/homePage/home_umap.png" alt="Default Photo" style="height: 600px; width=600px">
</div>
</div>
</div>

<!-- <h3>Cite us </h3>
<p>Chen, Xinyue & Huang, Yin & Huang, Ziliang & Xu, Lahong & Huang, Liangfeng & Ye, Mingli & You, Renke & Zhang, Xuegong & Miao, Zhichao*. (2023). Brain Cell Atlas: An Integrative Ensemble of Cell Transcriptomes Across Human Brain Regions. 10.21203/rs.3.rs-3221500/v1.</p>
<br/> -->

<h3 style="color:#587B39">Cite us </h3>
<div class="left-aligned" style="width: 100%;">
Chen, Xinyue & Huang, Yin & Huang, Ziliang & Xu, Lahong & Huang, Liangfeng & Ye, Mingli & You, Renke & Zhang, Xuegong & Miao, Zhichao*. <br>
<strong style="color:#587B39;font-weight: bold">Brain Cell Atlas: An Integrative Ensemble of Cell Transcriptomes Across Human Brain Regions. 10.21203/rs.3.rs-3221500/v1.</strong><br>
<!-- <a> Unpublished</a> -->
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    var adultButton = document.querySelector('.col-lg-4:nth-child(1) .card-clickable');
    adultButton.click();
  });
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
</style>
<style>
    .photo-card {
/*         width: 350px;
        height: 350px; */
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
<script>
  var clickedCard = null;

  function handleClick(card) {
    if (clickedCard !== null) {
      clickedCard.classList.remove("clicked");
    }

    card.classList.add("clicked");
    clickedCard = card;
  }
</script>

<style>
    .custom-column {
        margin: 0 10px; /* 设置列之间的间距 */
        text-align: center
    }
</style>