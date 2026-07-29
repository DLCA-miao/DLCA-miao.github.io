---
title: "Developmental Lung Cell Atlas - Helps"
layout: piclay
excerpt: "Developmental Lung Cell Atlas -- Helps"
permalink: /Helps/
---

# Help

<div class="help-nav">
<a class="btn btn-default" href="#Data Viewer" >Data Viewer</a>
<a class="btn btn-default" href="#Portrait">Portrait</a>
<a class="btn btn-default" href="#Genes">Gene</a>
<a class="btn btn-default" href="#Exploration">DEG</a>
<a class="btn btn-default" href="#Dataset">Dataset</a>
</div>


<h1 style="background-color: #00528e; color:#ffffff;">Data Viewer</h1>
<p id="Data Viewer"> </p>
<p>The Data Viewer page features the UMAP that presents the sample characteristics and gene expressions in the Developmental Lung Cell Atlas.
From the "Data Viewer" tab, you can choose to view a particular UMAP of lung.</p>
<p>(1)  <span class="material-icons" style="font-size: 15px; vertical-align: middle;">hub</span> : You can choose different atlas to display the UMAPs.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_dataview_data.png" class="help-image">
<p>(2)  <span class="material-icons" style="font-size: 18px; vertical-align: middle;">settings</span> : You can view coloured cells from a certain attribute for the cells. Several other dimiensions to view the UMAP are described in the first table of the Help Page</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_dataview_2.png" class="help-image">
<!-- <p>The left panel plot is a plotly.js module that displays the integrative UMAPs of the Adult Lung, Fetal Lung, Tumour and Organoids in the Respire Cell Atlas.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_figure_Dataviewer_left.png" style='height: 800px; width: auto; margin: 0;'> -->
<p>A list of selectable attributes to display the UMAPs are shown in the left column.</p>
<div class="help-table-wrap">
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CellType</td>
      <td>Cell type annotation.</td>
    </tr>
    <tr>
      <td>CellType Level1</td>
      <td>Broad cell type class.</td>
    </tr>    
    <tr>
      <td>CellType Level2</td>
      <td>Fine cell type.</td>
    </tr>  
    <tr>
      <td>CellType Level3</td>
      <td>Cell subtype.</td>
    </tr>    
    <tr>
      <td>Anatomical Region</td>
      <td>Anatomical structure(Please find details in the third table of the Help Page).</td>
    </tr>
    <tr>
      <td>Age</td>
      <td>For postnatal individuals, 6 months old is denoted by 6mo; 21 years old is denoted by "21 yr".
For prenatal individuals, 9 PCW stands for post-conception weeks.</td>
    </tr>   
    <tr>
      <td>Developmental Stage</td>
      <td>Developmental stage of each individual.</td>
    </tr>     
    <tr>
      <td>Gender</td>
      <td>F = Female; M = Male; Unclassified = Unknown.</td>
    </tr>               
    <tr>
      <td>Sample ID</td>
      <td>Sample ID of the cells or nuclei.</td>
    </tr>
    <tr>
      <td>Donor ID</td>
      <td>Author specified donor IDs, which are indicated in the original publications.</td>
    </tr>
    <tr>
      <td>Study</td>
      <td>Publications in the HDLCA reference atlas.</td>
    </tr>
    <tr>
      <td>Sequencing Technology</td>
      <td>Sequencing technology of the cells or nuclei.</td>
    </tr>  
     <tr>
      <td>Sequencing Methods</td>
      <td>Sequencing method of the cells or nuclei.</td>
    </tr>
    <tr>
      <td>Sample Type</td>
      <td>Categorizes samples according to the developmental stage of the donor, including fetal, infancy, adolescence and adult.</td>
    </tr>
    <tr>
      <td>Sample Status</td>
      <td>Health status of the tissue source.</td>
    </tr>

  </tbody>
</table>
</div>


