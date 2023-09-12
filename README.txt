Virtual measurement environments, University of Oulu

Juho Kurula, jkurula19@student.oulu.fi

•What has been done
This project basic idea was to create signal processing tool box (desktop application) for neuroimaging 
signals using Matlab App Designer. I created main app called SAappi.mlapp and 2 sub apps called AskMregComponent.mlapp
and AskEegComponent.mlapp. This app uses only given data which consist of magnetic resonance encephalography (MREG), 
electroencephalography (EEG), near infrared spectroscopy (NIRS), non-invasive blood pressure (NIBP) and anesthesia 
monitor signals (pleth, CO2). All the recordings are used to measure an aspect of brain function, often by exploring 
the relationship between activities in certain brain areas. This app also uses given signal filter called
Y_IdealFilter.m and given MREG components which are image .png files. Data selecting, signal filtering with different bands,
signal plotting and signal calculations have meen implemented in this project.

•How to use the program
!Firstly you need to put all the .mlapp files, function and all the data files and mreg components in the same folder and choose from
matlab application that folder for working directory before using this app! 
The program has been seperated in 3 different sections, left side being data handling and signal filtering, middle section
used for plotting the data however you like and right side for signal calculations and plotting aswell. The workflow goes
from left to right side firstly selecting the data you want to work for from pressing the button "Select data". 
Then you can filter that data first by selecting filter type with radio buttons, then choosing the frequencies, and lastly
pressing "Filter" button. You can also save the filtered data to .txt file from the button next to it.
When the data has been selected and it is showing in the "current data" editfield, you can also plot it from "plot for data1"
and choosing "original signal" and pressing "plot 1" button. When filtering is done, "filtered signal" can be applied
aswell. If you want to plot everything in different figures choose "plot for data 1", If you choose to plot for same figure,
plot first signal from "Plot 1" and then second signal from "Plot 2". Choosing "more" you can select from the files which
signal to plot.
In signal calculations, you choose "current data" or "filtered data" for Signal 1 and Signal 2 by pressing the import 1 
and import 2 buttons. The filename will be shown in the edit fields and also the component if the file has one.
It will also show if the file is filtered or not. By hovering the mouse over the buttons in signal calculations, tooltip
aka. help tips will be shown what the button does and what data it will calculate. "Correlation coefficient" and 
"Max cross correlation" both need signal 1 and signal 2 to be chosen to calculate. "coefficient of variance" and 
"Plot spectral entropy" and "plot power spectrum" will work from one signal which will be chosen from SIGNAL 1!!!

•more in detail what happens in different buttons/functions
Select data button - This will open ui where you can browse and choose the file you want. When you pick file, plot 1 button and import 1 
button are now enable. If you choose file mreg.txt there will pop up smaller window where it asks to choose component and press ok.
This was done using sub app and the main app fetch the data from the this sup app and uses it so there is data cycling
between aps. The component number will show in "component" edit field. The same goes for eeg.txt file but different sub app was made 
and it asks component between 1-32 rather than 1-70 in mreg.txt.


Filter button - Uses Y_IdealFilter function to filter the data with the inputs user gives.
 
Plot 1 button - plots the chosen signal in new figure with legends and labels
plot 2 button - plots the chosen signal in same figure where plot 1 plotted. This button can only be used when plot 1 is pressed.
!FIRST PRESS PLOT 1 BUTTON THEN PLOT 2!
If the plotted signal is mreg.txt file it will also show the spatial map.


Import for signal 1 - choose current or filtered data-->press import 1-->User sees what data is being used
Import for signal 2 - same but to signal 2
when importing data to signal 1 it will enable the three lowest buttons and when both signal 1 and signal 2 have values all buttons enabled


Correlation coefficient button - calculates the correlation coefficient value between 2 signals with corr2 function, shows it in editfield


Max cross correlation button - Calculates cross correlation between signals and shows maximum positive correlation and the time
differnece which gives the maximum correlation. Also checks if the imported signals are filtered or not, detrend used on those
which are not filtered which removes the mean of the signal. I did own function for this and specified implementation can be found from code.
Function name is calculateXCORR(3 inputs and 2 outputs)


Coefficient of variance button - calculates the cv of signal 1 and it takes only fullband signals, not filtered


plot spectral entropy button - plots spectral entropy signal 1 of eeg,mreg (with the right component) or nirs. pentropy function was used
and all the signals which were not filtered were detrended aka. mean removed.


plot power spectrum button - plots the power spectrum of signal 1 using my function calcpowerspectrum which takes 2 inputs and gives
2 outputs. Firstly taking fft of the signal then calculates every element to the power of two and divides this with length of dataset 
and sample frequency which is 10. Lastly takes the 10*log10 of the values. frequency range was done using lincpace from 0 to data length
with the steps of 10.


•How you have tested your program

All of the testing was just blackbox testing continiously through the implementation lifecycle. I tried to test all possible scenarios
after every little implementation. After the first full implementation was done, I tested it myself and I asked for a friend to try it
out, give opinion about the front end and the usability.
 
