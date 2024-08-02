---
title: "Developmental Lung Cell Atlas - Helps"
layout: piclay
excerpt: "Developmental Lung Cell Atlas -- Helps"
permalink: /Helps/
---

# Help

<a class="btn btn-default" href="#Data Viewer" >Data Viewer</a>
<a class="btn btn-default" href="#Portrait">Portrait</a>
<a class="btn btn-default" href="#Genes">Genes</a>
<a class="btn btn-default" href="#Exploration">Exploration</a>
<a class="btn btn-default" href="#Dataset">Dataset</a>
<br><br>

**Developmental Lung Cell Atlas is a comprehensive and unified atlas of the lung that was built across studies, regions, diseases and sequencing platforms. We integrated the majority of the single-nuclei/single-cell transcriptomic datasets published from 2017 to present from a diverse source of lung samples that provide a unified cell type and manually curated metadata annotated framework for lung cell research in the development.**

<h1 style="background-color: #587B39; color:#ffffff;">Data Viewer</h1>
<p id="Data Viewer"> </p>
<p>The Data Viewer page features the UMAP that presents the sample characteristics and gene expressions in the Developmental Lung Cell Atlas.
From the "Data Viewer" tab, you can choose to view a particular UMAP of lung.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_dataview.png" style='height: 70%; width: 70%; margin: 0;'>
<!-- <p>The left panel plot is a plotly.js module that displays the integrative UMAPs of the Adult Lung, Fetal Lung, Tumour and Organoids in the Respire Cell Atlas.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_figure_Dataviewer_left.png" style='height: 800px; width: auto; margin: 0;'> -->
<p>(1) By clicking  the selection from "Cell Metadata", you can view coloured cells from a certain attribute for the cells. Several other dimiensions to view the UMAP are described as below:
A list of selectable attributes to display the UMAPs are shown in the left column.</p>
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>sample_ID</td>
      <td>Sample ID of the cells or nuclei.</td>
    </tr>
    <tr>
      <td>donor_ID</td>
      <td>Author specified donor IDs, which are indicated in the original publications.</td>
    </tr>
    <tr>
      <td>donor_gender</td>
      <td>F = Female; M = Male; Unclassified = Unknown.</td>
    </tr>
    <tr>
      <td>donor_age</td>
      <td>For postnatal individuals, 6 months old is denoted by 6mo; 21 years old is denoted by "21yr".
For prenatal individuals, 9w stands for 9 gestational weeks (GW).
For organoids, use d (days in culture)
Eg. 10d.</td>
    </tr>
    <tr>
      <td>donor_status</td>
      <td>Each donor's disease status corresponds to common names appearing in MONDO Diseased Ontology.</td>
    </tr>
    <tr>
      <td>DEGregion</td>
      <td>Anatomical structure level 1 (Please find details in the first table of the Help Page).</td>
    </tr>
    <tr>
      <td>sample_status</td>
      <td>Each disease status corresponds to common names appearing in MONDO Diseased Ontology.</td>
    </tr>
    <tr>
      <td>project_code</td>
      <td>Project codes are the data accession codes or strings of abbreviation of the study provided by the authors.
Eg. GSE/SCP/E-MTAB-/PRJNA/EGAS/phs/PRJEB/SDY/SRP.</td>
     <tr>
      <td>seq_method</td>
      <td>Sequencing method of the cells or nuclei.</td>
    </tr>
    <tr>
      <td>seq_tech</td>
      <td>Sequencing technology of the cells or nuclei.</td>
    </tr>
    </tr>
  </tbody>
</table>

<!-- <ul>
  <li>The scAnnot cell type names are models that predicted cell names based on the transcriptomic expressions and known brain cell names. The model was built using a well-annotated adult human brain snRNA dataset <a href="https://www.science.org/doi/10.1126/science.add7046">(Siletti et al, 2023)</a> and the fetal human brain scRNA resource <a href="https://www.biorxiv.org/content/10.1101/2022.10.24.513487v1">(Braun et al, 2022)</a>.</li>
  <li>You can read more about scAnnot from <a href="https://github.com/rnacentre/scAnnot">scAnnot's GitHub Page</a>.</li>