<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <link
    href="https://fonts.googleapis.com/icon?family=Material+Icons"
    rel="stylesheet"
  >
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/@mdi/font@7.4.47/css/materialdesignicons.min.css"
  >
  <title>Material Icons</title>
</head>
<br><br>
<p>(3)  <span class="material-icons" style="font-size: 18px; vertical-align: middle;">search</span> : You can view coloured cells according to the expression level of the selected gene.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_dataview_gene.png" class="help-image">
<p>(4) The symbol attributes of the page.</p>
<div class="help-table-wrap">
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Symbol</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><span class="material-icons" style="font-size: 18px; vertical-align: middle;">hub</span></td>
      <td>Choose different atlas to display the UMAPs.</td>
    </tr>  
    <tr>
      <td><span class="material-icons" style="font-size: 20px; vertical-align: middle;">settings</span></td>
      <td>View coloured cells according to the selected attribute in Cell Metadata.</td>
    </tr>
    <tr>
      <td><span class="material-icons" style="font-size: 20px; vertical-align: middle;">search</span></td>
      <td>View coloured cells according to the expression level of the selected gene.</td>
    </tr>
    <tr>
      <td><span class="material-icons" style="font-size: 20px; vertical-align: middle;">invert_colors</span></td>
      <td>Indicate the Cell Metadata attribute currently selected to colour cells in the UMAP.</td>
    </tr>    
    <tr>
      <td><span class="material-icons" style="font-size: 20px; vertical-align: middle;">link</span></td>
      <td>Indicate the number of selected subcategories used to color cells within the selected Cell Metadata attribute.</td>
    </tr>
    <tr>
      <td><span class="material-icons" style="font-size: 18px; vertical-align: middle;">zoom_out_map</span></td>
      <td>Reset the complete UMAP graph after cropped screenshot.</td>
    </tr>
    <tr>
      <td><span class="mdi mdi-select-arrow-up" style="font-size: 21px; vertical-align: middle;"></span></td>
      <td>Capture a region of the UMAP for a cropped screenshot.</td>
    </tr>
    <tr>
      <td><span class="mdi mdi-plus-circle-multiple-outline" style="font-size: 20px; vertical-align: middle;"></span></td>
      <td>Multi-page display of the UMAP.</td>
    </tr>
    <tr>
      <td><span class="material-icons" style="font-size: 20px; vertical-align: middle;">arrow_downward</span></td>
      <td>Download the UMAP graph.</td>
    </tr>

  </tbody>
</table>
</div>

<!-- <ul>
  <li>The scAnnot cell type names are models that predicted cell names based on the transcriptomic expressions and known brain cell names. The model was built using a well-annotated adult human brain snRNA dataset <a href="https://www.science.org/doi/10.1126/science.add7046">(Siletti et al, 2023)</a> and the fetal human brain scRNA resource <a href="https://www.biorxiv.org/content/10.1101/2022.10.24.513487v1">(Braun et al, 2022)</a>.</li>
  <li>You can read more about scAnnot from <a href="https://github.com/rnacentre/scAnnot">scAnnot's GitHub Page</a>.</li>
</ul> -->

<!-- <p><b>(2)</b> On the right panel you can view the expression of a certain gene on the UMAP from search.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_figure_Dataviewer_right.png" style='height: 800px; width: auto; margin: 0;'>
<p><b>(3)</b> You may download the UMAP, using selection tools to crop an area and zoom-in/out by clicking on the tool bars on the top-right of the panel (Some tools may take several seconds to load).</p> -->


<br><br>
<h1 style="background-color: #00528e; color:#ffffff;"> Portrait</h1>
<p id="Portrait"> </p>
<!-- <p class="header_box">Portrait</p> -->
The interactive viewer shows the human lung and includes all the major regions from the data used in Developmental Lung Cell Atlas. You can click on the relevant label and the page will direct to the data viewer page to display information about that area. 
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_portrait_2.png" class="help-image">
<style>
  .table-custom {
    font-size: 0.9rem; /* 调整字体大小 */
    width: 500px; /* 调整表格宽度 */
    height:100px
  }
