# Ripple: Concept-Based Interpretation for Raw Time Series Models in Education

This is the official repository for the paper titled "Ripple: Concept-Based Interpretation for Raw Time Series Models in Education", written by [Mohammad Asadi](http://github.com/MohamadAsadi78), [Vinitra Swamy](http://github.com/vinitra), Jibril Frej, Julien Vignoud, Mirko Marras, Tanja Kaser and featured at AAAI 23.

Jupyter notebooks corresponding to each of the research questions mentioned in the paper can be found in `scripts` folder 

## Scripts
Jupyter notebooks and python scripts needed to reproduce the paper's results are provided in `scripts\` folder. Short descriptions regarding the research question and methodology are also presented at the beginning of each of the notebooks.
#### data_splits.ipynb
Splits the dataset for each of the courses found in `data\prep_data` folder into train, validation, and test with respect to the defined percentages (80-10-10 as default).
It then stores the arguments of the students corresponding to each of the splits and stores them in `data\split_args`
#### dataset_convert.ipynb
This script is responsible for transforming the course log datasets as provided by MOOC platforms into arrays of interaction×event_types, actual time_stamps, actual non-zero length of each time series and their corresponding pass/fail labels.
#### run_raindrop.ipynb
RQ1. Using the data splits and datasets resulted from the last two scripts, `run_raindrop.ipynb` alters `Raindrop` model w.r.t. each course dataset and trains the model on it.
It then evaluates the the trained model's performance again on validation set and test set and saves them as `.csv` files for each course.
This file uses two versions of Raindrop namely `Raindrop_v2` and `Raindrop_v3` where the last one is a slightly adjusted version of `Raindrop_v2` from the original Raindrop repository to change the number of layers for the final `MLP` classification layer for grid search.
#### run_baselines.ipynb
Trains, evaluates, and stores validation and test results for all the `handcrafted-feature` models. Implementation adopted from `Meta-Transfer Learning` paper.
#### run_baselines_seft_trnsfrmr.ipynb
Trains, evaluates, and stores validation and test results for SEFT and Transformer as implemented by Raindrop's repository. It also adjusts SEFT and Transformer for altering the number of layers for TransformerEncoder and last MLP classification layer essential for performing the grid search.

#### tcav_rq2.ipynb
RQ2 & RQ3. Implements TCAV pipeline on Raindrop model trained on a specific course. Here all the concepts mentioned in the paper are defined and the groups of top and bottom student w.r.t. each concept are extracted. These students are then used to specify the concepts and feed them into TCAV pipeline for time series. This script also generates the results showen in paper given the same dataset. This script also generates TCAV scores and the corresponding plots for the 4 confusion matrix scenarios.

#### tcav_rq3.ipynb
RQ3. This script is responsible for normalizing the feature scores comprising the concepts and then finding the top and bottom students regarding the overall performance across all the concepts. It then generates the TCAV score plots for the model's prediction on these specific students.
