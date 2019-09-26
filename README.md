# confidence-calibration
Assess performance of human and machine probabilistic forecasts using confidence calibration and ROC curves and various metrics

The analysis methods we use can be divided into discrimination tests (e.g., sensitivity, specificity) and calibration tests. 
Calibration tests follow a group of probabilistic predictions to determine how well the predictions correspond to reality.
Take the example of a weather forecaster making probabilistic predictions about the chance of rain. Let's say over the course of 
a year, he makes 100 forecasts of there being a 20% chance of rain the following day. We collect all these forecasts and check 
to see whether or not it rained the following day. If the forecaster is well-calibrated, then we expect there to be 20 days of 
rain out of those 100 days. Repeating the same process for his 40%, 60%, and 80% predictions of rain, we expect to see rain 
on 40, 60, and 80 of those 100 days, respectively.

The python notebook applies visual and numerical verification techniques available for analyzing these types of 
probabilistic forecasts, and outputs the data in the form of a confidence calibration curve, a receiver operating characteristics
(ROC) curve, and various metrics for assessing different aspects of these predictions. 
