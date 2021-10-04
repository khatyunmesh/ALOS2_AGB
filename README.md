# ALOS2_AGB
This notebook demonstrates the use of time-series L-band SAR backscatter from ALOS-2 data for extraction of forest above-ground biomass using a modified 3-parameter Water Cloud Model. 
The steps are as follows
1. The ALOS-2 data is converted to HDF5 format similar to NISAR using ISCE3
2. The ALOS-2 data is processed in ISCE3 and the backscatter over the field plots is extracted. We use an improved RTC method. In the RTC process, the plot corners are projected to radar geometry, and sub-pixel aggregation of backscatter is carried out. Further, this aggregation approach ensures that there is no mismatch between pixel size and plot size, as even partially covered pixels are weighted according to their areal coverage. [Khati et al., Remote Sensing, 2020]
3. There are many changes to the field during the 5 year ALOS-2 time-series. Many plots have been logged and many have grown. We use a simple Machine Learning method to identify these plots and remove those. Please see the method "data_clean_local" for the code
4. The time-series backscatter is modeled using the 3-parameter Water Cloud Model. This model is fitted using least-squares minimization approach. We also use the Jacobians to ensure more accuracy in parameter retrival
5. The AGB is modeled from the backscatter for each ALOS-2 acquisition.
6. We use a simple aggregation of the AGB estimates from each acquisition of the time-series to improve AGB estimates
Our results are summarized in our recently accepted publication: "Time-series L-band SAR and GEDI for forest above-ground biomass mapping of sub-tropical forest”, by Unmesh Khati*, Marco Lavalle and Gulab Singh, published in “Frontiers in Earth Science-Environmental Informatics and Remote Sensing”.
