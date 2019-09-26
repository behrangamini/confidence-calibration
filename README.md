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

The required input data are 2 python arrays: truth (either 0 or 1) and forecasts (real numbers from 0 to 1, inclusive). We've also 
included a few sample files in the csvs folder to get you started. The output is a matplotlib plot  element (plt), a dictionary of 
metrics (metrics), and a confusion matrix (cm).

Optional inputs are:
-plot_ci: Plot confidence intervals on the calibration curve (true by default)
-plot_isoskill: Plot iso-skill lines on the calibration curve (false by default)
-nplots: Whether to plot the calibration curve, the ROC and the metrics (nplots=3) or just the curves (nplots=2)
-fig_title: Optional title for the figure (blank by default)
-n_bins: Number of bins for the calibration curve (20 by default)


To get started, load one of the csv files as below:

d=np.loadtxt(open("csvs/well_calibrated_sharp.csv", "rb"), delimiter=",", skiprows=1)

truth = d[:,0]
forecast= d[:,1]

(plt,metrics,cm)=plot_calib_results(truth, forecast, plot_ci=True, plot_isoskill=False, nplots=3, fig_title="",n_bins=20)
plt.show()
