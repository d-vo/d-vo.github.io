---
permalink: "/WACV18/"
---

## Efficient Map Compression for Collaborative Visual SLAM
*IEEE Winter Conference on Applications of Computer Vision (WACV)* \\
Lake Tahoe, USA, March 2018


## Abstract:
<p align="justify">
Swarm robotics is receiving increasing interest, because the collaborative completion of tasks, such as the exploration of unknown environments, leads to improved performance and reduced effort. The ability to exchange map information is an essential requirement for collaborative exploration. When moving to large-scale environments, where the communication data rate between the swarm participants is typically limited, efficient compression algorithms and an approach for discarding less informative parts of the map are key for a successful long-term operation. In this paper, we present a novel compression approach for environment maps obtained from a visual SLAM system. We apply feature coding to the visual information to compress the map efficiently. We make use of a minimum spanning tree to connect all features that serve as observations of a single map point. Thereby, we can exploit inter-feature dependencies and obtain an optimal coding order. Additionally, we add a map sparsification step to keep only useful map points by solving a linear integer-programming problem, which preserves the map points that exhibit both good compression properties and high observability. We evaluate the proposed method on a standard dataset and show that our approach outperforms state-of-the-art techniques.
</p>


## Motivation: 
<p align="justify">
When it comes to collaborative exploration, there are several challenges to address. In this work, we focus on two main issues: First, we address the effective compression of maps obtained from a visual SLAM system by exploiting visual similarities between observations of a map point. Second, in order to restrict unbounded growth of the visual maps in long-term operation or when fusing multiple maps, we propose to remove map points that require more bits to store the visual information. The applications are numerous: 
</p>

<ul>
  <li>Map exchange</li>
  <li>Collaborative mapping</li>
  <li>Reducing computational complexity</li>
  <li>Long-term exploration</li>
  <li>Archiving</li>
</ul>

<p align="justify">
The motivation to use the costs in terms of bits per map point (normalized by the number of attached observations) in the map sparsification problem is driven by the observation that map points with many visually similar observations need fewer bits per observation to store the visual information. Replacing the number of observations, as suggested in the related work, by the required bits favours both map points with many observation, as well as visually similar observations. 
</p>

## Approach: 

<center>
<figure>
<img src="{{ site.url }}/_pages/WACV18/assets/MST_free_eng.svg" alt="MST Illustration" width="668"/>
<figcaption>Illustration of the Minimum Spanning Tree</figcaption>
</figure>
</center>

The approach is summarized in the following: 

<ul>
  <li>Map points are created by local features in keyframes, denoted as observations</li>
  <li>Build a fully connected <b>Graph</b> (dashed green lines) to connect all observations v of a map point</li>
  <li>The weight w of the edges is the Hamming distance between two local features</li>
  <li>Use a <b>Minimum Spanning Tree</b> (solid green lines) to obtain an optimal coding order</li>
  <li>Exploit visual similarities using <b>differential feature coding</b></li>
  <li>Include the costs in bits per map point in the <b>optimization problem for map sparsification</b></li>
  <li>Reduce number of map points until target map size is reached</li>
</ul>



## Results: 

<ul>
  <li>Evaluated using ORB-SLAM2 [1] on EuroC Dataset [2]</li>
  <li><b>Lossless map compression down to 39%</b> of the original map size</li>
  <li><b>Lossy map compression by 91.7%</b> while maintaining similar relocalization capabilities compared to the full map</li>
</ul>



<table>
  <tr>
    <td>
        <center>
        <figure>
                <img src="{{ site.url }}/_pages/WACV18/assets/30MB.png" alt="Full Map" />
                <figcaption>Original map</figcaption>
        </figure>
        </center>
    </td>
    <td>
        <center>
      <figure>
        <img src="{{ site.url }}/_pages/WACV18/assets/20MB.png" alt="2.0 MB Map" />
        <figcaption>2.0 MB map</figcaption>
       </figure>
      </center>
    </td>
  </tr>
  <tr>
    <td>
        <center>
      <figure>
        <img src="{{ site.url }}/_pages/WACV18/assets/10MB.png" alt="1.0 MB Map" />
        <figcaption>1.0 MB map</figcaption>
      </figure>
      </center>
    </td>
    <td>
        <center>
      <figure>
        <img src="{{ site.url }}/_pages/WACV18/assets/05MB.png" alt='0.5 MB Map' />
        <figcaption>0.5 MB map</figcaption>
      </figure>
      </center>
    </td>
  </tr>
</table>

Resulting maps for the EuroC Machine Hall 01 Sequence [2]. Color-coding: Red: Many observations attached to map point, Black: Few observations attached to map point


## Video: 

<iframe width="832" height="468" src="https://www.youtube.com/embed/BwhpjvjcFcc" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Citation:

If you refer to our map compression approach in an academic work, please cite:
{% raw %}
        @INPROCEEDINGS{VanOpdenbosch2018
        author = {{Dominik Van Opdenbosch AND Tamay Aykut AND Martin Oelsch AND Nicolas Alt AND Eckehard Steinbach}},
        title = {{Efficient Map Compression for Collaborative Visual SLAM}},
        booktitle = {{IEEE Winter Conference on Applications of Computer Vision (WACV)}},
        month = {Mar},
        year = {2018},
        address = {{Lake Tahoe, USA}}
        }
 {% endraw %}

## References: 
<ol>
  <li>R. Mur-Artal and J. D. Tardós. <i>ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras</i>, IEEE Transactions on Robotics, vol. 33, no. 5, pp. 1255-1262, 2017</li>
  <li>M. Burri, J. Nikolic, P. Gohl, T. Schneider, J. Rehder, S. Omari, M. Achtelik and R. Siegwart, <i>The EuRoC micro aerial vehicle datasets</i>, International Journal of Robotic Research, vol. 35, no. 10, pp 1157-1163, 2016</li>
</ol>


## Contact: 
Please contact us via dominik (dot) van-opdenbosch [at] tum (dot) de using "WACV2018" as subject. 



Return to [main page](/).

