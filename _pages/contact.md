---
title: "Developmental Lung Cell Atlas - Contact"
layout: gridlay
permalink: /contact/
---
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

<style>
  .contact-page {
    max-width: 1100px;
    margin: 0 auto;
  }

  .contact-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 20px;
    margin-bottom: 24px;
  }

  .contact-card {
    padding: 20px;
    border: 1px solid #d9e1ea;
    border-radius: 12px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.06);
    background: #fff;
    text-align: center;
  }

  .contact-card h3,
  .contact-card h4 {
    margin-top: 0;
  }

  .contact-card ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .contact-card li {
    line-height: 1.8;
    word-break: break-word;
  }

  .map-frame {
    width: 100%;
    height: 420px;
    border: 0;
    border-radius: 12px;
  }

  .map-wrap {
    margin-bottom: 24px;
  }
  
  .feedback-link {
  display: block;
  text-align: center;
  width: 100%;
  }
  .feedback-link img {
    width: min(100%, 400px);
    display: inline-block;
    margin: 0 auto;
  }

  @media (max-width: 991px) {
    .contact-grid {
      grid-template-columns: 1fr;
    }
  }

  @media (max-width: 767px) {
    .contact-card {
      padding: 16px;
    }

    .map-frame {
      height: 300px;
    }
  }
</style>

<br>
<div class="contact-page">
<div class="contact-grid">

<section class="contact-card">
  <h3><b>Shuo Feng</b></h3>
  <h4><b>Guangzhou Laboratory</b></h4>
  <p>International Bio-island,<br>Guangzhou, 510005, China</p>
  <ul>
    <li><a href="mailto:fengshuo@mail.ustc.edu.cn?subject=[Help]%20RCA"><i class="fa fa-envelope fa-fw"></i> fengshuo@mail.ustc.edu.cn</a></li>
  </ul>
</section>

<section class="contact-card">
  <h3><b>Zhichao (Chichau) Miao</b></h3>
  <h4><b>Guangzhou Laboratory</b></h4>
  <h4><b>Guangzhou Medical University</b></h4>
  <p>International Bio-island,<br>Guangzhou, 510005, China</p>
  <ul>
    <li><a href="mailto:miao_zhichao@gzlab.ac.cn?subject=[Help]%20RCA"><i class="fa fa-envelope fa-fw"></i> miao_zhichao@gzlab.ac.cn</a></li>
  </ul>
</section>
</div>

<div class="map-wrap">
<iframe
  class="map-frame"
  src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d3670.9607940189653!2d113.3728525!3d23.0618989!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x34025549978de655%3A0xbfef76e0d9d7b9!2z5bm_5bee55Sf54mp5bKb5Zu96ZmF5YWs5a-T!5e0!3m2!1sen!2skr!4v1716198561625!5m2!1sen!2skr"
  allowfullscreen>
</iframe>
</div>

<div>
<a class="feedback-link" href="https://docs.google.com/spreadsheets/d/1MnyUdtO2yXy3WoTDZlKiBMdRUiL7OgH9mc6PiWZsYDA/edit?usp=drive_link" target="_blank">
  <img src="{{ site.url }}{{ site.baseurl }}/images/helpPage/feedback.svg" alt="Feedback form">
</a>
</div>
</div>
