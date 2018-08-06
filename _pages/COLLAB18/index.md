---
permalink: "/COLLAB18/"
---

## Collaborative Visual SLAM for Heterogeneous Robotic Exploration Teams using Compressed Feature Exchange
*Under review* \\
Munich, Germany, July 2018

### Abstract:
<p align="justify">
In the field of robotics, collaborative Simultaneous Localization and Mapping (SLAM) is still a challenging problem. The exploration of unknown large-scale environments benefits from the joint exploration with multiple agents equipped with different abilities, such as aerial or ground-based vehicles. However, the computational capabilities and energy constraints differ significantly depending on the agent type. In this letter, we address the issue of efficient collaborative mapping by a heterogeneous robotic team using visual SLAM. We propose a system architecture, where the energy constrained team members extract local binary features and send a compressed version over a network to a more powerful team member which is capable of running several visual SLAM instances in parallel. In addition, we propose to use the information from nearby agents by detecting overlap between already mapped areas and subsequent merging of the maps. Henceforth, the participants contribute to a joint global map representation and benefit from shared map information. To this end, we extend a compression scheme for local binary features by exploiting the spatial relations between views obtained by a stereo camera system and implement a collaborative mapping scheme. We demonstrate the effectiveness of both the feature compression approach and the collaborative mapping strategy on the well-known KITTI dataset. 
</p>

## Approach: 
The approach is summarized in the following: 

<ul>
  <li>We extend our feature coding framework [1] to support multi-view coding</li>
  <li>We propose an architecture, where local features are extracted at thin agents, encoded and transmitted to base agents</li>
  <li>The base agents run multiple visual SLAM instances in parallel</li>
  <li>A collaborative mapping is achieved through a map merging module</li>
</ul>

Our system is based on ORB-SLAM2 [2] and we evaluated our approach on the KITTI dataset [3] and the Euroc dataset [4].

### Supplementary Material: 
<p align="justify">
Here, we show additional material not included in the paper. First, we show the resulting trajectories of our experiment by splitting KITTI 00 into three disjunct parts. The ground truth is shown alongside the trajectory estimated by our collaborative approach. 
</p>

<table>
  <tr>
    <td width="50%">
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Kitti/kitti00-1.svg" alt="Kitti 00-1" />
                <figcaption>KITTI 00-1</figcaption>
        </figure>
        </center>
    </td>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Kitti/kitti00-2.svg" alt="Kitti 00-2" />
                <figcaption>KITTI 00-2</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Kitti/kitti00-3.svg" alt="Kitti 00-3" />
                <figcaption>KITTI 00-3</figcaption>
      </figure>
      </center>
    </td>
    <td width="50%">
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Kitti/Eyecatcher3.png" alt="Kitti Map" />
                <figcaption>Collaborative Map</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
Next, we show the evaluation of our feature coding framework on the Euroc dataset. First we evaluate the sequence with the I+S+M+P and one reference frame for the P mode: 
</p> 

<table>
  <tr>
    <td>
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r1/numBitsLeftView.svg" alt="Bits per cofing mode left view" />
                <figcaption>a) Bits per coding mode for left view</figcaption>
        </figure>
        </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r1/numBitsRightView.svg" alt="Bits per cofing mode right view" />
                <figcaption>b) Bits per coding mode for right view</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r1/numFeaturesLeftView.svg" alt="Percentage of used coding modes left view" />
                <figcaption>c) Percentage of used coding modes for the left view</figcaption>
      </figure>
      </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r1/numFeaturesRightView.svg" alt="Percentage of used coding modes right view" />
                <figcaption>d) Percentage of used coding modes for the right view</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
Next, we evaluate the sequence with the I+S+M+P and four reference frames for the P mode: 
</p>

<table>
  <tr>
    <td>
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r4/numBitsLeftView.svg" alt="Bits per cofing mode left view" />
                <figcaption>a) Bits per coding mode for the left view</figcaption>
        </figure>
        </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r4/numBitsRightView.svg" alt="Bits per cofing mode right view" />
                <figcaption>b) Bits per coding mode for the right view</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r4/numFeaturesLeftView.svg" alt="Percentage of used coding modes left view" />
                <figcaption>c) Percentage of used coding modes for the left view</figcaption>
      </figure>
      </center>
    </td>
    <td>
      <center>
      <figure>
                <img src="{{ site.url }}/_pages/COLLAB18/assets/Euroc/r4/numFeaturesRightView.svg" alt="Percentage of used coding modes right view" />
                <figcaption>d) Percentage of used coding modes for the right view</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

<p align="justify">
When changing from a single to four reference frames, the inter-coding mode is used more frequently (compare figures c+d). The encoding time increases from 16.38 ms to 22.46 ms. The measurements were performed on an Intel i7-7700 CPU @ 3.60GHz, with 1200 features per frame (ORB-SLAM2 default settings).
</p>

### Source Code:

We plan to release the source code upon publication. 

Please contact us via dominik (dot) van-opdenbosch [at] tum (dot) de using "COLLAB2018" as subject.

## References: 
<ol>
  <li>D. Van Opdenbosch, M. Oelsch, A. Garcea, T. Aykut, E. Steinbach, <i>Selection and Compression of Local Binary Features for Remote Visual SLAM</i>, IEEE International Conference on Robotics and Automation (ICRA), 2018</li>
  <li>R. Mur-Artal and J. D. Tardós, <i>ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras</i>, IEEE Transactions on Robotics, vol. 33, no. 5, pp. 1255-1262, 2017</li>
  <li>A. Geiger, P. Lenz, R. Urtasun, <i>Are we ready for autonomous driving? The KITTI vision benchmark suite</i>, IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 3354-3361, 2012</li>
  <li>M. Burri, J. Nikolic, P. Gohl, T. Schneider, J. Rehder, S. Omari, M. Achtelik and R. Siegwart, <i>The EuRoC micro aerial vehicle datasets</i>, International Journal of Robotic Research, vol. 35, no. 10, pp 1157-1163, 2016</li>
</ol>


Return to [main page](/).