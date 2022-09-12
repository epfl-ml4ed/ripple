# Ripple: Concept-Based Interpretation for Raw Time Series Models in Education

Attention: This code is subject to restructuring and cleaning upon EAAI acceptance.

This is the official repository for the submitted EAAI-23 paper titled "Ripple: Concept-Based Interpretation for Raw Time Series Models in Education"

## Scripts
Jupyter notebooks and python scripts needed to reproduce the paper's results are provided in `scripts` folder.
### data_splits.ipynb
Splits the dataset for each of the courses found in `ripple_data\prep_data` folder into train, validation, and test with respect to the defined percentages (80-10-10 as default).
It then stores the arguments of the students corresponding to each of the splits and stores them in `ripple_data\split_args`
### dataset_convert.ipynb
This script is responsible for transforming the course log datasets as provided by MOOC platforms into arrays of interaction×event_types, actual time_stamps, actual non-zero length of each time series and their corresponding pass/fail labels.
