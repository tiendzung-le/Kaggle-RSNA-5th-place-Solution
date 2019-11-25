# Postprocessing

Required inputs:
* `df_dicom_metadata_train.csv` and `df_dicom_metadata_test.csv`. These are created using `dicom-metadata-to-csv-train-and-test.ipynb`. The stage 1 labels can be appended to the train data on release, and the test data can be replaced with the stage 2 metadata.
* `patients_stacking_splits.csv` which contains the 5 fold cross-validation scheme for the post-processsing model. This is created by `stacking-split.ipynb`. When the stage 1 labels are released, the stage 1 images can be appended to this file as a 6th fold.
* A CSV file containing the out-of-fold predictions from a model
* A CSV file containing the test predictions (i.e. a submission file)

To postprocess the resuls run `post-processing-v7-with-wo-meta.ipynb`
