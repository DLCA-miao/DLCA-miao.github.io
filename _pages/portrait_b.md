---
title: "Ribo centre - Portrait"
layout: piclay
excerpt: "Ribo centre -- Portrait"
permalink: /portrait_b/
---
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<style>
  .brain-wrap {
    position: relative;
    z-index: 2;
    width: 1000px;
    transform: scale(0.9);
    height: 700px;
    margin: 0 auto;
    transition: all 0.3s;
  }

  .brain-wrap #imgMap,
  .brain-wrap .img-bg,
  .brain-wrap .organ-img {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 0;
    height: 100%;
  }

  .brain-wrap .line {
    z-index: 99;
  }

  .brain-wrap #imgMap {
    z-index: 333;
  }

  .brain-wrap area {
    cursor: pointer;
  }

  .brain-wrap .nav-list {
    position: absolute;
    z-index: 999;
  }

  .brain-wrap .nav-list.nose-list {
    top: 150px;
    left: 179px;
  }

  .brain-wrap .nav-list.pharynx-list {
    top: 220px;
    left: 594px;
  }

  .brain-wrap .nav-list.airway-list {
    top: 420px;
    left: 690px;
  }

  .brain-wrap .nav-list.lungsub-list {
    top: 420px;
    left: 690px;
  }

  .brain-wrap .lung-nav {
    width: 100%;
  }

  .brain-wrap .lung-nav li {
    position: absolute;
    z-index: 999;
    font-size: 12px;
    background: #eff5ff;
    color: #406b9b;
    cursor: pointer;
    padding: 3px 4px;
    border-radius: 4px;
    min-width: 80px;
    text-align: center;
    border: 1px solid #d9e1f1;
    font-weight: bold;
    line-height: 1.2em;
  }

  .brain-wrap .lung-nav li:hover,
  .brain-wrap .lung-nav li.actived {
    background: #3a5c93;
    color: #fff;
  }

  .brain-wrap .lung-nav li#nav_1 {
    left: 125px;
    top: 234px;
  }

  .brain-wrap .lung-nav li#nav_2 {
    left: 731px;
    top: 271px;
  }

  .brain-wrap .lung-nav li#nav_3 {
    left: 912px;
    top: 451px;
  }

  .brain-wrap .lung-nav li#nav_4 {
    left: 912px;
    top: 520px;
  }

  .brain-wrap .lung-nav li#nav_Larynx {
    left: 239px;
    top: 330px;
  }

  .brain-wrap .lung-nav.nose-nav {
    background-size: auto 70%;
    width: 140px;
    height: 0px;
    position: relative;
  }

  .brain-wrap .lung-nav.nose-nav li {
    left: 60px;
  }

  .brain-wrap .lung-nav.nose-nav li.nav_1_0 {
    top: 68px;
  }

  .brain-wrap .lung-nav.nose-nav li.nav_1_1 {
    top: 99px;
  }

  .brain-wrap .lung-nav.nose-nav li.nav_1_2 {
    top: 170px;
  }

  .brain-wrap .lung-nav.pharynx-nav {
    background-size: auto 100%;
    width: 130px;
    height: 0px;
    position: relative;
  }

  .brain-wrap .lung-nav.pharynx-nav li {
    left: 10px;
  }

  .brain-wrap .lung-nav.pharynx-nav li.nav_2_0 {
    top: 19px;
  }

  .brain-wrap .lung-nav.pharynx-nav li.nav_2_1 {
    top: 50px;
  }

  .brain-wrap .lung-nav.pharynx-nav li.nav_2_2 {
    top: 81px;
  }

  .brain-wrap .lung-nav.pharynx-nav li.nav_2_3 {
    top: 126px;
  }

  .brain-wrap .lung-nav.airway-nav {
    min-width: 200px;
    height: 0px;
    position: relative;
  }

  .brain-wrap .lung-nav.airway-nav li {
    left: 82px;
  }

  .brain-wrap .lung-nav.airway-nav li.nav_3_0 {
    top: 0px;
  }

  .brain-wrap .lung-nav.airway-nav li.nav_3_1 {
    top: 30px;
  }

  .brain-wrap .lung-nav.airway-nav li.nav_3_2 {
    top: 60px;
  }

  .brain-wrap .lung-nav.lungsub-nav {
    min-width: 130px;
    height: 0px;
    position: relative;
  }

  .brain-wrap .lung-nav.lungsub-nav li {
    left: 82px;
  }

  .brain-wrap .lung-nav.lungsub-nav li.nav_4_0 {
    top: 90px;
  }

  .brain-wrap .lung-nav.lungsub-nav li.nav_4_1 {
    top: 120px;
  }
