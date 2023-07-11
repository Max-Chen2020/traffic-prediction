### This repository contains the dataset used for the project. 

### Description: 

The experimental datasets are sourced from three platforms. The PeMSD7 dataset is collected from Caltrans Performance 
Measurement System (PeMS) website. We downloaded the data dating from 1st of May to 30th of June and selected 200 nodes in 
District 7 for experiments. The Melbourne Traffic Volume Dataset is collected from DATA VIC with 300 road links selected. 
For the Melbourne Traffic Speed dataset, we have been pulling the bluetooth travel time data from the Victorial Government 
data exchange platform since 2nd of July. To match the timestamp frequencies with the volume dataset, we aggregate each 30 
half-minute readings into one 15-minutes reading by taking the averages. Since traffic flows are directional, 
it will be inaccurate to model the volumes on an aggregated site-level. Therefore, we matched each site-detector correspondence 
to obtain link-level traffic flow, thus preserving the directional features. For all of the datasets, we adopted 
linear interpolation to impute the missing values. 
