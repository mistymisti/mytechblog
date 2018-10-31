# mytechblog
# Large scale event processing system in Site Reliability
# Introduction
A highly available and highly reliable system is appreciated and patronized for a better customer experience and retention. Such a system is always backed by a superior monitoring model that that keeps downtimes at bay. Successful serve a high octane traffic that requires minimal time to recover from any site incident. Site Reliability is a field of study and practice that focuses intensively on reliability/availability/resiliency/security aspects of a system and ways to improve the said metrics.
# Preface
The current solution is a minimalistic model of a monitoring system with a decent intelligence to be proactive to site incidents and predictions. A user of this system will be able to monitor and predict anomalous site events that are about to happen and take proactive measures to bring the situation under control.

# Component Description

A light-weight web application using Angular and REST APIs serving the backend will retrieve and display data trending over a given period of time (from, to).

An aggregator job runs on a timely basis to update a data set which are in turn used by the REST APIs discussed above.

To achieve proactive analysis we employ an ML job to mine through the aggregator data to display whether the current feature input results in a failed condition or not. This will result give an idea on necessary actions to be taken if any for current anomalous situation.

Trained the model with a simple classifier training algorithm such as  Logistic Regression for an initial outlier detection with a binary output saying the output is 0 or 1 for a group of columns as input features.

Prevalent classifier algorithms such as KNN, LSTM can be employed to achieve better ROC and better predictions.

Aggregator jobs can be run on a daily/weekly/monthly roll ups to consolidate metric data grouped over a period time. We can have multiple ML models one for each roll up job that are trained for daily/weekly/monthly data and also for different traffic periods (like holiday season, peak season on holiday sale etc.,.)

LSTM Recurrent Neural network prediction is an ML technique where current prediction is based on historical data. So we might have to superimpose current day data to the one a week or a month ago to obtain a dataset for the model to get trained for real time predictions. Being one of the best prediction models when the site traffic does not vary on a large scale due to external factors such as holiday seasons, the chances of incident predictions are state of the art.

Coming to the APIs section, we have a straight forward Spring Boot application which takes a time range as input and gets the data for all perfmon metrics for the Angular’s dygraphs library.

Angular dygraph is a directive within Angular for easy integration and the full power of dygraphs library can be employed. Sample time series data for dygraphs follow below,

[["timestamp","value"],
    [new Date("2018-10-26 12:00:00"),1],
    [new Date("2018-10-26 12:01:00"),1],
    [new Date("2018-10-26 12:01:00"),0]];
