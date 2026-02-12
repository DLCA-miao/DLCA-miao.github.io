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
<p class="text-center" style="color:#00528e; font-size:40px;">Developmental Lung Cell Atlas</p>
<p class="text-center" style="font-size:20px;">The website offer a comprehensive lung development atlas that covers all stages from embryonic development to adulthood. The website hope this atlas will contribute to advancements and breakthroughs in the field of lung development research.</p>
<div class="wrapper box_style">
<div class="well" style="border: 0px solid #C9C9C9; background-color: #fff;">

<!-- Statistics Section -->
<div markdown="0" class="stats-container">
  <div class="stat-item">
    <div class="stat-icon">
      <img src="{{ site.url }}{{ site.baseurl }}/images/home-icon/publications.png" alt="Publications">
    </div>
    <div class="stat-content">
      <div class="stat-label">Publications</div>
      <div class="stat-number" data-target="225">0</div>
    </div>
  </div>
  
  <div class="stat-item">
    <div class="stat-icon">
      <img src="{{ site.url }}{{ site.baseurl }}/images/home-icon/cells.png" alt="Cells">
    </div>
    <div class="stat-content">
      <div class="stat-label">Cells</div>
      <div class="stat-number" data-target="18000000">0</div>
    </div>
  </div>
  
  <div class="stat-item">
    <div class="stat-icon">
      <img src="{{ site.url }}{{ site.baseurl }}/images/home-icon/samples.png" alt="Samples">
    </div>
    <div class="stat-content">
      <div class="stat-label">Samples</div>
      <div class="stat-number" data-target="3133">0</div>
    </div>
  </div>
  
  <div class="stat-item">
    <div class="stat-icon">
      <img src="{{ site.url }}{{ site.baseurl }}/images/home-icon/sampling locations.png" alt="Locations">
    </div>
    <div class="stat-content">
      <div class="stat-label">Locations</div>
      <div class="stat-number" data-target="34">0</div>
    </div>
  </div>
</div>

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
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/region_summary_gender_seq_donor_2.svg" alt="Slide 2" style=" width:1500px; height:300px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
 <div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/region_summary_gender_seq_donor_2_copy.svg" alt="Slide 2" style=" width:1500px;  height:300px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/donor_age_region_celnumber_heatmap_new2.svg" alt="Slide 3" style="width:2000px; height:300px;object-fit: cover;border-radius:0%;display: block; margin: 0 auto;"/>
</div>
<!--<div class="item">
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

/* Statistics Section Styles */
.stats-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px 20px;
  background: #ffffff;
  margin-bottom: 30px;
}

.stat-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 15px 20px;
  background: #dae3f5;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  width: 250px;
  transition: all 0.3s ease;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.stat-icon {
  margin-right: 20px;
  flex-shrink: 0;
  animation: iconPulse 2s ease-in-out infinite;
}

.stat-icon img {
  width: 40px;
  height: 40px;
  display: block;
}

@keyframes iconPulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.08);
  }
}

.stat-content {
  display: flex;
  border-left: 4px solid #666;
  padding-left: 20px;
  flex-direction: column;
  align-items: flex-start;
}

.stat-label {
  font-size: 14px;
  color: #000;
  font-weight: 500;
  margin-bottom: 5px;
  text-transform: capitalize;
}

.stat-number {
  font-size: 26px;
  font-weight: 600;
  color: #00528e;
  font-family: 'Arial', sans-serif;
  letter-spacing: 0.5px;
  line-height: 1;
}

@media (max-width: 768px) {
  .stats-container {
    flex-direction: column;
    padding: 20px 15px;
    gap: 15px;
  }
  
  .stat-item {
    width: 100%;
    min-width: auto;
  }
  
  .stat-number {
    font-size: 28px;
  }
}
</style>



<br/>
<p class="text-center" style="color:#00528e; font-size:30px;">The UMAP of Developmental Lung Cell Atlas</p>
<div class="container">
<div class="row" >
<div class="image-container">
<img id="photo" src="{{ site.url }}{{ site.baseurl }}/images/homePage/umap.svg" alt="Default Photo" style="height: 600px; width=600px">
</div>
</div>
</div>

<h3 style="color:#00528e">Cite us </h3>
<div class="left-aligned" style="width: 100%;">
Huang, L. et al. <strong style="color:#00528e;font-weight: bold">An integrated single-cell atlas of the human lung across the lifespan.</strong><br>
<!-- <a> Unpublished</a> -->
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    // Statistics counter animation
    function animateCounter(element, target, duration) {
      let start = 0;
      const increment = target / (duration / 16); // 60fps
      const isLargeNumber = target >= 1000000;
      
      const timer = setInterval(() => {
        start += increment;
        if (start >= target) {
          start = target;
          clearInterval(timer);
        }
        
        // Format number based on size
        let displayValue;
        if (isLargeNumber) {
          displayValue = (start / 1000000).toFixed(1) + 'M';
        } else if (start >= 1000) {
          displayValue = Math.floor(start).toLocaleString();
        } else {
          displayValue = Math.floor(start);
        }
        
        element.textContent = displayValue;
      }, 16);
    }
    
    // Intersection Observer for triggering animation when visible
    const observerOptions = {
      threshold: 0.3,
      rootMargin: '0px'
    };
    
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const statNumbers = document.querySelectorAll('.stat-number');
          statNumbers.forEach(stat => {
            const target = parseInt(stat.getAttribute('data-target'));
            animateCounter(stat, target, 2000); // 2 seconds animation
          });
          observer.unobserve(entry.target);
        }
      });
    }, observerOptions);
    
    const statsContainer = document.querySelector('.stats-container');
    if (statsContainer) {
      observer.observe(statsContainer);
    }
    
    // Original code
    var adultButton = document.querySelector('.col-lg-4:nth-child(1) .card-clickable');
    if (adultButton) {
      adultButton.click();
    }
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
        border-color: #00528e;
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
