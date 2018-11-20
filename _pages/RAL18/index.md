---
permalink: "/RAL18/"
---

## Collaborative Visual SLAM using Compressed Feature Exchange
*IEEE Robotics and Automation Letters* \\
Munich, Germany, January 2019, [Preprint LMT](https://intern.lkn.ei.tum.de/forschung/publikationen/dateien/Van%20Opdenbosch2019CollaborativeVisualSLAMusing.pdf), [IEEE](https://ieeexplore.ieee.org/document/8516392/)

## Abstract:
<p align="justify">
In the field of robotics, collaborative Simultaneous Localization and Mapping (SLAM) is still a challenging problem. The exploration of unknown large-scale environments benefits from sharing the work among multiple agents possibly equipped with different abilities, such as aerial or ground-based vehicles. In this letter, we specifically address data-efficiency for the exchange of visual information in a collaborative visual SLAM setup. For efficient data exchange, we extend a compression scheme for local binary features by two additional modes providing support for local features with additional depth information and an inter-view coding mode exploiting the spatial relations between views of a stereo camera system. To demonstrate the coding framework, we use a centralized system architecture based on ORB-SLAM2, where energy constrained agents extract local binary features and send a compressed version over a network to a more powerful agent, which is capable of running several visual SLAM instances in parallel. We exploit the information from other agents by detecting overlap between already mapped areas and subsequent merging of the maps. Henceforth, the participants contribute to a joint representation and benefit from shared map information. We show a reduction in terms of data-rate by 70.8 % for the feature compression and a reduction in absolute trajectory error by 53.7 % using the collaborative mapping strategy on the well-known KITTI dataset. For the benefit of the community, we provide a public version of the source code.
</p>

<center>
<figure>
        <img src="{{ site.url }}/_pages/RAL18/assets/Scenario3_web.png" alt="Scenario" width="540" />
        <figcaption>heterogeneous robot team</figcaption>
</figure>
</center>

<p align="justify">
In addition, we propose to use the information from nearby agents by detecting overlap between already mapped areas and subsequent merging of the maps. Henceforth, the participants contribute to a joint global map representation and benefit from shared map information. To this end, we extend a compression scheme for local binary features by exploiting the spatial relations between views obtained by a stereo camera system and implement a collaborative mapping scheme. We demonstrate the effectiveness of both the feature compression approach and the collaborative mapping strategy on the well-known KITTI dataset. 
</p>



## Approach: 
The approach is summarized in the following: 

<ul>
  <li>We extend our feature coding framework [1] to support depth value coding</li>
  <li>We complete the feature coding framework by supporting multi-view coding</li>
  <li>We demonstrate the compression in a centralized collabortive visual SLAM architecture.</li>
</ul>



Our system is based on ORB-SLAM2 [2] and we evaluated our approach on the KITTI dataset [3] and the Euroc dataset [4]. Our feature coding framework is based on [1] and adds a depth value and a stereo coding mode. 

<center>
<figure>
        <img src="{{ site.url }}/_pages/RAL18/assets/Overview_free.svg" alt="Overview" width="875" />
        <figcaption>Proposed improved binary feature coding framework</figcaption>
</figure>
</center>

## Video: 

<iframe width="832" height="468" src="https://www.youtube.com/embed/_Jhf5a5Z0vg" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

### Supplementary Material: 

<p align="justify">
Here, we show additional material not included in the paper. First, we show the resulting trajectories of our experiment by splitting KITTI 00 into three disjunct parts. The ground truth is shown alongside the trajectory estimated by our collaborative approach. 
</p>

<table>
  <tr>
    <td width="50%">
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Kitti/Kitti00-1.svg" alt="Kitti 00-1" />
                <figcaption>KITTI 00-1</figcaption>
        </figure>
        </center>
    </td>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Kitti/Kitti00-2.svg" alt="Kitti 00-2" />
                <figcaption>KITTI 00-2</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Kitti/Kitti00-3.svg" alt="Kitti 00-3" />
                <figcaption>KITTI 00-3</figcaption>
      </figure>
      </center>
    </td>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Kitti/Eyecatcher3.png" alt="Kitti Map" />
                <figcaption>Collaborative Map</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
Next, we show the evaluation of our feature coding framework on the Euroc dataset V101 sequence. First we evaluate the sequence with the I+S+M+P and one reference frame for the P mode. For the left view, we added the costs for coding the depth information, as used for the monocular version.  
</p> 

<table>
  <tr>
    <td>
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r1/numBitsLeftView.svg" alt="Bits per cofing mode left view" />
                <figcaption>a) Bits per coding mode for the left view</figcaption>
        </figure>
        </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r1/numBitsRightView.svg" alt="Bits per cofing mode right view" />
                <figcaption>b) Bits per coding mode for the right view</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r1/numFeaturesLeftView.svg" alt="Percentage of used coding modes left view" />
                <figcaption>c) Percentage of used coding modes for the left view</figcaption>
      </figure>
      </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r1/numFeaturesRightView.svg" alt="Percentage of used coding modes right view" />
                <figcaption>d) Percentage of used coding modes for the right view</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
