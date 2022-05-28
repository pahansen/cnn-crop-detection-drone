# cnn-plant-detection
University research project 2020 for CNN development

High level documentation of the development of a Convolutional-Neural-Network (CNN) including automatic labeling of training data to detect plants on agricultural fields. Research goal was to see if crops can be distinguished from weeds by a CNN using aerial images. By knowing the locations with high weed pressure, the use of pesticides could be reduced because they only need to be applied where they are actually required. Images were shot with a DJI Phantom in heights of 5m, 10m and 15m.

## Preparation of training data
Based on the aerial images, training for the CNN can be created.

![Aerial Image Example](https://github.com/pahansen/cnn-plant-detection/blob/main/aerial_image_crops.png)

However, looking at this example image it is clear that labeling every plant by hand is not feasible because hundreds of these image snippets are necessary to cover an entire agricultural field. Therefore, an automatic labeling approach was developed.

First, plants are segmented from the background into masks by leveraging index based segmentation with excessive green index + otsu thresholding. Based on the plant mask, a hough lines transformation is computed to identify crop rows. By assuming that only crop grows on crop rows and weed grows next to crop rows, all plants that intersect the hough lines can be labeled as crop.

![Hough Lines Example](https://github.com/pahansen/cnn-plant-detection/blob/main/hough_lines.png)

Image shows computed hough lines. Based on these lines, intersecting plant contours are cut from the image to generate training data.

## Main Resources for image preparation and CNN architecture
Bah, M.; Hafiane, Adel; Canals, Raphael (2018): Deep Learning with Unsupervised Data Labeling for Weed Detection in Line Crops in UAV Images. In: Remote Sensing 10 (11), p. 1690.

Lottes, Philipp; Khanna, Raghav; Pfeifer, Johannes; Siegwart, Roland; Stachniss, Cyrill (2017): UAV-based crop and weed classification for smart farming. In: 2017 IEEE International Conference on Robotics and Automation (ICRA). IEEE Inter- national Conference on Robotics and Automation (ICRA). Singapore, Singapore, 29.05 - 03.06.2017: IEEE, p. 3024–3031.

Milioto, A.; Lottes, P.; Stachniss, C. (2017): REAL-TIME BLOB-WISE SUGAR BEETS VS WEEDS CLASSIFICATION FOR MONITORING FIELDS USING CONVOLUTIONAL NEURAL NETWORKS. In: ISPRS Ann. Photogramm. Re- mote Sens. Spatial Inf. Sci.
