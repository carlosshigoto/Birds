
# Set your working directory
setwd("C:/Users/Philippe/Documents/Grad school/Classes/CMPUT 551_ Machine Learning/Project")

# Packages needed for sound analysis
library(tuneR)
library(stats)
library(seewave)
library(sound)

# Input a Wave file as a test for the function
wave <- readWave("BRCR/HL-3-15-1_20140619_140000_000_06_BRCR.wav")

# Tentative function for collecting features out of wave data:

features <- function(wave){
  x<-rmnoise(wave,output="Wave")
  y<-acoustat(x,plot=F,aggregate = sum)
  df <- data.frame("ZCR" = zcr(x, wl=NULL),
                   "ACI"= ACI(x),
                   specprop(spec(x,fftw=TRUE,plot=F)),
                   "time.P1" = y$time.P1,
                   "time.M" = y$time.M,
                   "time.P2" = y$time.P2,
                   "time.IPR"	= y$time.IPR,
                   "freq.P1" = y$freq.P1,	
                   "freq.M"	= y$freq.M,
                   "freq.P2" = y$freq.P2,	
                   "freq.IPR" = y$freq.IPR)
  return(df)  
}

# As of now, we have the following features:
#
# 1. Zero Crossing rate (ZCR)
#
# 2. Acoustic Complexity Index (ACI) 
#
# 3-16. Spectral properties (specrop)
#     (The spectrum is converted in a probability mass function (PMF))
#     From this PMF, we compute: 
#
#     mean: mean frequency 
#     sd: standard deviation of the mean
#     sem: standard error of the mean
#     median: median frequency 
#     mode: mode frequency, i.e. the dominant frequency
#     Q25: first quartile
#     Q75: third quartile
#     IQR: interquartile range
#     cent: centroid
#     skewness: skewness, a measure of asymmetry
#     kurtosis: kurtosis, a measure of peakedness
#     sfm: spectral flatness measure
#     sh: spectral entropy
#     prec: frequency precision of the spectrum
#
# 17-24: Acoustat: statistics based on Short Time Fourier Transform time and frequency contours.
#       
#     time.P1: the time initial percentile
#     time.M: the time median
#     time.P2: the time terminal percentile
#     time.IPR: the time interpercentile range
#     freq.P1: the frequency initial percentile
#     freq.M: the frequency median
#     freq.P2: the frequency terminal percentile
#     freq.IPR: the frequency interpercentile range
#


# STILL TO DO
# Add label
# Add the features you guys think would be usefull.

bird.dataframe <- features(wave)