</ul> -->

<!-- <p><b>(2)</b> On the right panel you can view the expression of a certain gene on the UMAP from search.</p>
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_figure_Dataviewer_right.png" style='height: 800px; width: auto; margin: 0;'>
<p><b>(3)</b> You may download the UMAP, using selection tools to crop an area and zoom-in/out by clicking on the tool bars on the top-right of the panel (Some tools may take several seconds to load).</p> -->

<br><br>
<h1 style="background-color: #587B39; color:#ffffff;"> Portrait</h1>
<p id="Portrait"> </p>
<!-- <p class="header_box">Portrait</p> -->
The interactive viewer shows the human lung and includes all the major regions from the data used in Developmental Lung Cell Atlas. You can click on the relevant label and the page will direct to the data viewer page to display information about that area. 
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_portrait.png" style='height: 100%; width: 80%; margin: 0;'>
<style>
  .table-custom {
    font-size: 0.9rem; /* 调整字体大小 */
    width: 500px; /* 调整表格宽度 */
    height:100px
  }
</style>
<table class="table table-hover table-bordered">
  <thead>
    <tr>
      <th>Concrete Region</th>
      <th>Broad Region</th>
      <th>Anatomical Region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Distal airway</td>
      <td>Distal airway</td>
      <td>Distal airway</td>
    </tr>
    <tr>
      <td>Lung</td>
      <td>Whole lung</td>
      <td>Whole lung</td>
    </tr>
    <tr>
      <td>Peripheral lung</td>
      <td>Periphery</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>d_LowLeftPar</td>
      <td>Parenchyma</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>e_TopLeftPar</td>
      <td>Parenchyma</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>c_Bronchi.4</td>
      <td>Bronchi</td>
      <td>Bronchi</td>
    </tr>
    <tr>
      <td>Distal lung</td>
      <td>Distal lung</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>Whole lung</td>
      <td>Whole lung</td>
      <td>Whole lung</td>
    </tr>
    <tr>
      <td>Right lobes</td>
      <td>Right lobes</td>
      <td>Right lobes</td>
    </tr>
    <tr>
      <td>Middle airway</td>
      <td>Middle airway</td>
      <td>Middle airway</td>
    </tr>
    <tr>
      <td>Proximal airway epithelium</td>
      <td>Proximal airway</td>
      <td>Proximal airway</td>
    </tr>
    <tr>
      <td>a_Trachea</td>
      <td>Trachea</td>
      <td>Trachea</td>
    </tr>
    <tr>
      <td>Right middle lobe</td>
      <td>Right middle lobe</td>
      <td>Right middle lobe</td>
    </tr>
    <tr>
      <td>Left lower lobe periphery region</td>
      <td>Periphery</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>Right upper lobe periphery region</td>
      <td>Periphery</td>
      <td>Bronchioles/alveoli</td>
    </tr>
    <tr>
      <td>b_Bronchi.2.3</td>
      <td>Bronchi</td>
      <td>Primary bronchus</td>
    </tr>
    <tr>
      <td>Not applicable</td>
      <td>Trachea</td>
      <td>Trachea</td>
    </tr>
    <tr>
      <td>Proximal lung</td>
      <td>Proximal lung</td>
      <td>Proximal lung</td>
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
      <td>Bronchioles/alveoli</td>
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
<h1 ref="" style="background-color: #587B39; color:#ffffff;">Gene</h1>
<!-- <p class="header_box" >Gene</p> -->
<p>Users can obtain a list of differentially expressed genes of the cell types from a selected lung region.<br>
The cell type name is defined by the most scored prediced cell type computed from the 8 machine-learning-based annotation methods:</p>
<ul>
  <li><a href="https://academic.oup.com/bioinformatics/article/36/2/533/5540320?login=false">ACTINN</a></li>
  <li><a href="https://www.rnacentre.org/RCA_Web/10.1093/nar/gkz543">CHETAH</a></li>
  <li><a href="https://www.nature.com/articles/s41587-021-01001-7">scArches</a></li>
  <li><a href="https://doi.org/10.1038/nmeth.4644">ScMap</a></li>
  <li><a href="https://doi.org/10.1186/s13059-019-1862-5">ScPred</a></li>
  <li><a href="https://doi.org/10.1016/j.cels.2019.06.004">SingleCellNet</a></li>
  <li><a href="https://doi.org/10.1038/s41590-018-0276-y">SingleR</a></li>
  <li>scAnnot - a hierarchical classification model trained based on scANVI.</li>
