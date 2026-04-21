# Example Data Standardization

Here we document an example of how we took processed data stored in a typical file format many researchers work with and converted that to the NWB file format (community standard accepted by EMBER). 

We also show how we are able to replicate figure results from a paper using the converted data. 

In doing this exercise, we complete a pipeline that is key for any datasets that are uploaded to EMBER. It is important that not only is the data standardized for improved storage and metadata retrieval, but that the standardized data can also be used for secondary processing and analyses. Reproducing key figures is the first such verification step towards ensuring that open datasets can be repurposed for new scientific endeavours.

## Original dataset

The [original dataset](https://zenodo.org/records/13743052) is associated with the paper [Human neural dynamics of real-world and imagined navigation](https://www.nature.com/articles/s41562-025-02119-3), authored by a BBQS Team (Dr. Nanthia Suthana, PI). It contains four .mat files containing highly processed data for each of the four figures of the paper. In addition, the MATLAB codes to generate each figure are comprised of four .m files. 

## Conversion

In collaboration with Dr. Suthana and Dr. Seeber (lead author), we explored each of the data variables in the original .mat files and identified analogous containers within the NWB file structure.

Most of the data variables are relevant to multiple subjects at the same time, as is often the case for data representing group averages in paper figures. 

Because of this, we opted to convert the data into an NWB extension: [`ndx-multisubjects`](https://pypi.org/project/ndx-multisubjects/). 

Each variable within the .mat files was then converted into the appropriate modality type within NWB with the relevant metadata capture (sampling rates, start times, descriptions of variables).

<figure style="text-align: center;">
    <img src="/assets/ZenodoConversionOutline.png" alt="Figure1_original" style="width: 100%; display:block; margin-left: auto; margin-right: auto;"> 
    <figcaption>Each variable of the four .mat files was converted into a container within a single NWB file</figcaption>
</figure>


## Verfication

To verify that the original data was properly converted into NWB, we checked whether the NWB data could be used to replicate the MATLAB code and resulting figures. 

We were able to recreate all figures from the original paper. 

Below are a few examples:



<div align="center">
  <h3>Fig. 1 Original</h3>
</div>
<figure style="text-align: center;">
    <img src="/assets/Seeber2025_Fig1_orig.png" alt="Figure1_original" style="width: 70%; display:block; margin-left: auto; margin-right: auto;"> 
  
</figure>

<br>
<div align="center">
  <h3>Fig. 1d recreated in Python with NWB data</h3>
</div>

<figure style="text-align: center;">
<img src="/assets/Seeber2025_Fig1d.png" alt="Figure1d_NWB" style="width: 70%; display:block; margin-left: auto; margin-right: auto;">
</figure>

<br>

<div align="center">
  <h3>Fig 2. Original</h3>
</div>
<figure style="text-align: center;">
    <img src="/assets/Seeber2025_Fig2_orig.png" alt="Figure2_original" style="width: 70%; display:block; margin-left: auto; margin-right: auto;"> 
</figure>

<br>
<div align="center">
  <h3>Fig. 2b top recreated in Python with NWB data</h3>
</div>
<figure style="text-align: center;">
<img src="/assets/Seeber2025_Fig2b.png" alt="Figure2_NWB" style="width: 70%; display:block; margin-left: auto; margin-right: auto;">
</figure>


<div align="center">
  <h3>Fig. 3 Original</h3>
</div>
<figure style="text-align: center;">
    <img src="/assets/Seeber2025_Fig3_orig.png" alt="Figure3_original" style="width: 70%; display:block; margin-left: auto; margin-right: auto;"> 
   
</figure>
<br>
<div align="center">
  <h3>Fig. 3a recreated in Python with NWB data</h3>
</div>
<figure style="text-align: center;">
<img src="/assets/Seeber2025_Fig3a.png" alt="Figure3_NWB" style="width: 70%; display:block; margin-left: auto; margin-right: auto;">
</figure>



<div align="center">
  <h3>Fig. 4 Original</h3>
</div>

<figure style="text-align: center;">
    <img src="/assets/Seeber2025_Fig4_orig.png" alt="Figure3_original" style="width: 70%; display:block; margin-left: auto; margin-right: auto;"> 
</figure>

<br>

<div align="center">
  <h3>Fig. 4g recreated in Python with NWB data</h3>
</div>
<figure style="text-align: center;">
<img src="/assets/Seeber2025_Fig4g.png" alt="Figure4_NWB" style="width: 70%; display:block; margin-left: auto; margin-right: auto;">
</figure>

## Next Steps

As mentioned above, the first step towards enabling robust secondary analyses is to replicate publication figures or analyses produced with the original file format. 

To continue towards this effort, the following next steps are outlined: 

- convert original raw data into NWB 
- replicate analyses from the original raw data stored in NWB, using the processed data as an intermediate check
- perform secondary (new) analyses 