---
title: 'tissueloc: Whole slide digital pathology image tissue localization'
tags:
  - whole slide image
  - digital pathology
  - tissue localization
  - tissue detection
  - tissue region
  - pyramid structure
authors:
 - name: Pingjun Chen
   orcid: 0000-0003-0528-1713
   affiliation: "1"
 - name: Lin Yang
   affiliation: "1"
affiliations:
 - name: J. Crayton Pruitt Family Department of Biomedical Engineering, University of Florida
   index: 1
date: 20 December 2018
bibliography: paper.bib
---

# Background
``tissueloc`` is an open-source Python package for fast and accurate tissue localization on whole slide image (WSI). Automatic pathology diagnosis using WSI gradually becomes a research hotspot in biomedical imaging domain [@cruz2014automatic, @barker2016automated]. Because of the gigabyte size of WSI, instead of directly taking the WSI as input, patch-based strategy is commonly used to deal with WSI [@cruz2014automatic, @hou2016patch, @chen2018automatic]. As there are large amounts of background regions that are useless for diagnosis, researchers working on automatic WSI diagnosis can utilize ``tissueloc`` to locate genuine tissue regions and focus their analysis on these regions.


# Overview
``tissueloc`` mainly contains two functionalities: selecting proper low level image from WSI and tissue localization based on the selected low level WSI.

The width and height of WSI are far larger than 10,000 pixels. Locating tissue regions directly on WSI image is computationally expensive. However, based on the pyramid storage structure of WSI, we can select a proper low level image from the WSI for following tissue localization. The low level slide image can have much smaller size, thus can speed up the tissue localization process. Based on the setting of maximum width or height of the low level image, we select the level that its corresponding image has size smaller but closest to the setting.

Tissue localization is applied on the selected low level image based on
a series of basic image processing techniques. The main procedures include: 1) Low level WSI loading. 2) Color space conversion from RGB to gray. 3) Inverse binarization to generate binary image. 4) Hole filling of the binary image. 5) Small object removal. 6) Contour finding.

 ![Tissue localization pipeline for whole slide image. The main procedures include: 1) Low level image loading. 2) Color space conversion. 3) Inverse binarization. 4) Hole filling. 5) Small object removal. 6) Contour finding.](tissuelocPipeline.png)

The proposed WSI tissue localization is very efficient as it is entirely based on basic image processing techniques and applied on low level image, which could act as a preprocessing step for automatic WSI analysis. Researchers can focus their analysis on those patches inside the located tissue regions and avoid those irrelevant background regions.

# Acknowledgement
Development was supported by National Institutes of Health R01 AR065479-02.

# References