</ul>
<p>To calculate candidate markers within a specific region by selecting tabs <b>By Region</b> or find candidate markers of a cell type by selecting the tab <b>By Cell type</b>. After selection and click on the tab <b>Markers</b>, a volcano plot will be shown</p>
<p>For example, if you click By Region, the search box will show the region and cell type, you can select a region and a cell type, this function is to show the differential genes of your selected cell type and other cell types under the same region, and clicking the marker button will show the volcano map and the csv table of the differential genes.</p>

<!-- <div style="display: flex; justify-content: center;"> -->
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_gene1.png" style='height: 100%; width: 70%; margin: 0;'>
</div>
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help-gene2.png" style='height: 100%; width: 70%; margin: 0;'>
</div>

<h1 style="background-color: #587B39; color:#ffffff;">Region DEG & Cell type DEG</h1>
<p>Region DEG (Differential expression Genes) compares different cell types from the same region. A violin plot of the top 3 DEGs for each different cell types of the region will be shown after selection of the input.</p>
<p>Cell type DEG compares the same cell type from different regions. Likewise, a violin plot of the top 3 DEGs for this cell type across different region will be shown after selection of the input.</p>
<div style="display: flex">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help-deg.png" style='height: 100%; width: 70%; margin: 0;'>
</div>

<!-- <h1>Cell type DEG</h1> -->

<!-- <div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/brain_celltype.png" style='height: 100%; width: 100%; margin: 0;'>
</div> -->
<p id="Exploration"> </p>
<br><br>
<h1 style="background-color: #587B39; color:#ffffff;">Exploration</h1>
<p>This page present the statistics of Developmental Lung Cell Atlas with various of plots.<br>
You can locate the lung region to get summary information about the relevant resources in the Developmental Lung Cell Atlas. From the "Data Viewer" tab, you can choose the Atlas from  Developmental Lung. Then, select some meta information from the "Cell Metadata" tab and click on the "COMPOSITION" button to view the statistics information. For example, in "Cell Metadata", select "donor_gender" and "donor_age", and then click "COMPOSITION" to see the gender ratio for each age.</p>
<ul>
  <li><b>Cell Proportion</b><br>The bar plot shows the proportion of different donor gender in the different ages. The cell types are annotated with <a href="https://github.com/rnacentre/scAnnot">scAnnot</a>.</li>
</ul>
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help_explore.png" style='height: 100%; width: 70%; margin: 0;'>
</div>

<p id="Dataset"></p>
<br><br>
<h1 style="background-color: #587B39; color:#ffffff;">Dataset</h1>
<p>The Dataset page includes all the datasets used in the Developmental Lung Cell Atlas, a full list of the studies and authors from this page can be found here. Processed data with re-annotated cell type metadata will be avaiable for download upon publication. All data can be downloaded by four buttons: Copy, CSV, Excel, PDF etc.</p>
<div style="display: flex;">
<img src = "{{ site.url }}{{ site.baseurl }}/images/helpPage/help-dataset.png" style='height: 100%; width: 70%; margin: 0;'>
</div>