Next, we evaluate the sequence with the I+S+M+P and four reference frames for the P mode. Again, the left view has additionally the depth values included. 
</p>

<table>
  <tr>
    <td>
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r4/numBitsLeftView.svg" alt="Bits per cofing mode the left view" />
                <figcaption>a) Bits per coding mode for the left view</figcaption>
        </figure>
        </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r4/numBitsRightView.svg" alt="Bits per cofing mode the right view" />
                <figcaption>b) Bits per coding mode for the right view</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r4/numFeaturesLeftView.svg" alt="Percentage of used coding modes left view" />
                <figcaption>c) Percentage of used coding modes for the left view</figcaption>
      </figure>
      </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/RAL18/assets/Euroc/r4/numFeaturesRightView.svg" alt="Percentage of used coding modes right view" />
                <figcaption>d) Percentage of used coding modes for the right view</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
Next, timings are provided for the Euroc dataset V101 sequence:
</p>


<div style="font-size:small;">
<table align="center">
  <tr>
        <td style="text-align: center; vertical-align: middle;">Stereo</td>
        <td style="text-align: center; vertical-align: middle;"><b>I</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+M</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+P<sub>1</sub>+S</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+P<sub>1</sub>+S+M</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+P<sub>4</sub>+S+M</b></td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">ORB</td>
        <td style="text-align: center; vertical-align: middle;" colspan="5">14.5 ms</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">encoding</td>
        <td style="text-align: center; vertical-align: middle;">11.5 ms</td>
        <td style="text-align: center; vertical-align: middle;">12.8 ms</td>
        <td style="text-align: center; vertical-align: middle;">15.6 ms</td>
        <td style="text-align: center; vertical-align: middle;">16.4 ms</td>
        <td style="text-align: center; vertical-align: middle;">26.3 ms</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">decoding</td>
        <td style="text-align: center; vertical-align: middle;">12.6 ms</td>
        <td style="text-align: center; vertical-align: middle;">13.3 ms</td>
        <td style="text-align: center; vertical-align: middle;">13.8 ms</td>
        <td style="text-align: center; vertical-align: middle;">13.9 ms</td>
        <td style="text-align: center; vertical-align: middle;">13.5 ms</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">bits/feature</td>
        <td style="text-align: center; vertical-align: middle;">224.5</td>
        <td style="text-align: center; vertical-align: middle;">208.9</td>
        <td style="text-align: center; vertical-align: middle;">170.4</td>
        <td style="text-align: center; vertical-align: middle;">165.3</td>
        <td style="text-align: center; vertical-align: middle;">151.5</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">#features</td>
        <td style="text-align: center; vertical-align: middle;">2x1.2k</td>
        <td style="text-align: center; vertical-align: middle;">2x1.2k</td>
        <td style="text-align: center; vertical-align: middle;">2x1.2k</td>
        <td style="text-align: center; vertical-align: middle;">2x1.2k</td>
        <td style="text-align: center; vertical-align: middle;">2x1.2k</td>
  </tr>
