# RSNA Intracranial Hemorrhage Detection

## Entrypoints for the 5th-place solution

### Train models 
Follow the instructions in the following 3 repositories to train 9 models, generate predictions for the test set and the out-of-fold-train set 
* [1] Bac Nguyen’s source code
https://github.com/ngxbac/Kaggle-RSNA
* [2] Nguyen Tai Tri Duc 's pipeline to train InceptionV3 + Deepsupervision
https://github.com/triducnguyentang/RSNA
* [3] Anjum 's pipeline
https://github.com/Anjum48/rsna-ich


### Post-processing 
See the section at the end of this file.


### Stacking 
Details and code are presented at https://www.kaggle.com/mathormad/5th-place-solution-stacking-pipeline.

## Postprocessing

Required inputs:
* `df_dicom_metadata_train.csv` and `df_dicom_metadata_test.csv`. These are created using `dicom-metadata-to-csv-train-and-test.ipynb`. The stage 1 labels can be appended to the train data on release, and the test data can be replaced with the stage 2 metadata.
* `patients_stacking_splits.csv` which contains the 5 fold cross-validation scheme for the post-processsing model. This is created by `stacking-split.ipynb`. When the stage 1 labels are released, the stage 1 images can be appended to this file as a 6th fold.
* A CSV file containing the out-of-fold predictions from a model
* A CSV file containing the test predictions (i.e. a submission file)

Run `post-processing-v7-with-wo-meta.ipynb` with the following options
* META_NUMBER_IMAGES_IN_USE = True
* NUMBER_FOLDS = 6 # 6 for if we include the stage 1 set

