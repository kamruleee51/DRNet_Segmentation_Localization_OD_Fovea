# DRNet: Segmentation of OD and Localization OD and Fovea Centers
In modern ophthalmology, automated Computer-aided Screening Tools (CSTs) are crucial non-intrusive diagnosis methods, where an accurate segmentation of Optic Disc (OD) and localization of OD and Fovea centers are substantial integral parts. However, designing such an automated tool remains challenging due to small dataset sizes, inconsistency in spatial, texture, and shape information of the OD and Fovea, and the presence of different artifacts.

This article proposes an end-to-end encoder-decoder network, named DRNet, for the segmentation and localization of OD and Fovea centers. In our DRNet, we propose a skip connection, named residual skip connection, for compensating the spatial information lost due to pooling in the encoder. Unlike the earlier skip connection in the UNet, the proposed skip connection does not directly concatenate low-level feature maps from the encoder's beginning layers with the corresponding same scale decoder. We validate DRNet using different publicly available datasets, such as IDRiD, RIMONE, DRISHTI-GS, and DRIVE for OD segmentation; IDRiD and HRF for OD center localization; and IDRiD for Fovea center localization. The proposed workflow, as shown in figure below, serves two different tasks: OD segmentation and regression using predicted heatmaps for OD and Fovea localization.

<img src="https://user-images.githubusercontent.com/32570071/99866548-42e47500-2bdc-11eb-9933-c5c51e16cca6.png" width="800" height="300">


## Contribution
1.	Proposed an automated CNN-based encoder-decoder network, called DRNet (Diabetic Retinopathy Network), for both segmentation and localization of the OD and Fovea, which substantially alleviates the necessity of manual parameter tuning while being an end-to-end system.
2.	The proposed DRNet has a U-shaped structure with newly proposed skip connections, called residual skip connections.
3.	Unlike earlier skip connections as in UNet, the new residual skip connection will not directly aggregate low-level features from the previous layers of the encoder with the corresponding same scale decoder since skipping features are passed through several convolutional layers and merged with the non-zero regularizing skipping path.
4.	To avoid primary dependence on the object’s shape on a binary mask, we create a 2D heatmap, having Gaussian-shaped intensity distribution.
5.	Publicly available datasets are used for open-source implementations.

## Utilized datasets with source link

| Different datasets                                                                  | Resolution | FoV | Bit depth |  OD center localization |  Fovea center localization | OD mask segmentation |
|-------------------------------------------------------------------------------------|:----------:|:---:|:---------:|:-----------------------:|:--------------------------:|:--------------------:|
| [IDRiD](https://idrid.grand-challenge.org/)                                         |  4288×2848 | 50° |  24-bits  |           516           |             516            |          81          |
| [RIMONE](http://medimrg.webs.ull.es/research/downloads/)                            |  1072×1424 |  -- |  24-bits  |            --           |             --             |          169         |
| [DRISHTI-GS](https://cvit.iiit.ac.in/projects/mip/drishti-gs/mip-dataset2/Home.php) |  2896×1944 | 30° |  24-bits  |            --           |             --             |          101         |
| [DRIVE](https://drive.grand-challenge.org/)                                         |   786×584  | 30° |   8-bits  |            --           |             --             |          40          |
| [HRF](http://www5.cs.fau.de/research/data/fundus-images/)                           |  3504×2336 | 45° |  24-bits  |            45           |             --             |          --          |



## Results
All the results reported in the literature were produced using the following version Python and Python API:

<ul>
    <li>Python 3.6.5</li>
    <li>numpy 1.19.0</li>
    <li>pandas 1.0.3</li>
    <li>matplotlib 3.1.3</li>
    <li>Scikit-learn 0.22.1</li>
    <li>scipy 1.4.1</li>
    <li>keras 2.3.1</li>
   
</ul>
The proposed DRNet, for OD segmentation, achieves mean Intersection over Union (mIoU) of 0.845, 0.901, 0.933, and 0.920 for IDRiD, RIMONE, DRISHTI-GS, and DRIVE, respectively. Our OD segmentation result, in terms of mIoU, outperforms the state-of-the-art results for IDRiD and DRIVE datasets, whereas it outperforms state-of-the-art results concerning mean sensitivity for RIMONE and DRISHTI-GS datasets. The DRNet localizes the OD center with mean Euclidean Distance (mED) of 20.23 and 13.34 pixels, respectively, for IDRiD and HRF datasets; it outperforms the state-of-the-art by 4.62 pixels for IDRiD dataset. The DRNet also successfully localizes the Fovea center with mED of 41.87 pixels for the IDRiD dataset, outperforming the state-of-the-art by 1.59 pixels for the same dataset. As the proposed DRNet exhibits excellent performance even with limited training data and without intermediate intervention, it can be employed to design a better-CST system to screen retinal images. <br>

<br> 

**Written by**<br>
**Md. Kamrul Hasan**  <br>
M.Sc. in Medical Imaging and Applications (MAIA)(https://maiamaster.udg.edu/ ) <br>
Assistant Professor <br>
Department of Electrical and Electronic Engineering (EEE) <br>
Khulna University of Engineering & Technology (KUET) <br>
Khulna-9203, Bangladesh <br>
E-mail: kamruleeekuet@gmail.com or m.k.hasan@eee.kuet.ac.bd<br>
G.Scholar: https://scholar.google.com/citations?user=36WXELIAAAAJ&hl=en