</table>
</div>

<p align="justify">
Next, we present the results for Mono+Depth
</p>

<div style="font-size:small;">
<table align="center">
  <tr>
        <td style="text-align: center; vertical-align: middle;">Mono+Depth</td>
        <td style="text-align: center; vertical-align: middle;"><b>I+D</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+P<sub>1</sub>+S+D</b></td>
        <td style="text-align: center; vertical-align: middle;"><b>I+P<sub>4</sub>+S+D</b></td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">encoding</td>
        <td style="text-align: center; vertical-align: middle;">7.7 ms</td>
        <td style="text-align: center; vertical-align: middle;">9.8 ms</td>
        <td style="text-align: center; vertical-align: middle;">13.4 ms</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">decoding</td>
        <td style="text-align: center; vertical-align: middle;">8.6 ms</td>
        <td style="text-align: center; vertical-align: middle;">8.9 ms</td>
        <td style="text-align: center; vertical-align: middle;">8.9 ms</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">bits/feature</td>
        <td style="text-align: center; vertical-align: middle;">230.1</td>
        <td style="text-align: center; vertical-align: middle;">175.8</td>
        <td style="text-align: center; vertical-align: middle;">160.1</td>
  </tr>
  <tr>
        <td style="text-align: center; vertical-align: middle;">#features</td>
        <td style="text-align: center; vertical-align: middle;">1.2k</td>
        <td style="text-align: center; vertical-align: middle;">1.2k</td>
        <td style="text-align: center; vertical-align: middle;">1.2k</td>
  </tr>
</table>
</div>


<p align="justify">
When changing from a single to four reference frames, the inter-coding mode is used more frequently (compare figures c+d). The encoding time increases from 16.4 ms to 26.3 ms. The measurements were performed on an Intel i7-7700 CPU @ 3.60GHz, with 1200 features per frame (ORB-SLAM2 default settings).
</p>


## Citation:

If you refer to our map compression approach in an academic work, please cite:

{% raw %}
	@article{VanOpdenbosch2019,
	author = {{Van Opdenbosch}, Dominik and Steinbach, Eckehard},
	journal = {IEEE Robotics and Automation Letters (RAL)},
	number = {1},
	pages = {57--64},
	title = {{Collaborative Visual SLAM using Compressed Feature Exchange}},
	volume = {4},
	year = {2019}
	}
 {% endraw %}

Preprint is available online at IEEE [here](https://ieeexplore.ieee.org/document/8516392/)



## Source Code:

The source code for the collaborative visual SLAM system can be found [here](https://github.com/d-vo/collab_orb_slam2).\\
The binary feature compression pipeline can be found [here](https://github.com/d-vo/featureCompression2).

Please contact us via dominik (dot) van-opdenbosch [at] tum (dot) de using "RAL2018" as subject.

## Knwon Issues:

The two images in Figure 5 are mixed up. 


## References: 
<ol>
  <li>D. Van Opdenbosch, M. Oelsch, A. Garcea, T. Aykut, E. Steinbach, <i>Selection and Compression of Local Binary Features for Remote Visual SLAM</i>, IEEE International Conference on Robotics and Automation (ICRA), 2018</li>
  <li>R. Mur-Artal and J. D. Tardós, <i>ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras</i>, IEEE Transactions on Robotics, vol. 33, no. 5, pp. 1255-1262, 2017</li>
  <li>A. Geiger, P. Lenz, R. Urtasun, <i>Are we ready for autonomous driving? The KITTI vision benchmark suite</i>, IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 3354-3361, 2012</li>
  <li>M. Burri, J. Nikolic, P. Gohl, T. Schneider, J. Rehder, S. Omari, M. Achtelik and R. Siegwart, <i>The EuRoC micro aerial vehicle datasets</i>, International Journal of Robotic Research, vol. 35, no. 10, pp 1157-1163, 2016</li>
</ol>


Return to [main page](/).
