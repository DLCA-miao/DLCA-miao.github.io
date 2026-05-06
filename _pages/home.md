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
<div class="home-intro-block">
<p class="text-center home-intro-title" style="color:#00528e;">Developmental Lung Cell Atlas</p>
<p class="text-center home-intro-text">This website provides a comprehensive, up-to-date lung cell atlas by systematically curating and integrating single-cell transcriptomic datasets from over 200 publications across the human lifespan. The atlas covers the majority of anatomical regions of the upper and lower respiratory tracts in both health and disease. It provides a valuable resource for the lung community and beyond, and enables cross-conditional comparisons of respiratory cell types.</p>
</div>
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
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/dev_stage.png" alt="Slide 1" class="home-carousel-image"/>
</div>
<div class="item ">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/F1_main_B.svg" alt="Slide 2" class="home-carousel-image"/>
</div>
 <div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/F1_E1_c.svg" alt="Slide 2" class="home-carousel-image"/>
</div>
<div class="item">
<img src="{{ site.url }}{{ site.baseurl }}/images/homePage/F1_E1_f.png" alt="Slide 3" class="home-carousel-image"/>
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

.home-intro-block {
  max-width: 1040px;
  margin: 0 auto 28px;
}

.home-intro-title {
  font-size: 40px;
  line-height: 1.2;
  margin-bottom: 18px;
}

.home-intro-text {
  font-size: 20px;
  line-height: 1.8;
  margin: 0 auto;
  color: #334155;
}

/* Statistics Section Styles */
.stats-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
  padding: 24px 20px;
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
  border-radius: 16px;
  width: 250px;
  transition: all 0.3s ease;
  box-shadow: 0 12px 28px rgba(0, 82, 142, 0.08);
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

.home-carousel-image {
  width: 100%;
  max-width: 2000px;
  height: 300px;
  object-fit: cover;
  border-radius: 16px;
  display: block;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .home-intro-block {
    margin-bottom: 20px;
  }

  .home-intro-title {
    font-size: 28px;
    line-height: 1.3;
    margin-bottom: 12px;
  }

  .home-intro-text {
    font-size: 16px;
    line-height: 1.7;
  }

  .stats-container {
    flex-direction: column;
    padding: 10px 0 0;
    gap: 12px;
    margin-bottom: 22px;
  }
  
  .stat-item {
    width: 100%;
    min-width: auto;
    padding: 14px 16px;
    border-radius: 14px;
  }
  
  .stat-number {
    font-size: 28px;
  }

  .home-carousel-image {
    height: 300px;
    border-radius: 0%;
  }
}
</style>



<br/>
<p class="text-center home-umap-title" style="color:#00528e;">The UMAP of Developmental Lung Cell Atlas</p>
<div class="container">
<div class="row" >
<div class="image-container">
<img id="photo" src="{{ site.url }}{{ site.baseurl }}/images/homePage/umap.svg" alt="Default Photo" class="home-umap-image">
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
  .home-umap-title {
    font-size: 30px;
    line-height: 1.3;
    margin-bottom: 18px;
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

  .home-umap-image {
    max-height: 600px;
    border-radius: 16px;
  }

  @media (max-width: 768px) {
    .home-umap-title {
      font-size: 24px;
      line-height: 1.4;
      margin-bottom: 14px;
    }

    .home-umap-image {
      max-height: 320px;
      border-radius: 12px;
    }
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


