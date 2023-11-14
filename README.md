
# ECG_Analyze
Import your raw ECG timeseries and export several metrics such as BPM and Heart Rate Variability (HRV) measures both in the time and frequency domains.

HOW TO INSTALL
Download the ECG_Analyzer.mlappinstall file and double click on it.

MAIN INTERFACE
On the left hand, you can find interactive tools to import and preprocess your data.
In the middle, three plots are shown: 
•	the top plot shows the raw imported data; 
•	the middle plot shows both raw (blue) and filtered (yellow) data, together with the detected peaks (grey circles); 
•	the bottom plot shows the inter-beat-interval (IBI) timeseries (red) derived by the peak detection processing.
On the right hand, you can find interactive buttons to add/remove peaks from the list of detected peaks, as well as a tab with exporting options.

HOW TO USE
1 - Load ECG data from a .mat file or directly from your Matlab workspace
Input: must be a single vector of double/single values containing your ECG signal.
Important: before importing your datafile, check the samplig rate of your recording and adjust the scroll-down value accordingly in the Import data tab.
If you click on "Import from file..." button, the raw data will be imported from the .mat file.
If you click on "Read workspace variables..." button, all the variables present in your workspace will be listed in the box below. Just select the variable with your ECG signal and click on the "Import from workspace" button.

2 - Preprocess your data and automatically detect peaks
Set filter parameters for filtering your raw data (high- and low-pass cutoffs, filter steepness and stopband attenutation).
Set parameters to find the peaks. Peak finding algoritmh is implemented via wavelet methods as described here.
Click on "Apply and Plot" button.
Detected peaks will be plotted as grey circles in the middle panel.

3 - Manually edit detected peaks
You can add new peaks or remove those you consider ectopic by simply click "Add" or "Remove" buttons on the right hand of the middle plot:
•	To add a new peak, select the point(s) on the middle plot corresponding to the x-axis coordinate of the new peak you want to add. You can click on any point of either the blue (raw) or the yellow (filtered) line. Once you selected the point(s) corresponding to the x-axis coordinates you want to add, just click on the "Add" button.
•	To remove a peak you think has been wrongly detected, just select the corresponding grey circle(s) and click on the "Remove" button.

4 - Export your results
By clicking on the "Export to workspace" button, you will export directly to your workspace a structure containing several metrics extracted from your ECG datafile. The structure contains 15 fields:
•	rawData: the same raw data vector received as input
•	filteredData: the filtered data as displayed in yellow in the middle plot
•	peakLocs: a vector of numbers indicating the time (in sec) at which each peak occurred
•	BPM: beats per minute in your recording
•	RR: a vector containing the IBI timeseries as displayed in the bottom plot
•	Four measures of HRV in the time domain (SDNN. RMSSD, IBI, pNN50)
•	Five metrics of HRV in the frequency domain: 
  1 - "pLF": low frequency power (0.04 to 0.15 Hz)
  2 - "pHF": high frequency power (0.15 to 0.40 Hz)
  3 - "rpLF": relative low frequency power (expressed in percentage)
  4 - "rpLHF": relative high frequency power (expressed in percentage)
  5 - "LF_HF_ratio": ratio between low and high frequency components of the signal
•	newSR: the sampling rate at which you chose to export the IBI timeseries
Note: All the exported metrics are based on the IBI timeseries: up- or down-sampling the IBI timeseries will affect these metrics
For more info about ECG HRV parameters see this paper.

You can set the name of the variable which will be exported to your Matlab workspace by editing the "Exported Variable Name" field.
