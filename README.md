# confidence-calibration
Assess performance of human and machine probabilistic forecasts using confidence calibration and ROC curves and various metrics

A web-based version can be found at http://checkmyai.com/ 

The python notebook applies visual and numerical verification techniques available for analyzing these types of 
probabilistic forecasts, and outputs the data in the form of a confidence calibration curve, a receiver operating
characteristics (ROC) curve, and various metrics for assessing different aspects of these predictions. 

The required input data are 2 numpy arrays: truth (either 0 or 1) and forecasts (real numbers from 0 to 1, inclusive). 
We've also included a few sample files in the csvs folder to get you started. The output is a matplotlib plot element
(plt), a dictionary of metrics (metrics), and a confusion matrix (cm).

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

We also provide a way of printing out a radar plot of the metrics. First, define the array of metrics
you want to plot. The names have to correspond to metric names used by the code. We recommend the 
following order:

array_of_names=['Calibration loss','Calib-in-the-large','Confidence score',
                'Specificity','NPV','Accuracy','PPV','Sensitivity',
                'AUC','Resolution','Refinement loss',
                'Brier score loss', 'Brier skill score']


Then the data has to be reformatted as such:

data_radar=create_data_for_radar_plot(metrics,array_of_names)

Then call the function:

p=plot_radar_chart(data=data_radar,forecaster_names=['Forecaster'],plot_file_name='test')
