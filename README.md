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

## VSOD
|**Year**|**Publisher**|**Paper**|**Model**|**RDVS**|**DAVIS**|**DAVSOD**|**FBMS**|**SegV2**|**ViSal**|**VOS**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|2018|ECCV|[**PDB**](https://openaccess.thecvf.com/content_ECCV_2018/papers/Hongmei_Song_Pseudo_Pyramid_Deeper_ECCV_2018_paper.pdf)|[Code](https://github.com/shenjianbing/PDB-ConvLSTM)|[Baidu ](https://pan.baidu.com/s/1J7gUaAQhXxpF3Rd0jdrtQg?pwd=ef57)|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|
|2019 | ICCV | [**MGAN**](https://openaccess.thecvf.com/content_ICCV_2019/papers/Li_Motion_Guided_Attention_for_Video_Salient_Object_Detection_ICCV_2019_paper.pdf)|[Code](https://github.com/lhaof/Motion-Guided-Attention)|[Baidu ](https://pan.baidu.com/s/1qp6_wrPowCea-pNedtbNkg?pwd=rufu)|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|
|2019 | CVPR | [**SSAV**](https://openaccess.thecvf.com/content_CVPR_2019/papers/Fan_Shifting_More_Attention_to_Video_Salient_Object_Detection_CVPR_2019_paper.pdf)|[Code](https://github.com/DengPingFan/DAVSOD)|[Baidu](https://pan.baidu.com/s/1Rhjh0vvHqfqHpgC83-60XA?pwd=iq5g)|[Baidu]()|[Baidu]()|[Baidu]()|[Baidu]()|[Baidu]()|[Baidu]()|
|2020 | AAAI | [**PCSA**](https://aaai.org/papers/10869-pyramid-constrained-self-attention-network-for-fast-video-salient-object-detection/)|[Code](https://github.com/guyuchao/PyramidCSA)|[Baidu ](https://pan.baidu.com/s/1GbalsdHdQ75cfKSdSao5qA?pwd=rd09)|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|
|2021 | ICCV | [**FSNet**](https://openaccess.thecvf.com/content/ICCV2021/papers/Ji_Full-Duplex_Strategy_for_Video_Object_Segmentation_ICCV_2021_paper.pdf)|[Code](https://github.com/GewelsJI/FSNet)|[Baidu ](https://pan.baidu.com/s/1fYTZ6awbJNy-XHh_IWDk6g?pwd=9hie)|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|[Baidu ]()|
|2021 | ICCV | [**DCFNet**](https://openaccess.thecvf.com/content/ICCV2021/papers/Zhang_Dynamic_Context-Sensitive_Filtering_Network_for_Video_Salient_Object_Detection_ICCV_2021_paper.pdf)|[Code](https://github.com/Roudgers/DCFNet)|[Baidu](https://pan.baidu.com/s/1zabfNUWB35z9FbpEjELYJA?pwd=hubj)|[Baidu ]()|[Baidu]()|[Baidu]()|[Baidu]()|[Baidu]()|[Baidu]()|
|2022 | ICIP | [**DCTNet**](https://arxiv.org/pdf/2202.06060.pdf)|[Code](https://github.com/luyukang/DCTNet)|[Baidu](https://pan.baidu.com/s/1VB0sJSUYxoUl__fQx8A-pA?pwd=yzd8)|[Baidu](https://pan.baidu.com/s/1S6n6aKaazrQ-w5BxD6rV9Q?pwd=awpg)|[Baidu](https://pan.baidu.com/s/1U4IazgOL-zcVM4JWqm4Odw?pwd=qmss)|[Baidu](https://pan.baidu.com/s/1Fw-UtU5A0815dfuRRB2OQw?pwd=sqxz)|[Baidu](https://pan.baidu.com/s/17Kx8qmJSeABkxE6dfxwngg?pwd=6rla)|[Baidu](https://pan.baidu.com/s/1dmRi_x96AoFzEFot6VRTHw?pwd=k7s5)|[Baidu](https://pan.baidu.com/s/1wBGiuW31MV-onMQeScmr2A?pwd=of9b)|


## RGBD-SOD
|**Year**|**Publisher**|**Paper**|**Model**|**RDVS**|
| :-: | :-: | :-: | :-: | :-: |
|2020 | ECCV | [**BBSNet**](https://arxiv.org/pdf/2007.02713.pdf)|[Code](https://github.com/DengPingFan/BBS-Net)|[Baidu ](https://pan.baidu.com/s/1eyMummax1HQpeI2CBrWZmA?pwd=obe0)| 
|2020 | CVPR | [**JLDCF**](https://openaccess.thecvf.com/content_CVPR_2020/papers/Fu_JL-DCF_Joint_Learning_and_Densely-Cooperative_Fusion_Framework_for_RGB-D_Salient_CVPR_2020_paper.pdf)|[Code](https://github.com/kerenfu/JLDCF)\|
|2020 | CVPR | [**S2MA**](https://openaccess.thecvf.com/content_CVPR_2020/papers/Liu_Learning_Selective_Self-Mutual_Attention_for_RGB-D_Saliency_Detection_CVPR_2020_paper.pdf)|[Code](https://github.com/nnizhang/S2MAhttps://github.com/nnizhang/S2MA)|[Baidu](https://pan.baidu.com/s/1PxVWLhXL5VQjgQK-1toZtA?pwd=c3tf)\|
|2020 | ECCV | [**HDFNet**](https://arxiv.org/pdf/2007.06227.pdf)|[Code](https://github.com/lartpang/HDFNet)|[Baidu ](https://pan.baidu.com/s/1XlVARG4jUlbwW411IHq3ng?pwd=dgfi)\|
|2020 | TIP | [**DPANet**](https://ieeexplore.ieee.org/document/9247470)|[Code](https://github.com/JosephChenHub/DPANet)|[Baidu](https://pan.baidu.com/s/156frOJuJHqbkZVuYg0aybQ?pwd=ulh6)\|
|2021 | ICCV | [**SPNet**](https://openaccess.thecvf.com/content/ICCV2021/supplemental/Zhou_Specificity-Preserving_RGB-D_Saliency_ICCV_2021_supplemental.pdf)|[Code](https://github.com/taozh2017/SPNet)|[Baidu](https://pan.baidu.com/s/1RVdliC67daR_JJ44_-oYSQ?pwd=5rur)\|
|2021 | TIP | [**CDNet**](https://ieeexplore.ieee.org/document/9366409)|[Code](https://github.com/blanclist/CDNet)|[Baidu ](https://pan.baidu.com/s/1a-Eqeyf8Qvam81EZLw3Mtw?pwd=fvf1)\|
|2021 | CVPR | [**DCF**](https://openaccess.thecvf.com/content/CVPR2021/papers/Ji_Calibrated_RGB-D_Salient_Object_Detection_CVPR_2021_paper.pdf)|[Code](https://github.com/jiwei0921/DCF)|[Baidu ](https://pan.baidu.com/s/1O7heB5mgbgbMHz0pTOOFOA?pwd=aguk)\|
|2021 | ACM MM | [**TriTransNet**](https://arxiv.org/pdf/2108.03990.pdf)|[Code](https://github.com/liuzywen/TriTransNet)|[Baidu](https://pan.baidu.com/s/1AL1E8clMzPNek6kScyKzEw?pwd=svra)
|2021 | ICME | [**BTSNet**](https://arxiv.org/pdf/2104.01784.pdf)|[Code](https://github.com/zwbx/BTS-Net)|[Baidu](https://pan.baidu.com/s/1RgsWbFM2hutchErblTXJHQ?pwd=hi7x)
|2022 | TNNLS | [**RD3D**](https://ieeexplore.ieee.org/document/9889257)|Code|[Baidu](https://pan.baidu.com/s/1oLSu4jxZFaRDYeitAKJTYA?pwd=vwwf)

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
