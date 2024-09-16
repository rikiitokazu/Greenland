# Greenland Project 🏔️


## Analysis of Greenland Lakes: Volumes and Water Coverage 
* 📚 Riki Itokazu, Professor Behn, Professor Willis
* 📍 Boston College Data Visualization Lab
* 🛰️ Using Sentinel-2 Data
* 🗾 Region of Interest: ~68º43’N 49º30’W.


## Technologies 💻
* Python
  - Libraries: scikit-learn, cv2, matplotlib, pandas, numpy
* ArcGIS
* SQL

## Slope Analysis
During the summer, the ice sheet that covers Greenland can quickly melt, causing large bodies of water to form.
We wanted to explore the behavior of the melting and draining of these lakes, as well as different factors that may influence these patterns. How does elevation play a role? Can we calculate the velocities of the water when they are drained? Around what month(s) do we tend to see the most water?


This [ArcticDEM website](https://www.pgc.umn.edu/data/arcticdem/) contains elevation models across different timestamps. We imported these raster files directly into ArcGIS that allowed us to analyze the elevation at different points. We examined two lakes in our regin of interest (North and South Lake) and analyzed their behaviors over time. Using ArcGIS's slope analysis, we were able to dictate how "deep" the lakes are at different times. 

As expected, we determined that when the lakes drained the most around late June, giving us depths of approximately 30-40 meters. The lakes would slowly start to make a uniform elevation. 

## Volume Analysis
Similarly, we were able to use the elevation models to determine the model. This was done using the [contour tool](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/contour.htm) in ArcGIS. The contour in conjunction with the image allowed us to determine the outlines of the lakes. After picking out the specific outline that corresponds with the lake, we used the [Surface Volume](https://pro.arcgis.com/en/pro-app/latest/tool-reference/3d-analyst/surface-volume.htm) to calculate the 3-d volume of the region. This was done by placing an imaginary "z-axis" over the lake. From there, we would calculate the volume below this imaginary plane. The results we found for the volumes of North & South lake aligned with the results of a previous research paper that calculated the same lakes. [Link](https://www.nature.com/articles/nature14480)

| Lake  | Date | Volume |
| ------------- | ------------- | ------------------------ |
| North  | May 1, 2022 | 0.005769 ± 0.0003174 km3  |
| North  | August 28, 2022 | 0.007824 ± 0.0003429 km3 |
| South | May 1, 2022 | 0.009310 ± 0.0002050 km3 |
| South | August 28, 2022 | 0.01320 ± 0.0002473 km3 |

## Coverage of Water 
Using unsupervised classification techniques, we were able to determine the total amount of water that covered a region. This is extremely helpful information as it helped us determine at what month(s) did draining occur the most, and also how elevation would play a role in the draining. 

We used a variety of methods:
1) ArcGIS's built in unsupervised classification
2) Python cv2 library to detect the range of "blue" colors compared to "non-blue" colors
3) K-means clustering to cluster an image into pixels and determine which pixels correspond to water

## Repository Structure
```bash
├── SlopeAnalysis 
│   ├── Unsupervised.ipynb 
│   ├── UnsupervisedWithSig.ipynb 
│   ├── Kmeans.ipynb 
│   ├── Vision.ipynb 
├── Classification 
│   ├── ElevationDifferences.ipynb 
│   ├── NorthSlopeAnalysis.ipynb 
│   ├── SouthSlopeAnalysis.ipynb 
├── Miscellaneous  
│   ├── Visualizations 
│   ├── Data
│   ├── Pictures 
└── .gitignore
```

