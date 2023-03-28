# Meeting 3

**Date:** 2023.02.28

**Time:** 2 - 3pm, 3 - 3:30pm

**Location and Supervisors:** Melbourne Connect 2101 with Dr. Lele Zhang and Dr. Tingjing Chu, Zoom Online with Dr. Jianzhong Qi 

## Agenda

### Problem Formuation 

In plain language, the problem of traffic prediction can be stated as: given a historial time-series of traffic condition along with the road network information,
find a functional mapping to predict the future traffic condition in a specified time range. Mathematically, denote the number of nodes in a road network as m, the number of traffic state features of interest
as n, the traffic condition matrix at timestamp t at a specified location as $X_t \in \mathbb{R}^{m \times n}$. The problem could be formulated as follows:

$$ f([X_{t-n}, ..., X_{t-1}, X_t], G) = [X_t, X_{t+1} ... X_{t+n}] $$ 

To ensure generality, most literature denote $X$ as a matrix rather than a vector. However, the variable of concern is mainly monotonic, typically speed or flow only.
Thus, $X_t \in \mathbb{R}^{m \times n}$ can be indeed regarded as $X_t \in \mathbb{R}^{m \times 1}$, which is a vector of speed/flow at different nodes in the road network. 
Based on the idea that there is a relationship between traffic volume and speed and that the variables may reinforce each other during model prediction, 
the new problem could be formulated as follows:

$$ f([X_{t-n}, ..., X_{t-1}, X_t], [Z_{t-n}, ..., Z_{t-1}, Z_t], G) = ([X_t, X_{t+1} ... X_{t+n}], [Z_t, Z_{t+1} ... Z_{t+n}]) $$ 

where $X_t \in \mathbb{R}^{m \times 1}$ and $Z_t \in \mathbb{R}^{m \times 1}$ are volume and speed vectors at different locations and G is the road network information. We can of course combine the
two vectors as a general matrix $X_t \in \mathbb{R}^{m \times 2}$, the above definition just emphasizes the difference between our approach and the traditional ones. 

### Fundamental relationship to add to the model 

Based on suggestions from Dr. Qi, the fundamental relationship between traffic volume and speed could be incorporated into the loss function of the deep learning model, instead of
adding an extra relationship variable in the problem definition. It is also pointed out that the combined loss function should be differentiable. It would be a problem if the loss
function with the fundamental relatinship equations involved is not differentiable. 

### Potential issues with the volume data

Previous literature mostly considers the overall volume of intersections/roads instead of counting different lanes in different directions separately. This would not be a problem when the variable of concern is
only speed on highway but would be problematic when it comes to volumes in complex road networks. Blending volumes in different directions of lanes would make
the forecasting results less indicative, as well as weakening the effectiveness of leveraging relationship between speed and volume. 

### Research design 

There are two simple ways to approach the problem. The first one is to feed all the data (including speed, volume, and spacial information) directly into one model
and output a matrix containing the predicted information regarding the two variables. The other one is to feed speed and volume data separately and fuse the two
together at some stage to obtain the final result. A meeting with Dr. Gong might be needed to discuss about the detailed model architecture design. 

## Next Steps
- Learn to use QGIS to extract layer information, and investigate into the connectivity and proximity between nodes and links
- Try to run existing models on google colab or Spartan
- Write research proposal 
- Consult with Dr. Gong about model architecture 

## Conclusion
- Dr. Zhang and Dr. Qi have provided valuable suggestions on general research directions and implementation details, which is valuable and greatly appreciated.  