</style>
<div class="help-table-wrap">
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Original Region</th>
      <th>Broad Region</th>
      <th>Region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Lung</td>
      <td>Lung</td>
      <td>Lung</td>
    </tr>
    <tr>
      <td>Right lobes</td>
      <td>Lung lobe</td>
      <td>Right lobes</td>
    </tr>
    <tr>
      <td>Peripheral lung</td>
      <td>Periphery</td>
      <td>Periphery</td>
    </tr>
    <tr>
      <td>Whole lung</td>
      <td>Whole lung</td>
      <td>Whole lung</td>
    </tr>
    <tr>
      <td>d_LowLeftPar</td>
      <td>Parenchyma</td>
      <td>Parenchyma</td>
    </tr>
    <tr>
      <td>a_Trachea</td>
      <td>Trachea</td>
      <td>Trachea</td>
    </tr>
    <tr>
      <td>Distal lung</td>
      <td>Distal lung</td>
      <td>Distal lung</td>
    </tr>
    <tr>
      <td>e_TopLeftPar</td>
      <td>Parenchyma</td>
      <td>Parenchyma</td>
    </tr>
    <tr>
      <td>Right middle lobe</td>
      <td>Right middle lobe</td>
      <td>Right middle lobe</td>
    </tr>
     <tr>
      <td>Distal airway</td>
      <td>Distal airway</td>
      <td>Distal airway</td>
    </tr>   
    <tr>
      <td>Proximal airway epithelium</td>
      <td>Proximal airway</td>
      <td>Proximal airway</td>
    </tr>
    <tr>
      <td>c_Bronchi.4</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>
    <tr>
      <td>Proximal lung</td>
      <td>Proximal lung</td>
      <td>Proximal lung</td>
    </tr>
    <tr>
      <td>Middle airway</td>
      <td>Middle airway</td>
      <td>Middle airway</td>
    </tr>
      <tr>
      <td>b_Bronchi.2.3</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>  
      <tr>
      <td>Right upper lobe periphery region</td>
      <td>Periphery</td>
      <td>Periphery</td>
    </tr>
      <tr>
      <td>Left lower lobe periphery region</td>
      <td>Periphery</td>
      <td>Periphery</td>
    </tr>
     <tr>
      <td>Trachea</td>
      <td>Trachea</td>
      <td>Trachea</td>
    </tr>
      <tr>
      <td>Right upper lobe mid-bronchial region</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>
       <tr>
      <td>Left lower lobe bronchus region</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>
    <tr>
      <td>Left upper lobe periphery</td>
      <td>Periphery</td>
      <td>Periphery</td>
    </tr>
    <tr>
      <td>Right lobes</td>
      <td>Right lobes</td>
      <td>Right lobes</td>
    </tr>
    <tr>
      <td>Bronchus</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>
    <tr>
      <td>Bronchiole</td>
      <td>Bronchiole</td>
      <td>Bronchioles</td>
    </tr>
  </tbody>
</table>
</div>
<p>The table shows the information of regions. The Concrete Region is the original annotation of studies; the Broad Region is rough region; the Anatomical Region is the anatomical division of the region.</p> 
<!-- <table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Level1</th>
      <th>Level2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cerebral cortex</td>
      <td>Frontal lobe</td>
      <td>Prefrontal cortex <br>
      Motor cortex</td>
    </tr>
    <tr>
      <td>Cerebral cortex</td>
      <td>Parietal lobe</td>
      <td>Somatosensory cortex</td>
    </tr>
    <tr>
      <td>Cerebral cortex</td>
      <td>Occipital lobe<br>
          Temporal lobe<br>
          Cingulate cortex</td>
      <td></td>
    </tr>
    <tr>
      <td>Brainstem</td>
      <td>Midbrain<br>
          Pons<br>
          Medulla oblongata</td>
      <td></td>
    </tr>
    <tr>
      <td>Deep structures</td>
      <td>Amygdala<br>
          Basal ganglia<br>
          Hippocampus<br>
          Hypothalamus<br>
          Olfactory bulb<br>
          Pineal gland<br>
          Putamen<br>
          Thalamus</td>
      <td></td>
    </tr>
    <tr>
      <td>Corpus callosum</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Cerebellum</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Spinal cord</td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table> -->