</style>

<div id="app">
<div class="brain-wrap" ref="brainwrap">
<!-- <img src="@/assets/brain/dark/brain-bg.png" alt="" height="100%" class="img-bg"> -->
<img src="../assets/lung/线.png" usemap="#Map" id="imgMap" />
<map name="Map" id="Map">
<!-- Nose -->
<!-- <area onclick="linFkTo('Nasal cavity', 'Nose and pharynx')" onmouseover="update('Nose', 'Nasal cavity')" -->
<area onclick="linkTo('Nasal cavity', 'Nose and pharynx')" onmouseover="update('Nose', 'Nasal cavity')"
title="Nasal cavity" coords="2788,1397,2751,1344,2587,1334,2514,1340,2380,1519,2469,1519,2525,1553,2793,1564"
shape="poly">
<area onclick="linkTo('Nostrils', 'Nose and pharynx')" onmouseover="update('Nose', 'Nostrils')" title="Nostrils"
coords="2492,1566,2413,1533,2413,1588" shape="poly">

<!-- Pharynx -->
<area onclick="linkTo('Nasal pharynx', 'Nose and pharynx')" o nmouseover="update('Pharynx', 'Nasal pharynx')"
title="Nasal pharynx" coords="2816,1441,2872,1474,2939,1497,2994,1642,2860,1631,2793,1564" shape="poly">
<area onclick="linkTo('Oropharynx', 'Nose and pharynx')" onmouseover="update('Pharynx', 'Oropharynx')"
title="Oropharynx" coords="2793,1671,2838,1738,2983,1716,2983,1649,2849,1638" shape="poly">
<area onclick="linkTo('Hypopharynx', 'Nose and pharynx')" onmouseover="update('Pharynx', 'Hypopharynx')"
title="Hypopharynx"
coords="3127,2169,3095,2185,3005,1904,2958,1861,2931,1782,2883,1824,2836,1803,2857,1750,2984,1739"
shape="poly">

<!-- Larynx -->
<area onclick="linkTo('Larynx')" onmouseover="update('Larynx')" title="Larynx"
coords="2905,1941,2942,1941,2973,1914,2920,1909" shape="poly">

<!-- Airway -->
<area onclick="linkTo('Trachea', 'Airway')" onmouseover="update('Airway', 'Trachea')" title="Trachea"
coords="3006,2748,3106,2748,3095,2212,2994,2223" shape="poly">
<area onclick="linkTo('Primary bronchus', 'Airway')" onmouseover="update('Airway', 'Primary bronchus')"
title="Primary bronchus"
coords="2994,2764,2950,2808,2961,2875,3017,2819,3095,2831,3207,2898,3251,2831,3117,2764" shape="poly">
<area onclick="linkTo('Bronchi', 'Airway')" onmouseover="update('Airway', 'Bronchi')" title="Bronchi"
coords="3240,2848,3296,2804,3307,2737,3363,2759,3419,2837,3441,2904,3408,3005,3508,3150,3430,3172,3341,3116,3240,3005"
shape="poly">

<!-- Lung -->
<area onclick="linkTo('all', 'Lung')" onmouseover="update('Lung')" title="Lung"
coords="2849,2399,2626,2690,2503,2969,2436,3461,2469,3505,2682,3416,2950,3315,2994,3215,2972,3025,3006,2902,2916,2846,2894,2734,2961,2701,2961,2545,2916,2411"
shape="poly">
<area onclick="linkTo('Bronchioles', 'Lung')" onmouseover="update('Lung', 'Bronchioles')" title="Bronchioles"
coords="3263,2721,3330,2710,3397,2755,3430,2833,3453,2911,3441,2978,3475,3056,3520,3146,3441,3179,3229,3034,3263,3112,3341,3168,3520,3235,3587,3235,3531,3079,3497,2799,3397,2676,3307,2554,3240,2609,3196,2676"
shape="poly">
<area onclick="linkTo('Alveoli', 'Lung')" onmouseover="update('Lung', 'Alveoli')" title="Alveoli"
coords="3184,2699,3207,2598,3251,2542,3318,2531,3385,2576,3419,2654,3453,2732,3520,2777,3531,2855,3542,2933,3542,3034,3587,3123,3609,3190,3620,3257,3553,3268,3453,3235,3363,3213,3296,3146,3229,3101,3218,3179,3263,3246,3330,3313,3397,3324,3475,3347,3564,3369,3631,3358,3687,3302,3676,3190,3631,3045,3620,2944,3587,2822,3542,2676,3464,2576,3385,2486,3229,2419,3151,2565"
shape="poly">
</map>
<!-- <img src="@/assets/brain/line.png" alt="" class="organ-img line"> -->
<div v-if="!activeBrain && !activeLabel">
<img src="../assets/lung/全景图.png" alt="" class="organ-img" />
</div>
<!-- 各个器官独立的图层 -->
<div class="Nose">
<!-- 鼻部全图层 -->
<img v-show="activeBrain == 'Nose' && activePart(null)" src="../assets/lung/全景图.png" alt="Nose"
class="organ-img">
<!-- 独立器官图层 -->
<img v-show="activePart('Nasal cavity')" src="../assets/lung/nasal cavity.png" alt="Nasal cavity"
class="organ-img">
<img v-show="activePart('Nostrils')" src="../assets/lung/nostrils.png" alt="Nostrils" class="organ-img">
</div>

