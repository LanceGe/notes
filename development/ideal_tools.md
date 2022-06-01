# Ideal Tools for Time Series Predictive Modeling

## Dataset

Ideally the dataset

* should be able to store tick data, i.e., unaligned collections of unevenly-spaced time series, and support resampling when queried;
* is fast;
* can be version-controlled.

It would be ideal to have a centralized database. Then any dataset used for a specific project can be defined by a query script and version-controlled. Database options include:

* `InfluxDB`. `2.x` is good, but I would like to see `IOx` mature. **`Flux `is just not as human-readable as `SQL`.** Also, it requires enterprise subscription to use the distributed version of the system. 
* `QuestDB` seems to have a good support for `SQL`. However, up til now **it can only run on a single node** and I'm a little bit skeptical about its reliability since it's not as widely-used as `InfluxDB`.

If a centralized database is not avaible, then using `DVC` with a reliable storage service is also not a bad idea. Storing `parquet` files `HDFS` would work.

## Exploratory Data Analysis

Ideally the EDA process

* automatically generates a report to read with fishy patterns pointed out;

* can check consistency between sliding-window cross-validation splits;
* makes it possible to perform hypothesis-verification iterations.

So far no library satisfies all the above properties. `dataprep` provides a bunch of useful functions and can help to build one.

## Feature Engineering

Ideally the feature engineering process

* is extensible, i.e., one can write custom features;
* can be tuned w.r.t. parameters like window size; 
* is fast (parallelization / GPU);
* can be version-controlled. 

So far my `FEDSL` has demonstrated potential to satisfy all the above properties. However it's still

* relying on a crappy `pyparsing`-based parser instead of a serious CFG parser;
* not well tested.

Also, it would be great if I can write a VSCode extension to support auto-complete of  `FEDSL` files.