<p id="Genes"> </p>
<br><br>
<h1 ref="" style="background-color: #00528e; color:#ffffff;">Gene</h1>
<!-- <p class="header_box" >Gene</p> -->
<p>Users can obtain a list of differentially expressed genes of the cell types from a selected lung region，or of different lung regions from a selected cell type.<br>
<p>To calculate candidate markers within a specific region by selecting tabs <b>By Region</b> or find candidate markers of a cell type by selecting the tab <b>By Cell Type</b>. After selection and click on the tab <b>Markers</b>, a volcano plot will be shown. </p>
<p>For example, if you click <b>By Region</b>, the search box will show the region and cell type, you can select a region and a cell type, this function is to show the differential genes of your selected cell type and other cell types under the same region, and clicking the <b>Markers</b> button will show the volcano map and the csv table of the differential genes. Clicking the <b>All</b> button</p> means selecting all regions.</p>

<!-- <div style="display: flex; justify-content: center;"> -->
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_gene1.png" class="help-image">
</div>

<p id="Exploration"></p>
<br><br>
<h1 style="background-color: #00528e; color:#ffffff;">DEG</h1>
<p>Cell type DEG (Differential expression Genes) compares the same cell type from different regions. Likewise, a violin plot of the top 3 DEGs for this cell type across different region will be shown after selection of the input.</p>
<p>Region DEG compares different cell types from the same region. A violin plot of the top 3 DEGs for each different cell types of the region will be shown after selection of the input.</p>
<div style="display: flex">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help-deg.png" class="help-image">
</div>

<p id="Dataset"></p>
<br><br>
<h1 style="background-color: #00528e; color:#ffffff;">Dataset</h1>
<p>The Dataset page provides access to publicly available datasets from the human and mouse respiratory systems. A complete list of the included studies and contributing authors is available on this page. The data table can be exported using the Copy, CSV, Excel, or PDF buttons.</p>
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help-dataset_2.png" class="help-image">
</div>

<style>
  .help-nav {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    position: sticky;
    top: 10px;
    z-index: 10;
    padding: 12px;
    margin-bottom: 8px;
    background: rgba(255, 255, 255, 0.94);
    border: 1px solid #dbe4ee;
    border-radius: 14px;
    backdrop-filter: blur(8px);
  }

  .help-image {
    width: min(100%, 80%);
    height: auto;
    margin: 0;
  }

  .help-table-wrap {
    width: 100%;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }

  .help-nav .btn {
    border-radius: 999px;
    border-color: #c9d6e4;
  }

  h1[style*="background-color"] {
    border-radius: 12px;
    padding: 10px 14px;
    margin-top: 28px;
    margin-bottom: 14px;
  }

  p, li {
    line-height: 1.75;
  }

  table.table {
    margin-bottom: 18px;
  }

  @media (max-width: 767px) {
    .help-nav {
      top: 6px;
      padding: 10px;
      border-radius: 12px;
    }

    .help-nav .btn {
      width: 100%;
    }

    .help-image {
      width: 100%;
    }

    .help-table-wrap table {
      min-width: 640px;
    }

    h1[style*="background-color"] {
      font-size: 26px;
      line-height: 1.3;
      padding: 8px 12px;
    }

    p, li {
      line-height: 1.7;
    }
  }
</style>
