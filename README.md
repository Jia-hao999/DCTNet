# SSAV (CVPR2019-Oral) <a name="headin"></a>

Code for paper in CVPR2019, '**Shifting More Attention to Video Salient Object Detection**' 

> **Authors:**
> [Deng-Ping Fan]([https://dpfan.net/](https://dengpingfan.github.io/)), 
> [Wenguan Wang](https://github.com/wenguanwang), 
> [Ming-Ming Cheng](http://mmcheng.net), 
> [Jianbing Shen](http://iitlab.bit.edu.cn/mcislab/~shenjianbing/).

[**Supplementary material** is also attached in the repo]

**Paper with code**: https://paperswithcode.com/task/video-salient-object-detection 

<p align="center">
    <img src="figures/framework.png" width="100%" /> <br />
    <em> 
    Figure 1: OVerall architecture of the proposed SSAV model.
    </em>
</p>

### Table of Contents
- [SSAV (CVPR2019-Oral) <a name="headin"></a>](#ssav-cvpr2019-oral-)
		- [Table of Contents](#table-of-contents)
	- [Abstract](#abstract)
	- [Notion of saliency shift](#notion-of-saliency-shift)
	- [Statistics of DAVSOD](#statistics-of-davsod)
	- [Downloads](#downloads)
	- [Usage](#usage)
	- [Results](#results)
	- [Citation](#citation)

## Abstract
The last decade has witnessed a growing interest in video salient object detection (VSOD). However, the research community long-term lacked a well-established VSOD dataset representative of real dynamic scenes with high-quality annotations. To address this issue, we elaborately collected a visual-attention-consistent Densely Annotated VSOD (DAVSOD) dataset, which contains 226 videos with 23,938 frames that cover diverse realistic-scenes, objects, instances and motions. With corresponding real human eye-fixation data, we obtain precise ground-truths. This is the first work that explicitly emphasizes the challenge of saliency shift, i.e., the video salient object(s) may dynamically change. To further contribute the community a complete benchmark, we systematically assess 17 representative VSOD algorithms over seven existing VSOD datasets and our DAVSOD with totally ~84K frames (largest-scale). Utilizing three famous metrics, we then present a comprehensive and insightful performance analysis. Furthermore, we propose a baseline model. It is equipped with a saliencyshift-aware convLSTM, which can efficiently capture video saliency dynamics through learning human attention-shift behavior. Extensive experiments1 open up promising future directions for model development and comparison.


## Notion of saliency shift
The saliency shift is not just represented as a binary signal, w.r.t., whether it happens in a certain frame. Since we focus on an object-level task, we change the saliency values of different objects according to the shift of human attention. The rich annotations, including saliency shift, object-/instance-level ground-truths (GT), salient object numbers, scene/object categories, and camera/object motions, provide a solid foundation for VSOD task and benefit a wide range of potential applications.

<p align="center">
    <img src="figures/saliencyShift-1.png" width="70%" /> <br />
    <em> 
    Figure 2: Annotation examples of our DAVSOD dataset.
    </em>
</p>


## Statistics of DAVSOD
<p align="center">
    <img src="figures/DAVSOD-statistics.png" width="100%" /> <br />
    <em> 
    Figure 3: Statistics of the proposed DAVSOD dataset.
    </em>
</p>

Figure 3 shows (a) Scene/object categories. (b, c) Distribution of annotated instances and image frames, respectively. (d) Ratio distribution of the objects/instances. (e) Mutual dependencies among scene categories in (a).


## Downloads
1. **DAVSOD dataset.** 
   - Training Set (3.05G, 61 sequences)  | [Baidu  Pan](https://pan.baidu.com/s/1gwflPRUk2pxWAj6jFAZxYQ)(fetch code: wvi3) | [Google Drive](https://drive.google.com/drive/folders/1_seEomJRkLWipHyEl28FQfmjbma-v0_8?usp=sharing) (**Updated link: 2021-02-18**)
   - Validation Set (2.30G, 46 sequences)  | [Baidu  Pan](https://pan.baidu.com/s/1YMxk7MTzxm-mrW92kmmveg)(fetch code: 9tbb) | [Google Drive](https://drive.google.com/drive/folders/1nJ3LhgKOE-Dy73sslxTlD8aSxufC3eQw?usp=sharing) (**Updated link: 2021-02-18**)
   - Test Set (4.89G, 80 sequences) | [Baidu Pan](https://pan.baidu.com/s/1A29Cf-KdCBA1dbxXodCg4Q) | [Google Drive](https://drive.google.com/drive/folders/18nCaMmLBzwAiNslODiPXMsKyP-qX0pi0?usp=sharing) (**Updated link: 2021-02-18**) 
     - Easy-35 (2.08G, 35 sequences,  tested in CVPR’19) | [Baidu  Pan](https://pan.baidu.com/s/1OtmI_eclQo9oD4IQY8p4OQ)(fetch code: v5ss) | [Google Drive](https://drive.google.com/file/d/1hwlb1t7S_Zahp6GSKW9qlRMQh7lMUhph/view?usp=sharing) (**Updated link: 2021-02-18**)
     - Normal-25 (1.42G, 25 sequences)   | [Baidu  Pan](https://pan.baidu.com/s/1QdWUy3vUbw1dkpitUoCqpw)| [Google Drive](https://drive.google.com/file/d/1bclC888a-3yXc-yTVB5PPnwyPiPi2hNJ/view?usp=sharing) (**Updated link: 2021-02-18**)
     - Difficult-20 (1.38G, 20 sequences)  | [Baidu  Pan](https://pan.baidu.com/s/1GcZp_R3KkgSdWItJCcJyjA) | [Google Drive](https://drive.google.com/file/d/1ZHf3y96tF7m92L08DnctI3uRh7h-gZo9/view?usp=sharing) (**Updated link: 2021-02-18**)
   - video description, name, attributes: [DAVSOD-name.xlsx](http://dpfan.net/wp-content/uploads/DAVSOD-name.xlsx) (old version) | [DAVSOD-name-v2.xlsx](http://dpfan.net/wp-content/uploads/DAVSOD-name-v2.xlsx) ( **Updated**: **2019-9-11**) | [DAVSOD-Statistics.xlsx](http://dpfan.net/wp-content/uploads/Taxonomy.xlsx) (old version) | [DAVSOD-Statistics-v2.xlsx](http://dpfan.net/wp-content/uploads/Taxonomy-v2.xlsx) (**Updated**: **2019-9-11**)

	**Note**: 
	- The [DAVSOD-name-v2.xlsx](http://dpfan.net/wp-content/uploads/DAVSOD-name-v2.xlsx) deleted some description of missing videos (0124、0291、0413、0556). Some video like 0189\_1 share with the same attributes with 0189. These shared videos including: 0064\_1, 0066\_1, 0182\_1, 0189\_1, 0256\_1, 0616\_1, 0675\_1, 0345\_1, 0590\_2, 0318\_1, 0328\_1, 0590\_1, 0194\_1, 0321\_1, 0590\_3
	- we merge the small sequence of the training set. Thus, there are only 61 sequences which are different from the CVPR 2019 paper (90 training sequences).


1. **SSAV model.** 
   - caffe version: [https://github.com/DengPingFan/DAVSOD](https://github.com/DengPingFan/DAVSOD)
   - pytorch version: coming soon.
   - Tensorflow version:  coming soon.


1. **Popular Existing Datasets.**

	Previous datasets have different formats, causing laborious data preprocessing when training or testing. Here we unified the format of all the datasets for easier use:
	
   	- original images saved as \*.jpg format 
   	- original images indexd of zero (e.g., 00000.jpg)
   	- ground-truth images saved as \*.png format

	|**Year**|**Publisher**|**Dataset**|**Clips**|**Download Link1**|**Download Link2**|
	| :-: | :-: | :-: | :-: | :-: | :-: |
	|2010|BMVC|**SegV1**|5(11.9MB)|[Baidu Pan](https://pan.baidu.com/s/1UQ0Lhoc94xwCL0dDUcFQYw)|[Google Driver](https://drive.google.com/open?id=12OslUpBZ61fNh48ksQYp43mt46gxj7k7)|
	|2013|ICCV|**SegV2**|14(84.9MB)|[Baidu Pan](https://pan.baidu.com/s/1MywImBeU644Z_qfwUwAxdg)|[Google Driver](https://drive.google.com/open?id=1xQznG6etAtbNEjb1R2ZbjXDD4RCWTHax)|
	|2014|TPAMI|**FBMS**|30 (790MB)|[Baidu Pan](https://pan.baidu.com/s/1KwW2-FlF-mkTRD5JRu_aNg)|[Google Driver](https://drive.google.com/open?id=1fOkBR_l1YzZ_eDojDa50ZLD-8Nv5OnJ3)|
	|2014|TPAMI|FBMS-59 (overall)|59(817.52MB)|[Baidu Pan](https://pan.baidu.com/s/159WtwxYy3ZDo1kg_K90ogQ)|[Google Driver](https://drive.google.com/open?id=1nmJVBvSRIi-OBaYvDl6PXb5xirENG9F-)|
	|2015|TIP|**MCL**|9(308MB)|[Baidu Pan](https://pan.baidu.com/s/1OH9FhK74Km5GM46FZmotwA)|[Google Driver](https://drive.google.com/open?id=1DGrIJM660zj6k67Mfgv7z3K2uIQnVaCs)|
	|2015|TIP|**ViSal**|17(59.1MB)|[Baidu Pan](https://pan.baidu.com/s/1s7OwV_wv6VUJV0DBN7Ot8A)|[Google Driver](https://drive.google.com/open?id=1q7I0srSSrlj-78aInbUpPqhHrcdxTZUt)|
	|2016|CVPR|**DAVIS**|50(842MB)|[Baidu Pan](https://pan.baidu.com/s/1SlrLuviBez1AkpNl-MzQtA)|[Google Driver](https://drive.google.com/open?id=1slc9rE6stq8ASyl0Mocznx6PLvu_zxOc)|
	|2017|TCSVT|**UVSD**|18(207MB)|[Baidu Pan](https://pan.baidu.com/s/1OL6-kOg6y0GPk_pf4ZJ1sw)|[Google Driver](https://drive.google.com/open?id=18Rv4xycxp7MLQHFliuDWUdcRxw2mQOsO)|
	|2018|TIP|[**VOS**](http://dpfan.net/wp-content/uploads/2018TIPVOSA-Benchmark-Dataset-and-Saliency-guided-Stacked-Autoencoders-for-Video-based-Salient-Object-Detection.pdf)|200(3.33GB)|Baidu Pan|Google Driver|
	|||**VOS\_test**|40(672MB)|[Baidu Pan](https://pan.baidu.com/s/1C1-Zf54Uqor8foaVMgq6xQ)|[Google Driver](https://drive.google.com/open?id=1ld3zHXjMO0I9OJAtIa6Ux-0UA1XfB7dG)|
	|2019|CVPR|**DAVSOD**|187(10.24G)|[Baidu Pan](https://pan.baidu.com/s/164sajEdC10-LOxGjCnEuUw) (fetch code: ivzo)|[Google Driver](https://drive.google.com/drive/folders/1BnDF7nB9gPFibx5a8XW5QMc-uyZTTNdA)|
	|||All datasets |||[Google Driver](https://drive.google.com/open?id=1AgDKaFESTwpRESqT3XecvWUNHxQYsLg1)


	\* We do not include the “penguin sequence” of the SegTrack-V2 dataset due to its inaccurate segmentation. Thus the results of the MCL dataset only contains 13 sequences in our benchmark. For VOS dataset, we only benchmark the test sequence divided by our benchmark (Traning Set: Val Set: Test Set = 6:2:2).

1. **Papers & Codes & Results (continue updating).**

	We have spent about **half a year** to execute all of the codes. You can download all the results directly for the convience of research. Please cite our paper if you use our results. The overall results link is here ([Baidu](https://pan.baidu.com/s/1ORJg2X4t6OFl-fYlEUcPvw)|Google)  **(Update: 2019-11-17)**	
	
|**Year & Pub & Paper**|**Model**|**DAVIS**|**DAVSOD**|**FBMS**|**SegV2**|**VOS**|**RDVS**|**ViSal**|**VOS**|**DAVSOD & Overall**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|2018 & ECCV & [**PDB**](http://dpfan.net/wp-content/uploads/2008CVPR%E3%80%90PGFT%E3%80%91Spatio-temporal-Saliency-Detection-Using-Phase-Spectrum-of-Quaternion-Fourier-Transform.pdf)|[Code](http://dpfan.net/wp-content/uploads/2008-CVPR-PQFT.zip)|[Baidu ](https://pan.baidu.com/s/1T6RD6gDmZRhdqeMfIp2aMQ)\| Google|[Baidu ](https://pan.baidu.com/s/1Ab0ex7YK0cMgRHPbgkNiYw)\| Google|[Baidu ](https://pan.baidu.com/s/1xrLthuxOpw6t1rPG--x1xA)\| Google|[Baidu ](https://pan.baidu.com/s/1StnLc4X2LvOqG2DRet4jeA)\| Google|[Baidu ](https://pan.baidu.com/s/13g7RsXMmzYVL6_BBgZC5ow)\| Google|[Baidu ](https://pan.baidu.com/s/1MczGKR1inm8DySUVei-kDg)\| Google|[Baidu ](https://pan.baidu.com/s/1Lh-jnPdOPFu61NN2QPsgfw)\| Google|[Baidu](https://pan.baidu.com/s/1WB0lRQLSQYylRf8RqgtVkw) \| Google|[Baidu ](https://pan.baidu.com/s/1n15KvcC5g1mPsvXKpp5U5w)\| Google|
|2019 & ICCV & [**MGAN**](http://dpfan.net/wp-content/uploads/2009JOVSSTStatic-and-Space-time-Visual-Saliency-Detection-by-Self-Resemblance.pdf)|[Code](http://dpfan.net/wp-content/uploads/2009-JOV-SST.zip)|[Baidu ](https://pan.baidu.com/s/1TBVqzCB7c1sG2DHmyu-D4Q)\| Google|[Baidu ](https://pan.baidu.com/s/19GqLH1wYdFcvCXjXp7IsNA)\| Google|[Baidu ](https://pan.baidu.com/s/1arnIiFBV-gfoKdVpEl0miA)\| Google|[Baidu ](https://pan.baidu.com/s/1sS7YlS4lNAnX4WV5cGJFFQ)\| Google|[Baidu ](https://pan.baidu.com/s/1_ngJQfKK7ZKuJxte5cPq9Q)\| Google|[Baidu ](https://pan.baidu.com/s/1epAaC6GbCFkhGVq5mIJbsg)\| Google|[Baidu ](https://pan.baidu.com/s/157jLf2roSvlXsDPZ5Zbyxg)\| Google|[Baidu ](https://pan.baidu.com/s/1ALW2n1ThQ_TJgM18l933FA)\| Google|[Baidu ](https://pan.baidu.com/s/1O3wBq3wZJxx-9wNvWMej4w)\| Google|
|2020 & AAAI & [**PCSA**](http://dpfan.net/wp-content/uploads/2009JOVSSTStatic-and-Space-time-Visual-Saliency-Detection-by-Self-Resemblance.pdf)|[Code](http://dpfan.net/wp-content/uploads/2009-JOV-SST.zip)|[Baidu ](https://pan.baidu.com/s/1TBVqzCB7c1sG2DHmyu-D4Q)\| Google|[Baidu ](https://pan.baidu.com/s/19GqLH1wYdFcvCXjXp7IsNA)\| Google|[Baidu ](https://pan.baidu.com/s/1arnIiFBV-gfoKdVpEl0miA)\| Google|[Baidu ](https://pan.baidu.com/s/1sS7YlS4lNAnX4WV5cGJFFQ)\| Google|[Baidu ](https://pan.baidu.com/s/1_ngJQfKK7ZKuJxte5cPq9Q)\| Google|[Baidu ](https://pan.baidu.com/s/1epAaC6GbCFkhGVq5mIJbsg)\| Google|[Baidu ](https://pan.baidu.com/s/157jLf2roSvlXsDPZ5Zbyxg)\| Google|[Baidu ](https://pan.baidu.com/s/1ALW2n1ThQ_TJgM18l933FA)\| Google|[Baidu ](https://pan.baidu.com/s/1O3wBq3wZJxx-9wNvWMej4w)\| Google|
|2019 & CVPR & [**SSAV**](http://dpfan.net/wp-content/uploads/2010ECCVSIVSegmenting-Salient-Objects-from-Images-and-Videos.pdf)|Code|[Baidu](https://pan.baidu.com/s/12fYTWtuOTe1refKt_qkZUg) \| Google|[Baidu](https://pan.baidu.com/s/1YkCjHTLG910H0EijJIQjWQ) \| Google|[Baidu](https://pan.baidu.com/s/15tpcXdkcWtkQ2oeENBgP0w) \| Google|[Baidu](https://pan.baidu.com/s/1x9tjEPpeH1fQNjkn17Fh-w) \| Google|[Baidu](https://pan.baidu.com/s/1rVZC_aNmw99D_PyUZ548Wg) \| Google|[Baidu](https://pan.baidu.com/s/1OfgeBaVOy7vVo5jNcfjIHw) \| Google|[Baidu](https://pan.baidu.com/s/1Yl_bPRrTnnCjtA5Erbs88g) \| Google|[Baidu](https://pan.baidu.com/s/1yOpkOn7PziogwHxvTUtqJw) \| Google|[Baidu](https://pan.baidu.com/s/1X5SysUkVXGuURvDjY3-BVg) \| Google|
|2021 & ICCV & [**FSNet**](http://dpfan.net/wp-content/uploads/2014CVPRTIMPTime-Mapping-Using-Space-Time-Saliency.pdf)|[Code](http://dpfan.net/wp-content/uploads/2014-CVPR-TIMP.zip)|[Baidu ](https://pan.baidu.com/s/12XB0NlAX1fw8yxSOrSlvSg)\| Google|[Baidu ](https://pan.baidu.com/s/1UWWbFzoz9vUazQHdsFskGg)\| Google|[Baidu ](https://pan.baidu.com/s/1Xb4JfLDxf4uBMH6aLmi3gA)\| Google|[Baidu ](https://pan.baidu.com/s/1ys3Zju3GHwR64cNB19ZDew)\| Google|[Baidu ](https://pan.baidu.com/s/1z8XCcO79hEOe9zsRAimvAQ)\| Google|[Baidu ](https://pan.baidu.com/s/16aUN7UsBDPv7VP-rn6F1hw)\| Google|[Baidu ](https://pan.baidu.com/s/1hvtVFOlwowfS2tQZ4aDADA)\| Google|Baidu \| Google|[Baidu ](https://pan.baidu.com/s/1GA0hp7_1iVB-RkcLc5oA-w)\| Google|
|2021 & ICCV & [**DCFNet**](http://dpfan.net/wp-content/uploads/2014TCSVTSPSuperpixel-Based-Spatiotemporal-Saliency-Detection.pdf)|[Code](http://www.ivp.shu.edu.cn/Default.aspx?tabid=33430)|[Baidu](https://pan.baidu.com/s/1rYIOt79nsyLrDEIzvpKfeQ) \| Google|[Baidu ](https://pan.baidu.com/s/1-hjZ3OjRQlCZkTxd51uZ5A)\| Google|[Baidu](https://pan.baidu.com/s/1Vpc3ICd6j3lzBMaN1Ayl9A) \| Google|[Baidu](https://pan.baidu.com/s/1kLD9Qepc9ilHDLiuSnHJsw) \| Google|[Baidu](https://pan.baidu.com/s/1-4cvt4qOtoJk8Vl0-LaPDg) \| Google|[Baidu](https://pan.baidu.com/s/1-kuRgB4hUbFY8gqqEhV9_A) \| Google|[Baidu](https://pan.baidu.com/s/1YCPQ4_sDUomxEGjivO_j1w) \| Google|[Baidu](https://pan.baidu.com/s/1vkBMMMY2C4TYh7cgJ--1cw) \| Google|[Baidu](https://pan.baidu.com/s/1tmqCvj84-vHJfH5mPnAL2w) \| Google|
|2022 & ICIP & [**DCTNet**](http://dpfan.net/wp-content/uploads/2015CVPRSAGSaliency-Aware-Geodesic-Video-Object-Segmentation.pdf)|[Code](http://dpfan.net/wp-content/uploads/2015-CVPR-SAG.zip)|[Baidu](https://pan.baidu.com/s/1JbKHX1LPnIxp8TzDys1H9Q) \| Google|[Baidu](https://pan.baidu.com/s/17sYQTV6i9fdapP61PJyL7w) \| Google|[Baidu](https://pan.baidu.com/s/19_nwWB9g9-4lo9sxkp_dMg) \| Google|[Baidu](https://pan.baidu.com/s/1nMvFloed3rIguxfN7HMMQQ) \| Google|[Baidu](https://pan.baidu.com/s/1u5BtxnNU5gdnV2qZgK5hpw) \| Google|[Baidu](https://pan.baidu.com/s/1dP1LS0pJUvk3j977wqvASA) \| Google|[Baidu](https://pan.baidu.com/s/1HR0p5lf__WTvhIvm45-Ozg) \| Google|[Baidu ](https://pan.baidu.com/s/1XMhAs7PNdVsqGbNLgC-GVQ)\| Google|[Baidu](https://pan.baidu.com/s/1-msJI7SH8OGJPckm0nveTw) \| Google|
## Usage

The code has been tested successfully on Ubuntu 16.04 with CUDA 8.0 and OpenCV 3.1.0

1. Prerequisites: 
	
	Use `DAVSOD/mycaffe-convlstm/Makefile.config` to build caffe. Follow [official instructions](http://caffe.berkeleyvision.org/installation.html).

	```bash
	make all -j8
	make pycaffe
	```

1. Downloading necessary data:

    + downloading the training/testing dataset and move it into `Datasets/`.
    
    + downloading pre-trained caffemodel and move it into `model/`, 
    which can be found in [baidu pan](https://pan.baidu.com/s/1dg_dcgFNOnUubfQev0e4Ag)(Fetch Code: pb0h) | [google drive](https://drive.google.com/open?id=1o9PkfgMpUI8McGSCgWG8cdGJF4dFmHrM). 

1. Testing Configuration:

    + After you download the pre-trained model and testing dataset, 
    just run `generateTestList.py` to get the test list, and `SSAV_test.py` to get the saliency maps in `results/SSAV/`.
    
    + Just enjoy it!
    
    + The prediction results of all competitors and our PNS-Net can be found at [Google Drive (7MB)](https://drive.google.com/file/d/1iCZiTS4n-5ZSnCozLBi-1gpbuzjORx4z/view?usp=sharing).

1. Training Configuration:
    
    + With the training dataset downloaded, you can download the basemodel from [baidu pan](https://pan.baidu.com/s/1qEyXennBYT2yv82bNx5TgA) (Fetch Code:0xk4) | [google drive](https://drive.google.com/file/d/1y6cpqpkAaIzBEHHpWkePTSr9C8Pyk5ND/view?usp=sharing).
    

2. Evaluating model:

	+ One-key evaluation is written in MATLAB code `main.m` in `DAVSOD/EvaluateTool/`. Details of the evaluation metrics please refer to the following papers.
		```
		[1]Structure-measure: A New Way to Evaluate the Foregournd Maps, ICCV2017.
		[2]Enhanced Alignment Measure for Binary Foreground Map Evaluation, IJCAI2018.
		```

---
Note that: This version only provide the **implicit manner** for learning attention-shift. The explicit way to train this model will not be released due to the commercial purposes (Hua Wei, IIAI).

---

## Results
1. **Leaderboard.**
	<p align="center">
		<img src = "figures/SSAV-Model-summary.png" /> <br />
		<em>
		Figure 4: Summarizing of 36 previous representative VSOD methods and the proposed SSAV model.
		</em>
	</p>

1. **Benchmark.**
	<p align="center">
		<img src = "figures/SSAV-CmpSOTAS-1.png" /> <br />
		<em>
		Figure 5: Benchmarking results of 17 state-of-the-art VSOD models on 7 datasets.
		</em>
	</p>

1. **Performance Preview**
	<p align="center">
		<img src = "figures/Table4.png" /> <br />
	</p>

	<p align="center">
		<img src = "figures/Figure6.png" /> <br />
	</p>

	<p align="center">
		<img src = "figures/blackswan.gif" width = "320px"/> <br />
		<em>
		Figure 6: Blackswan sequence result generated by our SSAV model. More results can be found in supplemental materials. 
		</em>
	</p>	

1. **DAVSOD Dataset Profile**
	<p align="center">
		<img src = "figures/DAVSODSample2.png" /> <br />
		<em>
		Figure 7: Samples from our dataset, with instance-level ground truth segmentation and fixation map.
		</em>
	</p>

	<p align="center">
		<img src = "figures/DAVSOD-AnnotationQuality.png" /> <br />
		<em>
		Figure 8: Examples to show our rigorous standards for segmentation labeling.
		</em>
	</p>

	<p align="center">
		<img src = "figures/DifferenceBetweenExistingDataset.png" /> <br />
		<em>
		Figure 9: Example sequence of saliency shift considered in the proposed DAVSOD dataset. Different (5th row) from tradition work which labels all the salient objects (2th row) via static frames. The proposed DAVSOD dataset were strictly annotated according to real human fixation record (3rd row), thus revealing the dynamic human attention mechanism.
		</em>
	</p>

	[![Watch the video](https://img.youtube.com/vi/NgsDsXDA8Zo/maxresdefault.jpg)](https://youtu.be/NgsDsXDA8Zo)

	<p align="center">
		<em>
		Watch the video for Supplemental Material
		</em>
	</p>


## Citation
If you find this useful, please cite the following works:

```
@InProceedings{Fan_2019_CVPR,
   author = {Fan, Deng-Ping and Wang, Wenguan and Cheng, Ming-Ming and Shen, Jianbing}, 
   title = {Shifting More Attention to Video Salient Object Detection},
   booktitle = {IEEE CVPR},
   year = {2019}
}
@inproceedings{song2018pyramid,
  title={Pyramid dilated deeper ConvLSTM for video salient object detection},
  author={Song, Hongmei and Wang, Wenguan and Zhao, Sanyuan and Shen, Jianbing and Lam, Kin-Man},
  booktitle={ECCV},
  pages={715--731},
  year={2018}
}

```

Contact: Deng-Ping Fan (dengpingfan@mail.nankai.edu.cn).

[⬆ back to top](#headin)
