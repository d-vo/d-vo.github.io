---
permalink: "/ICRA18/"
---

## Selection and Compression of Local Binary Features for Remote Visual SLAM
*IEEE International Conference on Robotics and Automation (ICRA)* \\
Brisbane, Australia, Mai 2018

### Abstract:
<p align="justify">
In the field of autonomous robotics, Simultaneous Localization and Mapping (SLAM) is still a challenging problem. With cheap visual sensors attracting more and more attention, various solutions to the SLAM problem using visual cues have been proposed. However, current visual SLAM systems are still computationally demanding, especially on embedded devices. In addition, collaborative SLAM approaches emerge using visual information acquired from multiple robots simultaneously to build a joint map. 
</p>

<center>
<figure>
        <img src="{{ site.url }}/_pages/ICRA18/assets/Scenario3_web.png" alt="Scenario" width="480" />
        <figcaption>Heterogeneous robot team</figcaption>
</figure>
</center>

<p align="justify">
In order to address both challenges, we present an approach for remote visual SLAM where local binary features are extracted at the robot, compressed and sent over a network to a centralized powerful processing node running the visual SLAM algorithm. 
</p>

<center>
<figure>
        <img src="{{ site.url }}/_pages/ICRA18/assets/Loop_free_eng.png" alt="Architecture" width="600"/>
        <figcaption>Proposed system architecture</figcaption>
</figure>
</center>

<p align="justify">
To this end, we propose a new feature coding scheme including a feature selection stage which ensures that only relevant information is transmitted. We demonstrate the effectiveness of our approach on well-known datasets. With the proposed approach, it is possible to build an accurate map while limiting the data rate to 75 kbits/frame. 
</p>

<center>
<figure>
        <img src="{{ site.url }}/_pages/ICRA18/assets/Overview_nostereo_free_eng.png" alt="Overview" width="668" />
        <figcaption>Proposed binary feature coding framework</figcaption>
</figure>
</center>

### Supplementary Material: 

We have tested our code using as encoding hardware a Core i5-6400HQ:

<font size="1">
<table width="100%">
  <tr> 
    <td></td>
    <td><b>75 kbit/s (r=1)</b></td>
    <td><b>0.5K feat (r=1)</b></td>
    <td><b>1K feat (r=1)</b></td>
    <td><b>75 kbit/s (r=4)</b></td>
    <td><b>0.5K feat (r=4)</b></td>
    <td><b>1K feat (r=4)</b></td>
  </tr>
  <tr>
    <td><b>ORB</b></td>
    <td colspan="6"><div align="center">12.1 ms</div></td>
  </tr>
  <tr> 
      <td><b>Encoding Time</b></td>
      <td>9.9 ms</td>
      <td>9.6 ms</td>
      <td>16.5 ms</td>
      <td>15.0 ms</td>
      <td>15.1 ms</td>
      <td>23.4 ms</td>
  </tr>
</table>
 </font>


We have tested our code using as decoding hardware a Core i7-3770:

<font size="1">
<table width="100%">
  <tr> 
    <td></td>
    <td><b>75 kbit/s (r=1)</b></td>
    <td><b>0.5K feat (r=1)</b></td>
    <td><b>1K feat (r=1)</b></td>
    <td><b>75 kbit/s (r=4)</b></td>
    <td><b>0.5K feat (r=4)</b></td>
    <td><b>1K feat (r=4)</b></td>
  </tr>
   <tr> 
     <td><b>Decoding Time</b></td>
     <td>12.8 ms</td>
     <td>12.6 ms</td>
     <td>24.5 ms</td>
     <td>14.1 ms</td>
     <td>12.0 ms</td>
     <td>23.5 ms</td>
  </tr>
  <tr> 
     <td><b>Tracking Time</b></td>
     <td>12.8 ms</td>
     <td>12.4 ms</td>
     <td>19.2 ms</td>
     <td>13.5 ms</td>
     <td>12.1 ms</td>
     <td>19.9 ms</td>
  </tr>
</table>
</font>

<p align="justify">
Please note that these results are obtained from single runs independent from the results presented in the paper. Timings and also the  RMSE trajectory error are dependent on many factors. Please note that 75 kbit/s almost provide 500 features/frame for 1 reference frame and about 600 features/frame for 4 reference frames. 
</p>

## Citation:

If you refer to our map compression approach in an academic work, please cite:
{% raw %}
        @INPROCEEDINGS{VanOpdenbosch2018
        author = {{Dominik Van Opdenbosch AND Martin Oelsch AND Adrian Garcea AND Tamay Aymut AND Eckehard Steinbach}},
        title = {{Selection and Compression of Local Binary Features for Remote Visual SLAM}},
        booktitle = {{IEEE International Conference on Robotics and Automation (ICRA)}},
        month = {May},
        year = {2018},
        address = {{Brisbane, Australia}}
        }
 {% endraw %}

### Source Code:

Our modified ORB-SLAM2 version can be found [here](https://github.com/d-vo/remote_orb_slam2).\\
The binary feature compression pipeline can be found [here](https://github.com/d-vo/featureCompression).\\
We plan to release an updated version in late 2018. 

Please contact us via dominik (dot) van-opdenbosch [at] tum (dot) de using "ICRA2018" as subject.



Return to [main page](/).
