# GW-TDA-Detection

**Used topology data analysis to determine if a simulated reading of a detector have a gravitational wave**

The code was based on this paper: https://arxiv.org/abs/1910.08245

The pipeline applied to the data is the following:

## Topology Pipeline

### Takens Embedding
- Reconstructs a phase space from time series data
- Parameters: 'time_delay', 'dimension' and 'stride'

### CollectionTransformer
- Applies PCA fro dimesnionality reduction
- 'n_jobs=1' allows parallel processing

### VietoriesRipsPeristence:
- Computes persistent homology
- 'homology_dimension=[0,1] means it computes H_0 and H_1

### Scaler:
- Scales the data for uniformity

### PersistenceEntropy: 
- Computes entropy of persistence diagrams
- 'normalize=True' and 'nan_fill_value=-10' handle normalization and NaN values

Once processed the data, we used logistic regression and a CNN to classify.

## To do's: 
- Tune and correct the CNN
- Apply the pipeline with real data