<div class="Pharynx">
<!-- 喉部全图层 -->
<img v-show="activeBrain == 'Pharynx' && activePart(null)" src="../assets/lung/全景图.png" alt="Pharynx"
class="organ-img">
<!-- 独立器官图层 -->
<img v-show="activePart('Nasal pharynx')" src="../assets/lung/nasal pharynx.png" alt="Nasal pharynx"
class="organ-img">
<img v-show="activePart('Oropharynx')" src="../assets/lung/oropharynx.png" alt="Oropharynx" class="organ-img">
<img v-show="activePart('Hypopharynx')" src="../assets/lung/hypopharynx.png" alt="Hypopharynx"
class="organ-img">
</div>

<div class="Larynx">
<!-- 鼻部全图层 -->
<img v-show="activeBrain == 'Larynx' && activePart(null)" src="../assets/lung/larynx.png" alt="Larynx"
class="organ-img">
</div>

<div class="Airway">
<!-- 气道全图层 -->
<img v-show="activeBrain == 'Airway' && activePart(null)" src="../assets/lung/全景图.png" alt="Airway"
class="organ-img">
<!-- 独立器官图层 -->
<img v-show="activePart('Trachea')" src="../assets/lung/trachea.png" alt="Trachea" class="organ-img">
<img v-show="activePart('Primary bronchus')" src="../assets/lung/primary bronchus.png" alt="Primary bronchus"
class="organ-img">
<img v-show="activePart('Bronchi')" src="../assets/lung/bronchi.png" alt="Bronchi" class="organ-img">
</div>

<div class="Lung">
<!-- 肺部全图层 -->
<img v-show="activeBrain == 'Lung' && activePart(null)" src="../assets/lung/lung.png" alt="Lung"
class="organ-img">
<!-- 独立器官图层 -->
<img v-show="activePart('Bronchioles')" src="../assets/lung/bronchioles.png" alt="Bronchioles"
class="organ-img">
<img v-show="activePart('Alveoli')" src="../assets/lung/alveoli.png" alt="Alveoli" class="organ-img">
</div>

<!-- <ul class="lung-nav">
<li class="nav" id="nav_1" onclick="linkTo('Nose')" onmouseover="update('Nose')"
:class="activeBrain == 'Nose' ? 'actived' : ''">Nose</li>
<li class="nav" id="nav_2" onclick="linkTo('Pharynx')" onmouseover="update('Pharynx')"
:class="activeBrain == 'Pharynx' ? 'actived' : ''">Pharynx</li>
<li class="nav" id="nav_3" onclick="linkTo('Airway')" onmouseover="update('Airway')"
:class="activeBrain == 'Airway' ? 'actived' : ''">Airway</li>
<li class="nav" id="nav_4" onclick="linkTo('Lung')" onmouseover="update('Lung')"
:class="activeBrain == 'Lung' ? 'actived' : ''">Lung</li>
<li class="nav" id="nav_Larynx" onclick="linkTo('Larynx')" onmouseover="update('Larynx')"
:class="activeBrain == 'Larynx' ? 'actived' : ''">Larynx</li>
</ul> -->

<ul class="lung-nav">
  <li class="nav" id="nav_1" onclick="linkTo('Nose')" onmouseover="update('Nose')" 
  :class="activeBrain == 'Nose' ? 'actived' : ''">Nose</li>
  <li class="nav" id="nav_2" onclick="linkTo('Pharynx')" onmouseover="update('Pharynx')" 
  :class="activeBrain == 'Pharynx' ? 'actived' : ''">Pharynx</li>
  <li class="nav" id="nav_3" onclick="linkTo('Airway')" onmouseover="update('Airway')" 
  :class="activeBrain == 'Airway' ? 'actived' : ''">Airway</li>
  <li class="nav" id="nav_4" onclick="linkTo('Lung')" onmouseover="update('Lung')" 
  :class="activeBrain == 'Lung' ? 'actived' : ''">Lung</li>
  <li class="nav" id="nav_Larynx" onclick="linkTo('Larynx')" onmouseover="update('Larynx')" 
  :class="activeBrain == 'Larynx' ? 'actived' : ''">Larynx</li>
