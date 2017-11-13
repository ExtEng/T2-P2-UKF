## Term 2 - Project 2 : Unscented Kalman Filter  
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

In this project, my goal was to use the techniques and code examples presented in the Udacity course to estimate the position of a car using an Unsected Kalman Filter and provided Lidar/radar sensor data.  

The goals / steps of this project are the following:
- Complete the UKF Algorithm 
- Achieve a RSME value <[.09, .09, 0.65, 0.65], [0.20, 0.20, 0.55, 0.55] for datasets 1 & 2 respectively
- Use NIS for tuning
- Test Estimation RSME for Dataset 1
  - Using only Radar data
  - Using only Laser Data
- Comparision between EKF & UKF

[//]: # (Image References)

[image1]: ./Output/Final_Data_1_Both_trial_2_a_2_yawdd_0.5.jpg "Position Estimation - Using Sensor Fusion - UKF"
[image2]: ./Output/Final_Data_2_Both_trial_2_a_2_yawdd_0.5.jpg "Position Estimation - Using Sensor Fusion - UKF"
[image3]: ./Output/NIS_Final_data_1.jpg "Final NIS for Dataset 1"  
[image4]: ./Output/NIS_Final_data_2.jpg "Final NIS for Dataset 3" 
[image5]: ./Output/Radar_data_only.jpg "Position Estimation - Radar UKF"
[image6]: ./Output/Laser_data_only.jpg "Position Estimation - Laser UKF"
[image7]: ./Output/EKF_Dataset_1-BothSensors.jpg "Position Estimation - Using Sensor Fusion - EKF"

## Final Results
After implementing the UKF algorithm, the NIS Values were used to tune and verify the process noise parameters (Std_a_ = 2 ; std_yawdd_ = 0.5). The final results of Dataset 1 yielded a 95% percentile of 7.34178 (Radar) & 5.10503 (Laser), which compared well to the desired values of 7.82 (Radar, n=3) & 	5.99 (Laser, df =2). See below for a illustration of Dataset 1 run and its respective NIS.

![alt text][image1]

![alt text][image3]

The final results of Dataset 2 yielded a 95% percentile of 7.21353 (Radar) & 5.79358 (Laser), which compared well to the desired values of 7.82 (Radar, n=3) & 5.99 (Laser, df =2).. See below for a illustration of the run and its respective NIS.

![alt text][image2]
![alt text][image4]

From Dataset 1 - Laser UKF Only, achieved good position tracking accuracy, but not as good as the sensor fusion implementation.

![alt text][image6]


From Dataset 1 - Radar UKF Only, achieved position tracking reasonably well, but not as good as the sensor fusion implementation or the Laser UKF Implementation. Which considering each sensor's Measurement noise, was the expected behavior. 

![alt text][image7]

From comparing EKF's results to the Final UKF results for Dataset 1, the performace was found to be greater as expected. This would be attributed to error introduced by the linealization approach in the EKF implementation and the use of the CRTV model which models the expected behavior of a car/bicycle better on turns. 

![alt text][image7]