</ul>



<!-- Sub-navigation for specific organs if needed -->
<div class ="nav-list nose-list">
<ul class="lung-nav nose-nav">
<li v-for="(item, index) in noseNav" :key="item"
  :class="(`nav_1_${index}`) + ' ' + (activedLabel(item) ? 'actived ' : '')" onclick="linkTo(item)"
  onmouseover="update('Nose', item)">{{ item }}</li>
</ul>
</div>

<div class="nav-list pharynx-list">
<ul class="lung-nav pharynx-nav">
<li v-for="(item, index) in pharynxNav" :key="item"
  :class="(`nav_2_${index}`) + ' ' + (activedLabel(item) ? 'actived ' : '')" onclick="linkTo(item)"
  onmouseover="update('Pharynx', item)">{{ item }}</li>
</ul>
</div>

<div class="nav-list airway-list">
<ul class="lung-nav airway-nav">
<li v-for="(item, index) in airwayNav" :key="item"
  :class="(`nav_3_${index}`) + ' ' + (activedLabel(item) ? 'actived ' : '')" onclick="linkTo(item)"
  onmouseover="update('Airway', item)">{{ item }}</li>
</ul>
</div>

<div class="nav-list lungsub-list">
<ul class="lung-nav lungsub-nav">
<li v-for="(item, index) in lungSubNav" :key="item"
  :class="(`nav_4_${index}`) + ' ' + (activedLabel(item) ? 'actived ' : '')" onclick="linkTo(item)"
  onmouseover="update('Lung', item)">{{ item }}</li>
</ul>
</div>
</div>
</div>


<script>
  const app = Vue.createApp({
    name: "BrainArea",
    data() {
      return {
        showImg: "brain",
        activeBrain: null,
        activeLabel: null,
        activedMLabel: null,
        noseNav: ['Nasal cavity', 'Nostrils'],
        pharynxNav: ['Nasal pharynx', 'Oropharynx', 'Hypopharynx'],
        airwayNav: ['Trachea', 'Primary bronchus', 'Bronchi'],
        lungSubNav: ['Bronchioles', 'Alveoli']
      };
    },
    computed: {
      activePart() {
        return (label) => {
          return this.activeLabel === label;
        };
      },
      activedLabel() {
        // 展开的文字是否高亮显示
        return (label, mLabel) => {
          return this.activeLabel === label || mLabel === label;
        };
      },
      initActiveBrain() {
        // (初始化&当前)显示的大脑部位、线条、文字
        return (label) => {
          return !this.activeBrain || this.activeBrain === label;
        };
      },
      initUnactiveBrain() {
        // 初始化不高亮
        return (label) => {
          return !this.activeBrain || (this.activeBrain && this.activeBrain !== label);
        };
      },
    },
    methods: {
      update(pLabel = null, label = null, mLabel = null) {
        this.activeBrain = pLabel;
        this.activeLabel = label;
        this.activedMLabel = mLabel;
        this.$emit("brainAreaUpdate", label || mLabel || pLabel);
        this.showImg = label;
      },
      linkTo(areaName) {
        // 公共方法跳转到对应页面，同文件下可用window.open('index.html')做跳转
        // 根据areaName传值不同，跳转到对应页面
        console.log(areaName, 'areaName');
        window.open('example.html')
      },
      // 点击div外部事件
      handleOutsideClick(e) {
        this.activeBrain = null;
        this.activeLabel = null;
        this.activedMLabel = null;
        this.$emit("brainAreaUpdate", null);
      },
    },
    mounted() {
      const imgMap = document.getElementById("imgMap");
      this.$nextTick(() => {
        imgMap.onload = () => {
          const naturalW = imgMap.naturalWidth;
          const scale = (imgMap.width / naturalW).toFixed(2);
          this.scale = scale;
          setTimeout(() => {
            const areas = document.getElementById("Map").childNodes;
            areas.forEach((area) => {
              let coords = area.coords.split(",");
              coords = coords.map((coord) => {
                return Math.floor(parseFloat(coord) * scale);
              });
              area.coords = coords.join(",");
            });
          }, 300);

        };
      });
    }
  })
  app.mount("#app")
</script>
